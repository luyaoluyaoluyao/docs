---
title: "XPath true"
parent: "xpath-constraint-functions"
---

## 1つの概要

関数 `true()` は、ブール値 `true` を返します。

To use the values `true` or `false` in XPath queries, it is necessary to either call `true()` or `false()` functions, or to enclose the values in quotation marks.

## 2つの例

このクエリは、「ゴールド顧客」として分類されるすべての顧客を返します：

```java
//Sales.Customer[IsGoldCustomer = true()]
```

