---
title: "OQL Select Clause"
parent: "oql"
tags:
  - "studio pro"
---

## 1つの説明

`SELECT` 節は、どのエンティティ属性またはその他の指定されたデータを取得する必要があるかを指定します。 `SELECT` 節は、 `SELECT` と1つ以上の式で構成されます。 これらの式はコンマで区切られなければなりません。 各式は、結果の列を定義します。 各式にはエイリアスがあり、結果の列の名前になります。

## 2つの構文

構文は以下の通りです:

```sql
SELECT [ DISTINCT ]
    {
            *
        | { entity_name | from_alias }.*
        | { expression [ [ AS ] column_alias ] } [ ,...n ]
    }
```

### 2.1 DISTINCT

`DISTINCT` は、結果に二重行を表示してはいけないことを指定している。

### 2.2 * (アスタリスク)

`*` (アスタリスク) は、 `FROM` 節に含まれるすべてのエンティティのすべての属性を返すよう指定します。

### 2.3 entity_name.* と from_alias.*

`entity_name.*` and `from_alias.*` specify that all attributes of the specified entity or expression of the `FROM` clause should be returned. `entity_name` は必要に応じて二重引用符で囲むことができる。 エンティティ名が予約済みの OQL 単語の場合、ダブルクォートは必須です ( `Order` や `Group` のように)。

```sql
SELECT Sales.Customer.* FROM Sales.Customer
```

```sql
担当者を選択してください。* 営業担当者からお客様を担当者にする
```

```sql
SELECT "Sales.Order".* FROM "Sales.Order"
```
### 2.4 式

`式` は、定数、関数、または属性名、定数、および演算子またはサブクエリによって接続された関数の任意の組み合わせです。 より多くの式を追加する場合は、各式の間にカンマを置きます。

```sql
SELECT Name AS CustomerName, LastName AS CustomerLastName, Birthday, Category FROM Sales.Customer
```

詳細については、 [OQL 式](oql-expressions) を参照してください。

### 2.5 column_alias

`column_alias` は、結果の列名を置き換える代替名です。 name 属性が取得されると、結果の列は "Name" になります。 エイリアスを使用すると、"顧客名" のように別の結果列名を指定できます。 エイリアスにはスペースを含めることができます。

```sql
SELECT Sales.Customer.Name As CustomerName FROM Sales.Customer
```

```sql
SELECT Sales.Customer.Name as 'Customer Name' FROM Sales.Customer
```
