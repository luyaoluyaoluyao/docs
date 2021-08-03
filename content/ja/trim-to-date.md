---
title: "日付にトリムする"
parent: "表現"
---

## 1つの紹介

これらは、日付を異なる時間単位に切り替える機能です。

## 2 trimToSeconds

日付を秒単位で切り落とし、すべてのミリ秒をゼロに切り落とします。

### 2.1 入力パラメータ

* トリミングされる日付
* タイプ: DateTime

### 2.2 出力

* 同じ日付は、秒単位で切り下げられます
* タイプ: DateTime

### 2.3 例

'08-06-2008 10:12:51.387' を表す変数 `$myDate` を仮定します。

```java
trimToSeconds($myDate)
```

戻り値:

```java
'サン08 10:12:51CEST2008'
```

## 3 trimToMinutes

日付を分にトリミングし、すべての(ミリ)秒をゼロに丸めます。

### 3.1 入力パラメータ

* トリミングされる日付
* タイプ: DateTime

### 3.2 出力

* 同じ日付を分単位で切り下げました。
* タイプ: DateTime

### 3.3 例

'08-06-2008 10:12:51'を表す変数 `$myDate` を仮定します:

```java
trimToMinutes($myDate)
```

戻り値:

```java
'Sun 08 10:12:00 CEST 2008'
```

## 4 trimToHours[UTC]

日付を時間にトリムし、すべての分をゼロに丸めます。

`trimToHours` はユーザのタイムゾーンを使用し、 `trimToHoursUTC` は UTC タイムゾーンを使用します。

### 4.1 入力パラメータ

* トリミングされる日付
* タイプ: DateTime

### 4.2 出力

* 同じ日付は、時間に切り下げられます。
* タイプ: DateTime

### 4.3 例

'08-06-2008 10:12:51'を表す変数 `$myDate` を仮定します:

```java
trimToHours($myDate)
```

戻り値:

```java
'Sun June 08 10:00:00 CEST 2008'
```

## 5 trimToDays[UTC]

日付を日付にトリムし、すべての時間をゼロに丸めます。

`trimToDays` はユーザのタイムゾーンを使用し、 `trimToDaysUTC` は UTC タイムゾーンを使用します。

### 5.1 入力パラメータ

* トリミングされる日付
* タイプ: DateTime

### 5.2 出力

* 同じ日付、日付のみ切り下げられます
* タイプ: DateTime

### 5.3 例

'08-06-2008 10:12:51'を表す変数 `$myDate` を仮定します:

```java
trimToDays($myDate)
```

戻り値:

```java
'Sun June 08 00:00:00 CEST 2008'
```

## 6 trimToMonths[UTC]

日付を月にトリムし、すべての日をゼロに丸めます。

`trimToMonths` はユーザーのタイムゾーンを使用し、 `trimToMonthsUTC` は UTC タイムゾーンを使用します。

### 6.1 入力パラメータ

*   調整されるべき日付
*   タイプ: DateTime

### 6.2 出力

* 同じ日付、月単位でのみ切り下げられます
* タイプ: DateTime

### 6.3 例

'08-06-2008 10:12:51'を表す変数 `$myDate` を仮定します:

```java
trimToMonths($myDate)
```

戻り値:

```java
'Sun June 01 00:00:00 CEST 2008'
```

## 7 trimtoYears[UTC]

日付を年にトリムし、すべての月と日をゼロに丸めます。

`trimToYears` はユーザのタイムゾーンを使用し、 `trimToYearsUTC` は UTC タイムゾーンを使用します。

### 7.1 入力パラメータ

* トリミングされる日付
* タイプ: DateTime

### 7.2 出力

* 同じ日付、年に切り下げられたのみ
* タイプ: DateTime

### 7.3 例

'08-06-2008 10:12:51'を表す変数 `$myDate` を仮定します:

```java
trimToYears($myDate)
```

戻り値:

```java
'Tue 1月01 00:00:00 CEST 2008'
```
