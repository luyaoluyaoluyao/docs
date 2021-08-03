---
title: "XPath の長さ"
parent: "xpath-constraint-functions"
---

## 1つの概要

`length()` 関数は、文字列属性または値の長さを返します。

## 2つの例

このクエリは、5文字以上の `FirstName` を持つすべての顧客を返します。

```java
//Sales.Customer[length(FirstName) >= 5]
```
