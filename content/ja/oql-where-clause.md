---
title: "OQL ここで条項を使用する"
parent: "oql"
tags:
  - "studio pro"
  - "クエリ"
  - "どこで"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-where-clause.pdf) をクリックしてください。
{{% /alert %}}

WHERE句は、取得されるデータがどのように制約される必要があるかを指定します。

構文は以下の通りです:

```
場所 <constraint>
```

`<constraint>` 値が常に真に等しい式。 式は演算子、関数、キーワード、システム変数を使用する単純な比較で構成されています。

{{% alert type="info" %}}

```
SELECT FirstName FROM Sales.Customer
WHERE LastName = 'Jansen'
```

このクエリは、名前が「Jansen」に等しいすべての顧客を取得します。

{{% /alert %}}{{% alert type="info" %}}

```
SELECT FirstName FROM Sales.Customer
INNER JOIN Sales.Customer/Sales.Customer_Address/Sales.Address
WHERESales.Address/City = 'Rotterdam'
```

このクエリは、「ロッテルダム」に住んでいるすべての顧客を取得します。

{{% /alert %}}
