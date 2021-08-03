---
title: "XPath 日付開始日"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`day-from-dateTime()` 関数は、 **Date and time** 属性から月の値の日を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` が月の 30 日になるすべてのログを返します(例えば、"2011-12-30")。

```java
//Logging.Log[day-from-dateTime(DateAttribute) = 30]
```
