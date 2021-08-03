---
title: "XPath week-from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`week-from-dateTime()` 関数は、DateTime 属性から週の量を抽出し、値と比較するために使用できます。 値は 1 から 53 までの範囲です(どの週に属する値はデータベースの実装に依存します)。

## 2つの例

このクエリは、 `DateAttribute` の週数が "2" (例: "2011-01-13" )のすべてのログを返します。


```java
//Logging.Log[week-from-dateTime(DateAttribute) = 2]
```
