---
title: "条項からの OQL"
parent: "oql"
---

## 1つの紹介

`FROM` 節は、データを取得するエンティティまたはその他のソースを指定します。 この節はエンティティ名に続く `FROM` キーワードで始まります。 他のエンティティからもデータを選択するには、これらのエンティティを `JOIN` キーワードで追加します。 この構文は公式の `SQL FROM` 節構文よりも少し厳密です。

これは完全な構文の例です。

```
FROM
    {
        entity_name | ( sub_oql_query )
    }
    [ AS ] from_alias ]

    {
        { INDER | { { LEFT | RIGHT | FULL } [ OTER ] } JOIN
        entity_path [ AS ]
        ON <constraint>
    } [ ,. .n
```

## 2 entity_name

データを取得するエンティティを指定します。

## 3 ( sub_oql_query )

データを取得する別の OQL クエリを指定します。 これは現在のクエリのソースになります。 副問い合わせは括弧内に置く必要があります。

## 4人で参加

このクエリに参加するエンティティへのパスを指定します。 サポートされている4つの異なるタイプのJOINSがあります:

* インナー参加
* 残りの出口で参加
* 右アウトライン参加
* 完全参加

構文は以下の通りです:

```
 { INDER | { { LEFT | RIGHT | FULL } [ OTER ] } JOIN
        entity_path [ AS ] from_alias ]
        [ ON <constraint>]
```

### 4.1 entity_path

これは、結合するエンティティと、 `FROM` 節の以前に定義されたエンティティからこのエンティティへのパスを指定します。

パス `Crm.Customer/Crm.Customer_Address/Crm.Address` は以前に定義されたエンティティ **Crm.Customer** から新しいエンティティ **Crm.Address** までのパスを定義します。

### 4.2 \[ ON \<constraint\>\]

これは、 `FROM` 節の `JOIN` 部分にある指定されたエンティティを拘束します。 制約の構文は `WHERE` 節の構文と似ています。 拘束内では、 `` の現在および直前の `` 要素からの図形と</code> のみが使用できます。

この部分は任意です。 システムは、指定された `entity_path` に基づいて適切な JOIN 条件を生成します。

### 4.3 参加タイプ

#### 4.3.1 インナー参加

`INDER JOIN` は、エンティティ間の最も一般的な結合操作であり、デフォルトの結合タイプを表します。 クエリでは、エンティティAの各行とエンティティBの各行を比較して、関連付けを持つ `JOIN` 述語を満たすすべての行のペアを見つけます。 関連付けが存在し、 `JOIN` 述語が満たされた場合。 A と B の一致する各行の列の値は、結果の行に結合されます。

構文は以下の通りです:

```
[ INNER ] JOIN entity_path [ ON <constraint>]
```

#### 4.3.2 残りのアウトラインに参加

With a `LEFT OUTER JOIN` construction, the query compares each row of entity A with each row of entity B to find all pairs of rows which have an association and thus satisfy the `JOIN` predicate. 関連付けが存在し、 `JOIN` 述語が満たされた場合 A と B の一致した行ごとの列の値は、結果の行に結合されます。

しかし、 `INNER JOIN` 建設とは対照的に。 クエリはエンティティBと一致しないエンティティAの行も返します。 エンティティ B のカラムが指定された場合、これらのカラムにはこれらのカラムの null 値が含まれます。

構文は以下の通りです:

```
LEFT [ OUTER ] entity_path [ ON <constraint>]
```

#### 4.3.3 右アウトラインに参加

With a `RIGHT OUTER JOIN` construction, the query compares each row of entity A with each row of entity B to find all pairs of rows which have an association and thus satisfy the `JOIN` predicate. 関連付けが存在し、 `JOIN` 述語が満たされた場合。 A と B の一致する各行の列の値は、結果の行に結合されます。

しかし、 `INDER JOIN` 構築とは対照的に、エンティティ A と一致しないエンティティ B からの行も返されます。 エンティティ A のカラムが指定された場合、これらのカラムはこれらの行の null 値を含みます。

構文は以下の通りです:

```
RIGHT [ OUTER ] JOIN entity_path [ ON <constraint>]
```

#### 4.3.4 フルアウター参加

`フルOUTER JOIN` 建設で クエリでは、エンティティAの各行とエンティティBの各行を比較して、関連付けを持つすべての行を検索し、ジョイン述語を満たします。 関連付けが存在し、結合述語が満たされた場合 A と B からの一致した行ごとの列の値は、結果行に結合されます。

しかし、 `INDER JOIN` 構築とは対照的に、 _一致しない_ エンティティからのデータも返されます。 これらの行の場合、欠落しているエンティティの列には null 値が含まれます。

構文は以下の通りです:

```
フル[ OUTER ] エンティティ_path [ ON <constraint>]
```

### 4.4 例

このシナリオでは テーブルBには関連性のないテーブルAのレコードを取得するために `レフト・アウター結合` を使用しています。

たとえば、エンティティ **顧客** と **注文**があり、顧客は複数の注文に関連付けることができます。 全く注文がないすべての顧客を取得します。

```
SELECT 
  Customer/Name as Name,
  Customer/<anyotherattribute> as <anyotherattribute>
FROM MyModule.Customer
  LEFT OUTER JOIN Customer/MyModule.Customer_Order/MyModule.Order as Order
WHERE注文/ID IS NULL.
```
