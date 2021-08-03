---
title: "XPath 分-from-dateTime"
parent: "xpath-constraint-functions"
---

## 1つの概要

`minutes from-dateTime()` 関数は、DateTime 属性から分量を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` の分数が30（例："2011-12-30 08:30:00"）のすべてのログを返します。

```java
//Logging.Log[minutes-from-dateTime(DateAttribute) = 30]
```
