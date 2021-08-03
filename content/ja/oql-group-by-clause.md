---
title: "条項によるOQL グループ"
parent: "oql"
tags:
  - "studio pro"
---

## 1つの説明

`GROUP BY` 節は、返されたすべての行を単一の行に凝縮し、この節で定義された式の同じ値を共有します。 この節の式はクエリの `SELECT` 節に存在する必要があります。 `GROUP BY` 節に存在しない `SELECT` 節内のすべての式は集計または集計関数でなければなりません。

## 2つの構文

構文は以下の通りです:

```sql
GROUP BY
    expression [ ,...n ]

[HAVING <constraint>]
```

### 2.1 式

`式` は、行の値をグループ化する式を指定します。

### 2.2 HAVING \<constraint\>

`HAVING <constraint>` specifies a constraint that must be defined in a `HAVING` clause, when a `GROUP BY` expression is used.

## 3つの例

このクエリは、都市ごとのすべての顧客数を返します:

```sql
SELECT COUNT(Sales.Customer/*)
FROM Sales.Customer
INNER JOINSales.Customer/Sales.Customer_Address/Sales.Address/Sales.Address
GROUP by Sales.Address/City
```

このクエリは、都市ごとのすべての注文の合計価格の合計を返します:

```sql
SELECT SUM(Sales.Order/TotalPrice)
FROM Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer/Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
```

このクエリは、合計が1000を超える都市ごとのすべての注文の合計価格の合計を返します。 0または都市はロスダンです：

```sql
SELECT SUM(Sales.Order/TotalPrice)
FROM Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer/Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
HAVING SUM(Sales.Order/TotalPrice) > 1000.0 OR Sales.Address/City = 'Losdun'
```

