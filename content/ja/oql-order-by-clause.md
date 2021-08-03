---
title: "条項別OQL注文"
parent: "oql"
tags:
  - "studio pro"
---

## 1つの説明

`ORDER BY` 節は、 `SELECT` ステートメントで返される列のソート順序を指定します。 複数の列を指定できます。 列は `ORDER BY` 節の項目の順序で並べられます。

This clause can include items that do not appear in the `SELECT` clause, except when `SELECT DISTINCT` is specified or when a `GROUP BY` clause exists. When `UNION` is used, the column names or aliases must be those specified in the `SELECT` clause of the first part of the query.

## 2つの構文


構文は以下の通りです:

```sql
ORDER BY
    {
        order_by_expression [ ASC| DESC ]
}
```

### 2.1 order_by_expression

`order_by_expression` はソートする `FROM` 節からのエンティティまたはエイリアスの属性を指定します。

### 2.2 ASC。

`ASC` では、結果を昇順に、最低から最高値に昇順にする必要があることを指定します。 これはデフォルトのソートタイプです。

### 2.3 DESC

`DESC` では、結果を降順に、最高値から最低値にするように指定します。

{{% alert type="info" %}}
NULL 値のデフォルト順序の動作の詳細 see the [NULL値 Order Behavior](ordering-behavior#null-ordering-behavior) section of *Order By Behavior*.
{{% /alert %}}

## 3つの例

このクエリはすべての顧客を取得し、姓、昇順でソートされた名を返します。

```sql
Select FirstName FROM Sales.Customer
ORDER BY LastName
```

このクエリはすべての顧客を取得し、姓でソートされた姓と姓を返します。

```sql
SELECT FirstName + ' ' + LastName FROM Sales.Customer
ORDER BY LastName DESC.
```
