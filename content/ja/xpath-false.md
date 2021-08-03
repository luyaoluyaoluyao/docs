---
title: "XPath false"
parent: "xpath-constraint-functions"
---

## 1つの概要

関数 `false()` はブール値 `false` を返します。

To use the values `true` or `false` in XPath queries, it is necessary to either use the `true()` and `false()` functions or to enclose the values in quotation marks.

## 2つの例

このクエリは、ゴールドの顧客として分類されていないすべての顧客を返します:

```java
//Sales.Customer[IsGoldCustomer = false()]
```
