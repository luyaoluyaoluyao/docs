---
title: "XPath 平日から日付時間"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`weekday-from-dateTime()` 関数は、 **Date and time** 属性から、曜日の日を数値として抽出し、値と比較するために使用することができます。 値は 1 から 7 の範囲です。 (1 = 日曜日、7 = 土曜日)。

## 2つの例

このクエリは、 `DateAttribute` の週の曜日が 6 (金曜日) のすべてのログを返します。

```java
//Logging.Log[weekday-from-dateTime(DateAttribute) = 6]
```
