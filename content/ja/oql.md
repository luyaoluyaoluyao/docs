---
title: "OQL"
parent: "データセット"
---


Mendix OQL (Object Query Language) は [SQL](http://en.wikipedia.org/wiki/Sql) と同じようなリレーショナルなクエリ言語です。 OQL の主な利点は、OQL が実際のデータベーステーブル名の代わりにエンティティと関連名を使用することです。

さらに、OQLはあらかじめ定義されたリレーション(関連付け)を使用して、どの列を結合すべきかを計算することなく、簡単にオブジェクトを結合することができます。 これらの違いにもかかわらず、多くのSQLキーワードはOQLでも動作します。

OQL クエリの例は次のとおりです。

*   `SELECT Name FROM Sales.Customer` すべての顧客の名前を取得します。
*   `Select FirstName FROM Sales.Customer WHERE名 = 'Jansen` すべてのお客様の名前を取得します。
*   `SELECT AVG(TotalPrice) FROM Sales.Order WherE IsPayed = 1` すべての支払済み注文の合計価格の平均を取得します。

OQL クエリは、いくつかのコンポーネントで構成されています。 詳細については、コンポーネントをクリックしてください。

| 部品をクエリする                                 | OQL                   | 目的                                                             |
| ---------------------------------------- | --------------------- | -------------------------------------------------------------- |
| **[Select 句](oql-select-clause)** (必須)   | `AVG(TotalPrice) を選択` | クエリーされるオブジェクトの属性を指定します。 取得したデータに対して実行する必要がある関数もここで定義する必要があります。 |
| **[From節](oql-from-clause)** (必須)        | `FROM Sales.Order`    | データを取得するソースエンティティを指定します。                                       |
| **[Where句](oql-where-clause)** (任意)      | `WHERE IsPaid = 1`    | 取得されるデータを制限します。                                                |
| **[節ごとのグループ](oql-group-by-clause)** (任意) | `部署ごとのグループ`           | 指定した属性の値で行をグループ化します。                                           |
| **[節による注文](oql-order-by-clause)** (任意)   | `日付で注文`               | 指定した属性の行を並べ替えます。                                               |
| **[Limit 句](oql-limit-clause)** (任意)     | `50オフセット30を制限`        | 行を合計量のサブセットに制限します。                                             |
