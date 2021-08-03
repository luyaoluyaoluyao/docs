---
title: "解析 & 日付関数呼び出しの書式設定"
parent: "表現"
description: "指定されたパターンを使用して文字列からdatetimeを解析したり、Mendixのdatetimeから文字列を生成したりする関数を説明します。"
---

指定したパターンを使用して文字列からdatetimeを解析したり、datetimeから文字列を生成したりする関数です。

すべてのパターンの可能性については [http://docs.oracle.com/javase/7/docs/api/java/SimpleDateFormat.html](http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html) を参照してください。

## parseDateTime[UTC]

文字列を取得して解析しようとします。 失敗し、デフォルト値が指定された場合、デフォルト値を返します。 そうでなければ、エラーが発生します。 関数 `parseDateTime` はユーザのタイムゾーンを使用し、 `parseDateTimeUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   日付 タイプ: String
*   形式 タイプ: String
*   a default value (**optional**) Type: DateTime

### 出力

解析された日付、または日付が解析できなかった場合のデフォルト値。 タイプ: DateTime

```java
parseDateTime('2015-05-21', 'yyyy-MM-dd')
```

を返します。

```java
日時 2015年5月21日\. 時間は夜の12時ですので、指定されていません。
```

```java
parseDateTime('noDateTime', 'dd-MM-yyyy', dateTime(2007))
```

を返します。

```java
'Mon Jan 01 00:00:00 CET 2007'
```

## formatDateTime[UTC]

datetimeを、format パラメーターに従って書式設定された文字列に変換します。 format パラメータがなければ、標準フォーマットが使用されます。 関数 formatDateTime `` はユーザカレンダーを使用し、 `formatDateTimeUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   日付 タイプ: DateTime
*   a format (**optional**) Type: String

### 出力

日時の書式付き表現。 タイプ: 文字列

```java
formatDateTime($object/Date1,'EEE, d MMM yyyyy HHH:mm:ss Z')
```

戻り値:

```java
'Sun, 8 Jun 2008 10:12:01 +0200'
```

'1987-12-31T23:59:00' を取得するには、2 つの formatDateTime[UTC] 関数を連結する必要があります。

```java
formatDateTime($object/Date1, 'yyyy-MM-dd') + 'T' + formatDateTime($object/Date1, 'HH:mm:ss')
```

## formatTime[UTC]

datetimeの時刻部分を標準形式で文字列に変換します。 formatTime `formatTime` はユーザーカレンダーを使用し、 `formatTimeUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   日付 タイプ: DateTime

### 出力

datetime値の時刻部分の書式付き表示。 タイプ: 文字列

```java
formatTime(dateTime(1974, 7, 2, 9, 50, 10))
```

戻り値:

```java
「午前9時50分」
```

## formatDate[UTC]

datetimeの日付部分を標準形式で文字列に変換します。 `formatDate` はユーザーのカレンダーを使用し、 `formatDateUTC` は UTC カレンダーを使用します。

### 入力パラメータ

*   日付 タイプ: DateTime

### 出力

datetime値の日付部分の書式付き表示。 タイプ: 文字列

```java
formatDate(dateTime) (1974, 7, 2, 9, 50, 10))
```

戻り値:

```java
'7/2/74'
```
