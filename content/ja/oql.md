---
title: "OQL"
parent: "データセット"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

Mendix Object Query Language (OQL) は、 [SQL](http://en.wikipedia.org/wiki/Sql) と同じようなリレーショナルなクエリ言語です。 OQL の主な利点は、実際のデータベーステーブル名の代わりにエンティティ名と関連名を使用することです。

さらに、OQLは事前に定義されたリレーション(アソシエーション)を使用して、どの列を結合すべきかを計算することなく、簡単にオブジェクトを結合することができます。 これらの違いにもかかわらず、多くの SQL キーワードは OQL でも動作します。

以下は、OQL クエリの例です。

* `SELECT Name FROM Sales.Customer` – すべてのお客様の名前を取得します
* `Select FirstName FROM Sales.Customer WHERE名 = 'Jansen`  – 名前を持つすべての顧客の最初の名前を取得します。
* `SELECT AVG(TotalPrice) FROM Sales."Order" WHERE IsPaid = 1`  –  retrieves the average of the total prices of all paid orders (`Order` needs to be encapsulated in quotes because it is a reserved word, meaning it can be used for `ORDER BY`)

{{% alert type="info" %}}
OQL クエリは、すぐに使用できるセキュリティを考慮しません。 これは、OQL を使用してカスタムセキュリティ式を手動で定義できることを意味します。 場合によっては、OQL を使用してセキュリティを自分自身で扱うことができます (XPathのボックス外のセキュリティを使用する代わりに)。
{{% /alert %}}

オンラインの OQL サンプルを [OQL Playground](https://mydemoversion8-sandbox.mxapps.io/p/OQL) デモアプリでお試しください。

## 2クエリコンポーネント

OQL クエリでは、次のコンポーネントを使用できます。

| クエリパート                               | OQL                   | 目的                                                             |
| ------------------------------------ | --------------------- | -------------------------------------------------------------- |
| [選択節](oql-select-clause) (必須)        | `AVG(TotalPrice) を選択` | クエリーされるオブジェクトの属性を指定します。 取得したデータに対して実行する必要がある関数もここで定義する必要があります。 |
| [From節](oql-from-clause) (必須)        | `FROM Sales.Order`    | データを取得するソースエンティティを指定します。                                       |
| [Where句](oql-where-clause) (任意)      | `WHERE IsPaid = 1`    | 取得されるデータを制限します。                                                |
| [節ごとのグループ](oql-group-by-clause) (任意) | `部署ごとのグループ`           | 指定した属性の値で行をグループ化します。                                           |
| [節ごとの順序](oql-order-by-clause) (任意)   | `日付で注文`               | 指定した属性の行を並べ替えます。                                               |
| [Limit 句](oql-limit-clause) (任意)     | `50オフセット30を制限`        | 行を合計量のサブセットに制限します。                                             |

