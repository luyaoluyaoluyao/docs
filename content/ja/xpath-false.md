---
title: "XPath False"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

## 1つの概要

関数 `false()` は、ブール値 `false` を返します。

To use the values `true` or `false` in XPath queries, it is necessary to either use the `true()` and `false()` functions or to enclose the values in quotation marks.

## 2つの例

このクエリは、ゴールドの顧客として分類されていないすべての顧客を返します:

```java
//Sales.Customer[IsGoldCustomer = false()]
```
