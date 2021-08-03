---
title: "XPath 平日-from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`weekday-from-dateTime()` 関数は、DateTime 属性から日数を抽出し、値と比較するために使用することができます。 値は 1 から 7 の範囲です。 (1 = 日曜日、7 = 土曜日)。

## 2つの例

このクエリは、 `DateAttribute` の平日の量が 6 になっているすべてのログを返します(例: "Friday 2011-12-30" )。

```java
//Logging.Log[day-from-dateTime(DateAttribute) = 6]
```
