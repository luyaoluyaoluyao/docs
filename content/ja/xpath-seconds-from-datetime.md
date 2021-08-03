---
title: "XPath from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`seconds-from-dateTime()` 関数は、DateTime 属性から秒数を抽出し、値と比較するために使用します。

## 2つの例

このクエリは、 `DateAttribute` の秒数が 30 のすべてのログを返します(例: "2011-12-30 08:08:30" )。

```java
//Logging.Log[seconds-from-dateTime(DateAttribute) = 30]
```
