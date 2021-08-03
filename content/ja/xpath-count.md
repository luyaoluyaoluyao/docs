---
title: "XPath カウント"
parent: "xpath-query-functions"
---

## 1つの概要

`count()` 関数は、囲まれたクエリで取得したすべてのオブジェクトをカウントし、値を整数として返します。

## 2つの例

このクエリは、すべての注文数を返します:

```java
count(//Sales.Order)
```

このクエリは、「Jansen」という名前の顧客によって発注されたすべての注文の数を返します。

```java
count(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen'])
```
