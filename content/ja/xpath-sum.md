---
title: "XPathSum"
parent: "xpath-query-functions"
tags:
  - "studio pro"
---

## 1つの概要

`sum()` 関数は引数の合計を返します。

関数は引数として XPath クエリを必要とします。

関数は、集計するクエリ内の列を指定する必要があります。

クエリは数値型の属性を指定する必要があります。

## 2つの例

このクエリは、すべての注文の合計価格の合計を返します:

```java
sum(//Sales.Order/TotalPrice)
```

このクエリは、「Jansen」という名前の顧客によって発注されたすべての注文の合計価格の合計を返します。

```java
sum(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen']/TotalPrice)
```
