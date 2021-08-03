---
title: "XPath年from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`year-from-dateTime()` 関数は、 `DateTime` 属性から年数を抽出し、値と比較するために使用します。

## 2つの例

このクエリは、 `DateAttribute` の年数が "2011" であるすべてのログを返します(例: "2011-12-30")。

```java
//Logging.Log[year-from-dateTime(DateAttribute) = 2011]
```
