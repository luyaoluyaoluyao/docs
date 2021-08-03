---
title: "XPath Quarter-from-DateTime"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`quaret-from-dateTime()` 関数は、 **Date and time** 属性に対応する四半期を抽出し、値と比較するために使用することができます。

## 2つの例

このクエリは、 `DateAttribute` が四半期にあるすべてのログを返します(たとえば、"2011-12-30")。

```java
//Logging.Log[quaret-from-dateTime(DateAttribute) = 4]
```
