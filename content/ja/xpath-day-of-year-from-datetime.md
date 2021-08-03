---
title: "XPath の日付開始日"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`year-of-dateTime()` 関数は、 **Date and time** 属性から年の日を抽出し、値と比較するために使用することができます。 値は 1 (1 月 1日) から 366 (うるう年のため) の範囲です。

## 2つの例

このクエリは、 `DateAttribute` の年の日付が 30 であるすべてのログを返します(例: "2011-01-30" と "2012-01-30" )。

```java
//Logging.Log[year-of-dateTime(DateAttribute) = 30]
```
