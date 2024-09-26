---
title: "条項別OQL注文"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-order-by-clause.pdf) をクリックしてください。
{{% /alert %}}

ORDER BY句は、SELECT文で返される列のソート順を指定します。 複数の列を指定できます。 カラムはORDER BY句内のアイテムの順序で並べられています。 SELECT句に表示されない項目を含めることができます。 SELECT DISTINCT が指定されている場合、または GROUP BY 句が存在する場合を除きます。 UNION を使用する場合、クエリの最初の部分の SELECT 句で列名またはエイリアスを指定する必要があります。

構文は以下の通りです:

```
ORDER BY
    {
        order_by_expression [ ASC| DESC ]
}
```

**order_by_expression** ソートするエンティティまたはFROM句のエイリアスの属性を指定します。

**ASC** 結果を昇順に並べる必要があることを指定します。 ASCはデフォルトのソートです。

**DESC** 結果を降順に並べることを指定します。

このクエリはすべての顧客を取得し、姓、昇順でソートされた名を返します。

```
Select FirstName FROM Sales.Customer
ORDER BY LastName
```

このクエリはすべての顧客を取得し、姓でソートされた姓と姓を返します。

```
SELECT FirstName + ' ' + LastName FROM Sales.Customer
ORDER BY LastName DESC.
```

{{% alert type="info" %}}
NULL 値のデフォルトの順序付け動作については、 [](ordering-behavior#null-ordering-behavior) Order By Behavior *の* NULL値の順序付け動作</em> セクションを参照してください。
{{% /alert %}}
