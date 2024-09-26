---
title: "OQL制限条項について"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-limit-clause.pdf) をクリックしてください。
{{% /alert %}}

limit 節では、クエリの結果の一部を返すことができます。

構文は以下の通りです:

```
[ 制限番号 ] [ オフセット番号 ]
```

**LIMIT** 返す行の数を指定します。

**OFFSET** 結果行を返す前にスキップする行数を指定します。

{{% alert type="info" %}}

```
販売からファーストネームを選択します。顧客
名でオーダー
LIMIT 10
```

このクエリは、姓でソートされた最初の10人の顧客を取得します。

{{% /alert %}}{{% alert type="info" %}}

```
SELECT FirstName FROM Sales.Customer
ORDER BY LastName
OFFSET 10
```

このクエリは、最初の10を除くすべての顧客を、姓でソートします。

{{% /alert %}}{{% alert type="info" %}}

```
販売からファーストネームを選択してください。顧客
姓でオーダーする
オフセット10を制限する
```

このクエリでは、11から20までの顧客名でソートされます。

{{% /alert %}}
