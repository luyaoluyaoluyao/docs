---
title: "XPath キーワード & システム変数"
parent: "xpath-constraints"
tags:
  - "studio pro"
  - "BeginOfCurrent"
---

## 1つの概要

XPath では、いくつかのキーワードとシステム変数を比較として呼び出すことができます。

## 2つのキーワード

これらのキーワードのいずれかを使用して、属性に値(任意の値)があるかどうかを確認することができます。

* `NULL`
* `空`

### 2.1 例

このクエリは、システムに不明なすべての顧客を返します。

```java
//Sales.Customer[Name = NULL]
```

これらのキーワードは属性と組み合わせてのみ使用できます。 この方法では、関連性の存在を確認することはできません。 関連を制約する方法の詳細については、 [XPath 制約関数](xpath-constraint-functions) を参照してください。

## 3つのシステム変数

システム変数は、システムまたは日付関連の値を取得するために使用できます。 利用可能なトークンについては、以下で説明します。

### 3.1 オブジェクト関連

| トークン                | 説明                            |
| ------------------- | ----------------------------- |
| `[%CurrentUser%]`   | 現在ログインしているユーザーのGUID。          |
| `[%CurrentObject%]` | アクティブなオブジェクトの GUID (コンテキスト内)。 |

### 3.2 ユーザロール

これらはアプリケーションの各ユーザーロールに対して作成されます。 以下に例を示します:

| トークン                         | 説明          |
| ---------------------------- | ----------- |
| `[%UserRole_Administrator%]` | 管理者ユーザーのロール |

次に、そのユーザーロールを取得する例を示します。

![](attachments/xpath/user-role.png)

### 3.3 時間関連

以下のトークンを使用して、日付と時刻の値を取得できます。

| トークン                          | 説明                    |
| ----------------------------- | --------------------- |
| `[%CurrentDateTime%]`         | 現在の日付と時刻              |
| `[%BeginOfCurrentMinute%]`    | 現在の分の開始時の日付と時刻。       |
| `[%BeginOfCurrentMinuteUTC%]` | UTCの現在の分の始めの日付と時刻。    |
| `[%EndOfCurrentMinute%]`      | 現在の分数の終わりの日付と時刻。      |
| `[%EndOfCurrentMinuteUTC%]`   | UTCの現在の分の終わりの日付と時刻。   |
| `[%BeginOfCurrentHour%]`      | 現在の時間の最初の日付と時刻。       |
| `[%BeginOfCurrentHourUTC%]`   | UTCの現在の時間の始めの日付と時刻。   |
| `[%EndOfCurrentHour%]`        | 現在の時間の終わりの日付と時刻       |
| `[%EndOfCurrentHourUTC%]`     | UTCの現在の1時間の終わりの日付と時刻。 |
| `[%BeginOfCurrentDay%]`       | 今日の初めの日付と時刻           |
| `[%BeginOfCurrentDayUTC%]`    | UTCの現在の日の初めの日付と時刻。    |
| `[%EndOfCurrentDay%]`         | 今日の終わりの日付と時刻          |
| `[%EndOfCurrentDayUTC%]`      | UTCの現在の日の終わりの日付と時刻。   |
| `[%BeginOfCurrentWeek%]`      | 現在の週の初めの日付と時刻         |
| `[%BeginOfCurrentWeekUTC%]`   | UTCの現在の週の初めの日付と時刻。    |
| `[%EndOfCurrentWeek%]`        | 現在の週の終わりの日付と時刻        |
| `[%EndOfCurrentWeekUTC%]`     | UTCの現在の週の終わりの日付と時刻。   |
| `[%BeginOfCurrentMonth%]`     | 現在の月の初めの日付と時刻         |
| `[%BeginOfCurrentMonthUTC%]`  | UTCの現在の月の初めの日付と時刻。    |
| `[%EndOfCurrentMonth%]`       | 現在の月の終わりの日付と時刻        |
| `[%EndOfCurrentMonthUTC%]`    | UTCの現在の月末の日付と時刻。      |
| `[%BeginOfCurrentYear%]`      | 現在の年の初めの日時。           |
| `[%BeginOfCurrentYearUTC%]`   | UTCの今年の初めの日付と時刻。      |
| `[%EndOfCurrentYear%]`        | 現在の年末の日付と時刻           |
| `[%EndOfCurrentYearUTC%]`     | UTCの今年の終わりの日付と時刻。     |

以下のトークンは、日付と時刻のトークンの値から期間を追加または減算するために使用できます。

| トークン               | 説明           |
| ------------------ | ------------ |
| `[%DayLength%]`    | 1日(24時間)の長さ。 |
| `[%HourLength%]`   | １時間の長さ。      |
| `[%MinuteLength%]` | 1分間の長さ。      |
| `[%SecondLength%]` | 一秒の長さ。       |
| `[%WeekLength%]`   | 1週間（7日）の長さ。  |
| `[%MonthLength%]`  | 1ヶ月の長さ。      |
| `[%YearLength%]`   | 一年の長さ。       |

{{% alert type="info" %}}
これらの変数は文字列値として使用し、2つの引用符の間に配置する必要があります。 時間関連トークンと期間関連トークンを組み合わせたトークンは、1つの文字列内に配置する必要があります。 例 3 を参照してください。
{{% /alert %}}

#### 3.3.1 例

このクエリは、今週の初めから登録されている顧客のみを返します:

```java
//Sales.Customer[DateRegistered >= '[%BeginOfCurrentWeek%]']
```

このクエリは、今週登録した顧客のみを返します:

```java
//Sales.Customer[DateRegistered >= '[%BeginOfCurrentWeek%]' and DateRegistered < '[%EndOfCurrentWeek%]']
```

このクエリは過去3年間に登録した顧客のみを返します:

```java
//Sales.Customer[DateRegistered > '[%BeginOfCurrentDay%] - 3 * [%YearLength%]']
```

このクエリは、ロール「Administrator」を持つユーザーを返します。

```java
//System.User[System.UserRoles = '[%UserRole_Administrator%]']
```
{{% alert type="info" %}}
システム変数は(引用符の間で)文字列として記述されるため、式をグループ化するのに括弧を使用することはできません。
{{% /alert %}}
