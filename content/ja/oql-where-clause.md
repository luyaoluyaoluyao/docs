---
title: "OQL ここで条項を使用する"
parent: "oql"
---


WHERE句は、取得されるデータがどのように制約される必要があるかを指定します。

構文は以下の通りです:

```
場所 <constraint>
```

`<constraint>` 値が常に真に等しい式。 式は、演算子、関数、キーワード、システム変数と単純な比較可能で構成されています。

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
