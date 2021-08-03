---
title: "OQL ここで条項を使用する"
parent: "oql"
tags:
  - "studio pro"
  - "クエリ"
  - "どこで"
---

## 1つの説明

`WHERE` 節では、取得されるデータがどのように制約されるかを指定します。

## 2つの構文

構文は以下の通りです:

```sql
場所 <constraint>
```

`<constraint>` は、値が常に真に等しい式です。 式は演算子、関数、キーワード、システム変数を使用する単純な比較で構成されています。

詳細については、 [OQL 式](oql-expressions) を参照してください。

## 3つの例

このクエリは、名前が "Jansen" に等しいすべての顧客を取得します。

```sql
SELECT FirstName FROM Sales.Customer
WHERE LastName = 'Jansen'
```

このクエリは、「Rotterdam」に住んでいるすべての顧客を取得します：

```sql
SELECT FirstName FROM Sales.Customer
INNER JOIN Sales.Customer/Sales.Customer_Address/Sales.Address
WHERESales.Address/City = 'Rotterdam'
```
