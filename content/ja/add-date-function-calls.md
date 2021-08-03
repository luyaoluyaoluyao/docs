---
title: "日付関数の呼び出しを追加"
parent: "表現"
---


日付に時間単位を追加します。 すべての例では、最初の入力は新しい dateTime のいずれかになります (すべての例で示されています)。 DateTime型の変数、またはDateTime型のドメインエンティティの属性。

## addMilliseconds

日付にミリ秒数を追加します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加するミリ秒数 Type: Integer

### 出力

DateTime 型の最初の日付とx ミリ秒の結果です。

{{% alert type="info" %}}

```java
addMilliseconds(dateTime(2007, 1, 1, 1), 1400)

```

結果は次の日時に対応します

```java
"Mon Jan 01 01:01:02:400 CET 2007"

```

{{% /alert %}}

## 追加秒

日付に秒数を追加します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加する秒数 Type: Integer

### 出力

DateTime 型の初期日付プラスx秒に対応する結果。

{{% alert type="info" %}}

```java
addSeconds(dateTime(2007年、1、1、1、1、2)

```

結果は次の日時に対応します

```java
"Mon Jan 01 01:01:03 CET 2007"

```

{{% /alert %}}

## addMinutes

日付に分数を追加します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加される分量 タイプ: 整数

### 出力

DateTime 型の最初の日付に x 分を加えた結果です。

{{% alert type="info" %}}

```java
addMinutes(dateTime(2007年、1、1、1、1、1、3)

```

結果は次の日時に対応します

```java
"Mon Jan 01 01:04:01 CET 2007"

```

{{% /alert %}}

## addHours

日付に時間を追加します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加する時間の量 タイプ: Integer

### 出力

日付の最初の日付とx時間を足した日付の型の結果。

{{% alert type="info" %}}

```java
addHours(dateTime(2007年, 1, 1, 1), 25)

```

結果は次の日時に対応します

```java
"Mon Jan 02 02:01:01 CET 2007"

```

{{% /alert %}}

## addDays[UTC]

日付に日付を追加します。 `addDays` はサーバーのカレンダーを使用し、 `addDaysUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加する日数 タイプ: 整数

### 出力

日付の最初の日付とx日数に対応する型の結果。

{{% alert type="info" %}}

```java
addDays(dateTime(2007年、1、1、1、1、3)

```

結果は次の日時に対応します

```java
"Mon Jan 04 01:01:01 CET 2007"

```

{{% /alert %}}

## addWeeks[UTC]

日付に週数を追加します。 `addWeeks` はサーバーのカレンダーを使用し、 `addWewsUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加する週の量 タイプ: Integer

### 出力

最初の日付とx週間に対応するDateTime型の結果。

{{% alert type="info" %}}

```java
addWeeks(dateTime(2007年、1、1、1、1、2)

```

結果は次の日時に対応します

```java
"Mon Jan 15 01:01:01 CET 2007"

```

{{% /alert %}}

## addMonths[UTC]

日付に月数を追加します。 `addMonths` はサーバーのカレンダーを使用し、 `addMonthsUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加される月数 タイプ: 整数

### 出力

日付の最初の日付とxヶ月に対応する型の結果。

{{% alert type="info" %}}

```java
addMonts(dateTime(2007年、1、1、1、1、13)

```

結果は次の日時に対応します

```java
"Mon Feb 01 01:01:01 CET 2008"

```

{{% /alert %}}

## addYears[UTC]

日付に年数を追加します。 `addYears` はサーバーのカレンダーを使用し、 `addYearsUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   初期日付 タイプ: DateTime
*   追加する年数 種類: Integer

### 出力

日付の最初の日付とx年数に対応する型の結果。

{{% alert type="info" %}}

```java
addYears(dateTime(2007, 1, 1, 1, 1, 1), 11)

```

結果は次の日時に対応します

```java
"Mon Jan 01 01:01:01 CET 2018"

```

{{% /alert %}}{{% alert type="warning" %}}

異なる日付関数呼び出しにロング値を渡すこともできます。

```java
addSeconds(dateTime(1970, 1, 0, 0, 0), (long)(2147483647 + 100))
```

結果は次の日時に対応します

```java
"Tue Jan 19 04:15:47 CET 2038"
```

{{% /alert %}}
