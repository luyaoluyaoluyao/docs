---
title: "条項によるOQL グループ"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-group-by-clause.pdf) をクリックしてください。
{{% /alert %}}

GROUP BY 句は、この節で定義された式の同じ値を共有するすべての返された行を単一の行に凝縮します。 この節の式はクエリの SELECT 句内に存在する必要があります。 GROUP BY句に含まれていないSELECT句に含まれるすべての式は集計または集計関数でなければなりません。

構文は以下の通りです:

```
GROUP BY
    expression [ ,...n ]

[HAVING <constraint>]
```

**expression** 行のグループ化する式を指定します。

`HAVING <constraint>` 制約を指定します。 GROUP BY 式が使用される場合は、HAVING 句内に制約を定義する必要があります。

{{% alert type="info" %}}

```
SELECT COUNT(Sales.Customer/*)
FROM Sales.Customer
INNER JOINSales.Customer/Sales.Customer_Address/Sales.Address/Sales.Address
GROUP by Sales.Address/City
```

このクエリは都市ごとのすべての顧客数を返します。

{{% /alert %}}{{% alert type="info" %}}

```
SELECT SUM(Sales.Order/TotalPrice)
FROM Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer/Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
```

このクエリは、都市あたりのすべての注文の合計価格の合計を返します。

{{% /alert %}}{{% alert type="info" %}}

```
SELECT SUM(Sales.Order/TotalPrice)
FROM Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer/Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
HAVING SUM(Sales.Order/TotalPrice) > 1000.0 OR Sales.Address/City = 'Losdun'
```

このクエリは、合計が1000を超える都市ごとのすべての注文の合計価格の合計を返します。 0または都市はロスダンです。

{{% /alert %}}
