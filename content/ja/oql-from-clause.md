---
title: "条項からの OQL"
parent: "oql"
tags:
  - "studio pro"
---

## 1つの説明

`FROM` 節は、データを取得するエンティティまたはその他のソースを指定します。 この節は、 `FROM` キーワードの後にエンティティ名が続きます。 他のエンティティからデータを選択するには、 `JOIN` キーワードを使用してこれらのエンティティを追加します。 この構文は公式の `SQL FROM` 節構文よりも少し厳密です。

## 2つの構文

これは完全な構文の例です。

```sql
FROM
    {
        entity_name | ( sub_oql_query )
    }
    [ AS ] from_alias ]

    {
        { INNER | { { LEFT | RIGHT | FULL } [ OUTER ] } JOIN
        entity_path [ AS ]
        [ ON <constraint> ]
    } [ ,. .n
```

### 2.1 entity_name

`entity_name` は、データを取得する必要があるエンティティを指定します。 エンティティ名は必要に応じて二重引用符でカプセル化することができます。 エンティティ名が ( `Order` や `Group`のような) 予約済みの OQL 単語である場合、二重引用符は必須です。

### 2.2 ( sub_oql_query )

`(sub_oql_query )` は、データを取得する必要がある別の OQL クエリを指定します。 これは現在のクエリのソースになります。 副問い合わせは括弧内に置く必要があります。

### 2.3 参加

4つの異なる `JOIN` タイプがサポートされています:

* `インナー参加`
* `残りの出口で参加`
* `右アウトライン参加`
* `完全参加`

構文は以下の通りです:

```sql
{ INDER | { { LEFT | RIGHT | FULL } [ OTER ] } JOIN
        entity_path [ AS ] from_alias ]
        [ ON <constraint>]
```

#### 2.3.1 entity_path

`entity_path` は、結合するエンティティと、 `FROM` 節の以前に定義されたエンティティからのパスを指定します。

パスの例 `Crm.Customer/Crm.Customer_Address/Crm.Address` はエンティティ **Crm.Customer** から新しいエンティティ **Crm.Address** までのパスを定義します。

`entity_name`と同様に、二重引用符を使用できます。

#### 2.3.2 \[ ON \<constraint\>\]

`[ ON <constraint> ]` は、 `FROM` 節の `JOIN` 部分で指定されたエンティティを拘束します。 制約の構文は `WHERE` 節の構文と似ています。 拘束内では、現在および直前の `` `JOIN` 要素からのエンティティと format@@4 FROMエイリアスのみが使用できます。

制約を使用することは任意です。システムは指定された `entity_path` に基づいて適切な `JOIN` 条件を生成します。

#### 2.3.3 参加型

##### 2.3.3.1 インナー参加

`INDER JOIN` は、エンティティ間の最も一般的な結合操作であり、デフォルトの結合タイプを表します。 クエリでは、エンティティAの各行とエンティティBの各行を比較して、関連付けを持つ `JOIN` 述語を満たすすべての行のペアを見つけます。 関連付けが存在し、 `JOIN` 述語が満たされた場合。 A と B の一致する各行の列の値は、結果の行に結合されます。

構文は以下の通りです:

```sql
[ INNER ] JOIN entity_path [ ON <constraint>]
```

##### 2.3.3.2 残りのアウトラインに参加

`LEFT OUTER JOIN` クエリは、エンティティAの各行をエンティティBの各行と比較し、関連付けを持つすべての行のペアを見つけ、 `JOIN` 述語を満たします。 関連付けが存在し、 `JOIN` 述語が満たされた場合 A と B の一致した行ごとの列の値は、結果の行に結合されます。

しかし、 `INNER JOIN` 建設とは対照的に。 クエリはエンティティBと一致しないエンティティAの行も返します。 エンティティ B のカラムが指定された場合、これらのカラムにはこれらのカラムの null 値が含まれます。

構文は以下の通りです:

```sql
LEFT [ OUTER ] entity_path [ ON <constraint>]
```

##### 2.3.3.3 右アウトラインに参加

`RIGHT OUTER JOIN` クエリはエンティティAの各行をエンティティBの各行と比較し、関連付けを持つすべての行のペアを見つけ、 `JOIN` 述語を満たす。 関連付けが存在し、 `JOIN` 述語が満たされた場合。 A と B の一致する各行の列の値は、結果の行に結合されます。

しかし、 `INDER JOIN` 構築とは対照的に、エンティティ A と一致しないエンティティ B からの行も返されます。 エンティティ A のカラムが指定された場合、これらのカラムはこれらの行の null 値を含みます。

構文は以下の通りです:

```sql
RIGHT [ OUTER ] JOIN entity_path [ ON <constraint>]
```

##### 2.3.3.4 フルアウター参加

`FULL OUTER JOIN` クエリは、エンティティAの各行をエンティティBの各行と比較し、関連付けを持つすべての行のペアを見つけ、 `JOIN` 述語を満たします。 関連付けが存在し、 `JOIN` 述語が満たされた場合 A と B からの一致した行ごとの列の値は、結果行に結合されます。

しかし、 `INDER JOIN` 構築とは対照的に、 *一致しない* エンティティからのデータも返されます。 これらの行の場合、欠落しているエンティティの列には null 値が含まれます。

構文は以下の通りです:

```sql
フル[ OUTER ] エンティティ_path [ ON <constraint>]
```

#### 2.3.4 例

このシナリオでは テーブルBには関連性のないテーブルAのレコードを取得するために `レフト・アウター結合` を使用しています。

たとえば、エンティティ **顧客** と **注文**があり、顧客は複数の注文に関連付けることができます。 全く注文がないすべての顧客を取得します。

```sql
SELECT 
  Customer/Name as Name,
  Customer/<anyotherattribute> as <anyotherattribute>
FROM MyModule.Customer
  LEFT OUTER JOIN Customer/MyModule.Customer_Order/MyModule.Order as Order
WHERE注文/ID IS NULL.
```
