---
title: "XPath 日付開始日"
parent: "xpath-constraint-functions"
---

## 1つの概要

`day-from-dateTime()` 関数は、DateTime 属性から日数を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の日数が30（例："2011-12-30"）のすべてのログを返します。

```java
//Logging.Log[day-from-dateTime(DateAttribute) = 30]
```
