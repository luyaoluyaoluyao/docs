---
title: "XPath 月から開始日時"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

`month-from-dateTime()` 関数は、 **Date and time** 属性から月の値を抽出し、値と比較するために使用できます。

## 2つの例

このクエリは、月の値 `DateAttribute` が 12 (December) のすべてのログを返します。 例: "2011-12-30":

```java
//Logging.Log[month-from-dateTime(DateAttribute) = 12]
```
