---
title: "XPath month-from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`month-from-dateTime()` 関数は、DateTime 属性から月数を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の月数が 12 になっている(例えば、"2011-12-30")すべてのログを返します。

```java
//Logging.Log[month-from-dateTime(DateAttribute) = 12]
```
