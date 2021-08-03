---
title: "条項別OQL注文"
parent: "oql"
---

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
NULL 値のデフォルト順序の動作の詳細 see the [NULL値 Order Behavior](ordering-behavior#null-ordering-behavior) section of *Order By Behavior*.
{{% /alert %}}
