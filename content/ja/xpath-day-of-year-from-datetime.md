---
title: "XPath 日 from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`year-of-dateTime()` 関数は、DateTime 属性から日数(その年)を抽出し、値と比較するために使用することができます。 値は 1 から 366 の範囲です(うるう年のため)。

## 2つの例

このクエリは、 `DateAttribute` の日数(その年)が30(たとえば、"2011-01-30")であるすべてのログを返します。

```java
//Logging.Log[year-of-dateTime(DateAttribute) = 30]
```
