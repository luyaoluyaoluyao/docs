---
title: "XPath hours-from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`hours-from-dateTime()` 関数は、DateTime 属性から時間の量を抽出し、値と比較するために使用します。

## 2つの例

このクエリは、 `DateAttribute` の時間数が8であるすべてのログを返します(例えば、"2011-12-30 08:00:00")。

```java
//Logging.Log[hours-from-dateTime(DateAttribute) = 8]
```
