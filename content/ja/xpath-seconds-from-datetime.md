---
title: "XPath 秒 from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`seconds-from-dateTime()` 関数は、 **Date and time** 属性の秒部分を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の秒部分が 30 であるすべてのログを返します(例: "2011-12-30 08:08:30" )。

```java
//Logging.Log[seconds-from-dateTime(DateAttribute) = 30]
```
