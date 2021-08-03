---
title: "XPath Minutes-from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`minutes from-dateTime()` 関数は、 **Date and time** 属性から分数の値を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の分部分が 30 になっているすべてのログを返します(例: "2011-12-30 08:30:00" )。

```java
//Logging.Log[minutes-from-dateTime(DateAttribute) = 30]
```
