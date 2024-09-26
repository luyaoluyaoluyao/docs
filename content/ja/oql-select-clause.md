---
title: "OQL Select Clause"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-select-clause.pdf) をクリックしてください。
{{% /alert %}}

SELECT句は、どのエンティティ属性またはその他の指定されたデータを取得するかを指定します。 `SELECT` 節は、 `SELECT` と1つ以上の式で構成されます。 これらの式はコンマで区切られなければなりません。 各式は、結果の列を定義します。 各式にはエイリアスがあり、結果の列の名前になります。

構文は以下の通りです:

```
SELECT [ DISTINCT ]
    {
            *
        | { entity_name | from_alias }.*
        | { expression [ [ AS ] column_alias ] } [ ,...n ]
    }
```

`DISTINCT` - 結果に二重行を表示してはいけないことを指定する。

`*` (アスタリスク) - FROM句に含まれるすべてのエンティティのすべての属性を返すよう指定します。

`entity_name.*`, `from_alias.*` – FROM句の指定されたエンティティまたは式のすべての属性を返すよう指定します。 `entity_name` は必要に応じて二重引用符で囲むことができる。 エンティティ名が ( `Order` や `Group`のような) 予約済みの OQL 単語である場合、二重引用符は必須です。

{{% alert type="info" %}}

```
SELECT Sales.Customer.* FROM Sales.Customer
```

```
担当者を選択してください。* 営業担当者からお客様を担当者にする
```

```
SELECT "Sales.Order".* FROM "Sales.Order"
```

{{% /alert %}}

`表現`

定数、関数、属性名、定数、および演算子またはサブクエリによって接続された関数の組み合わせです。 より多くの式を追加する場合は、各式の間にカンマを置きます。

{{% alert type="info" %}}

```
SELECT Name AS CustomerName, LastName AS CustomerLastName, Birthday, Category FROM Sales.Customer
```

{{% /alert %}}

詳細は [このページ](oql-expressions) を参照してください。

`column_alias` – 結果の列名を置き換える代替名です。 属性名が取得されると、結果の列は 'Name' です。 エイリアスを使用すると、「顧客名」のように別の結果列名を指定できます。 エイリアスにはスペースを含めることができます。

{{% alert type="info" %}}

```
SELECT Sales.Customer.Name As CustomerName FROM Sales.Customer
```

```
SELECT Sales.Customer.Name as 'Customer Name' FROM Sales.Customer
```

{{% /alert %}}
