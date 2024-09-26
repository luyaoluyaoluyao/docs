---
title: "OData クエリオプション"
parent: "published-odata-services"
tags:
  - "OData"
  - "フィルター"
  - "カウント"
  - "並べ替え"
  - "select"
  - "ページ"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/odata-query-options.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

これはODataのクエリオプションのリストです。

{{% alert type="info" %}}
現在、ここで説明されているオプションのみをサポートしています。
{{% /alert %}}

## 2 オブジェクトの取得

### 2.1 すべてのオブジェクトの取得

すべてのオブジェクトはURIを指定することで取得できます。 例: `/odata/myservice/myresource`。 ブラウザで URI を指定すると、これを見ることができます。

### 2.2 単一オブジェクトの取得

URI 内のオブジェクト識別子を渡すことで、単一のオブジェクトを取得できます。 例: `/odata/myservice/myresource(84444249301330581)`.

### 2.3 関連するオブジェクトの取得

関連付けられたオブジェクトは、 `$expand` クエリパラメータを渡すことで取得できます。 例: `/odata/myservice/Exployees?$expand=Cars,Address/City`.

{{% alert type="info" %}}
`$expand` 機能は、Studio Pro [8.11.0](/releasenotes/studio-pro/8.11#8110) で導入されました。
{{% /alert %}}

## 3 オブジェクト数の計算

### 3.1 オブジェクト数の取得

`$count` クエリオプションを指定すると、オブジェクトの数を調べることができます。 この場合、結果はオブジェクト数の整数になります。 例: `/odata/myservice/myresource/$count`.

### 3.2 インライン数

`$inlinecount` クエリオプションを 'allpages' に設定すると、返される項目の数が結果に含まれます。 例: `?$inlinecount=allpages`.

## フィルタリング4

フィルタはリクエストに `$filter=...` パラメータを追加することで適用されます。 例: `/Employees ?$filter=Name eq 'John'`.

### 4.1 属性を渡します

この表では、異なる属性タイプの値を渡す方法について説明します。

| タイプ     | パスする方法                                                                                                   |
| ------- | -------------------------------------------------------------------------------------------------------- |
| 文字列と列挙値 | シングルクォートで囲まれています（例：「John」）                                                                               |
| 日時      | `datetime` の前に、一括引用符で囲まれています (例: datetime'2015-01-01' or datetime'&lt;epoch value here&gt;') |
| その他     | プレーン値 (例: 15)                                                                                            |

### 4.2 比較演算子

以下の比較演算子をサポートします。

| 演算子 | 意味     | 例                                    |
| --- | ------ | ------------------------------------ |
| eq  | 等しい    | `/Employee?$filter=Name eq 'John'`   |
| ne  | 等しくない  | `/Employees ?$filter=Name ne 'John'` |
| GMT | より大きい  | `/Employees?$filter=年齢 gt 15`        |
| lt  | より小さい  | `/Employees?$filter=年齢 lt 15`        |
| ge  | 以上     | `/Employees?$filter=年齢 15`           |
| le  | 以下か等しい | `/Employees?$filter=年齢ル15`           |

### 4.3 算術演算子

| 演算子 | 意味      | 例                                      | Returns            |
| --- | ------- | -------------------------------------- | ------------------ |
| 追加  | 追加      | `/Products?$filter=Prices add 2 eq 10` | 価格が8のすべての製品        |
| sub | minus   | `/Products?$filter=Prices sub2 eq 10`  | 価格12のすべての製品        |
| mul | 乗算された   | `/Products?$filter=価格 mil 2 eq 10`     | すべての製品 価格5         |
| div | で割った    | `/Products?$filter=Prices div 2 eq 10` | 価格20のすべての製品        |
| mod | modulus | `/Products?$filter=価格 mod 5 eq 0`      | すべての商品の価格が5で割り切れます |

### 4.4 関数

| 関数          | 例                                               | Returns                              |
| ----------- | ----------------------------------------------- | ------------------------------------ |
| substringof | `/Employees ?$filter=substringof('f', Name)`    | 「f」を含む名前を持つすべての従業員。                  |
| endswith    | `/Employees ?$filter=endswith(Name, 'f')`       | 「f」で終わる名前を持つすべての従業員。                 |
| startswith  | `/Employee?$filter=startswith(Name, 'f')`       | 「f」で始まる名前を持つすべての従業員。                 |
| 長さ          | `/Employees ?$filter=length(Name) eq 5`         | 名前の長さが5のすべての従業員です                    |
| 年           | `/Employees?$filter=year(DateOfBirth) eq 1990`  | 1990年生まれの全社員。                        |
| 月           | `/Employees?$filter=month(DateOfBirth) eq 5`    | 5月生まれの社員全員。                          |
| 日           | `/Employees?$filter=day(DateOfBirth) eq 31`     | 31日目に生まれた従業員全員。                      |
| 時           | `/Employees?$filter=hour(Registration) eq 13`   | 全従業員登録は13:00(午後1時1分)から13:59(午後1時59分) |
| 分           | `/Employees?$filter=minute(Registration) eq 55` | すべての従業員は、任意の時間の55分に登録しました            |
| 秒           | `/Employees?$filter=second(Registration) eq 55` | すべての従業員は、任意の時間の分の55秒に登録されました         |

### 4.5 結合フィルター

フィルターは `と`、 `または`、 `ではなく`、 および `()` と組み合わせることができます。 例: `?$filter=Name eq 'John' と (Agge gt 65 or Age lt 11)`.

| 組み合わせ | 例                                                                 |
| ----- | ----------------------------------------------------------------- |
| と     | `/Employee?$filter=Name eq 'John' and Age gt 65`                  |
| または   | `/Employees?$filter=Age gt 65 or Age lt 11`                       |
| いいえ   | `/Employees ?$filter=not(Name eq 'John’)`                         |
| ( )   | `/Employees?$filter=Name eq 'John' and (Agge gt 65 or Age lt 11)` |

### 4.6 関連付けによるフィルタリング

関連するエンティティの属性をフィルタリングできます。 これを行う方法は、関連付けが 1 つのオブジェクトまたはオブジェクトのリストを公開するかによって異なります。

| タイプ              | 例                                                  |
| ---------------- | -------------------------------------------------- |
| 関連するオブジェクトでフィルター | `People?$filter=BirthPlace/CityName eq 'Rotterdam` |
| 関連付けられたリストでフィルター | `$filter=BornIn/any(person:person/Year le 1919)`   |

関連付けられているオブジェクトやリストへのフィルタリングは [リンク](odata-representation#associations) として関連付けを公開する場合に可能です。 あなたが [関連するオブジェクト ID として関連付けを公開する場合は不可能です](odata-representation#associations)。

## 5ソート

`$orderby` クエリオプションを使用して結果をソートできます。 例: `?$orderby=名前` または `?$orderby=誕生地/都市名`。

デフォルトの方向は昇順で、これを明示的にすることができます。 例: `?$orderby=Name asc`.

結果を降順に並べることもできます。 例: `?$orderby=Name desc`.

複数の属性をカンマ区切りで並べ替えることができます。 例: `?$orderby=名前 asc,Age desc`.

## 6項目の選択

`$select` クエリオプションを指定することで、返す属性と関連性を選択できます。 例: `?$select=名前,年齢`.

## 7ページ

### 7.1 トップ (制限)

`$top` クエリオプションを使用して返されるオブジェクトの数を制限することができます。ここで、制限は正の整数です。 例: `?$top=100`.

### 7.2 スキップ (オフセット)

`$skip` クエリオプションを使用して結果を取得する前に、多くのオブジェクトをスキップすることができます。オフセットは正の整数です。 例: `?$skip=100` は、リスト内の 101番目のオブジェクトから始まるオブジェクトを返します。

## 8 Null Literals

値を `null` リテラルと比較できます。 例: `?$filter=Name eq null`.

この例では、 `Name` はデータベースに割り当てられた値を持たない文字列属性です。 `null` は、 *''* (これは空の文字列) ではなく、 `値` を意味しないことに注意してください。

関連付けに対してフィルタリングする場合、null リテラルは非常に便利です。 例: `?$filter=Association_A_B ne null`. この例では、 エンティティタイプ `A` のオブジェクトに対して、エンティティタイプ `B` のオブジェクトに対して少なくとも1つの関連付けセットをクエリします。
