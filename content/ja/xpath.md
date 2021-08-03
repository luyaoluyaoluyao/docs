---
title: "XPath"
category: "デスクトップ モデラー"
description: "Mendix での XPath クエリ言語の使用方法を関数とサンプルを表示します。"
---

## 1 XPath の概要

Mendix XPath は、データを取得するために設計された Mendix クエリ言語の1つです。 XPath は、Mendix オブジェクトとその属性または関連付けのデータを選択するためにパス式を使用します。

XPath クエリはモデラーの両方に書き込むことができます。 例えば、マイクロフローのアクティビティで取得したデータの制約を指定したい場合や、直接コード内の . Javaアクションのavaファイル すべての演算子がModelerでサポートされているわけではなく、クエリの構文はModeler環境とJava環境で異なる場合があることに注意してください。

XPath クエリの例は次のとおりです。

*   `//Sales.Customer` すべての顧客を取得します。
*   `//Sales.Customer[Name='Jansen']` 「Jansen」という名前ですべての顧客を取得します。
*   `avg(//Sales.Order[IsPaid = true()]/TotalPrice)` すべての支払済み注文の合計価格の平均を取得します。

{{% alert type="warning" %}}

モデラーでは、完全なクエリを記述するのではなく、制約のみを記述します。 エンティティはコンテキストによって暗黙的に決定されます。 ですから、 `//Sales.Customer[Name='Jansen']` の代わりに、顧客のコンテキストで `[Name='Jansen']` のみ記述します。 Javaでは、二重スラッシュとエンティティ名を含む全クエリを記述します。

{{% /alert %}}

## 2つの XPath 要素

一般的な Mendix XPath クエリは、いくつかの要素で構成されています。

| A            | B               | C                 | D           |
| ------------ | --------------- | ----------------- | ----------- |
| 集計関数 (オプション) | 取得するエンティティ (必須) | 制約（任意）            | 取得する属性 (任意) |
| avg          | //Sales.Order   | [IsPaid = true()] | /合計価格       |

要素 B は、各クエリのコアを記述し、取得されるオブジェクトの説明で構成されます。 このセグメントは常に2つのスラッシュで始まり、ピリオドで区切られたエンティティを含むモジュールによって先頭にアクセスしたいエンティティの名前を含みます。 例えば、 //Sales.Customer は、モジュール 'Sales' 内のエンティティ 'Customer' のすべてのオブジェクトを返します。

クエリの要素 C はオプションで、取得されるデータを制限するための 1 つ以上の制約を含んでいます。

次のクエリを検討してください:

`//Sales.Customer[Name='Jansen']`

この制約は、括弧の間で明確に表示され、'Name' 属性が 'Jansen' に等しいオブジェクトに取得されたオブジェクトを制限します。 Jansen 以外の名前のオブジェクトはリストから除外されます。 単一のクエリで可能な制約の数は無制限です。 これらの制約を追加および操作する方法の詳細については、 [XPath 制約](xpath-constraints) を参照してください。

クエリの要素 D はオプションで、取得したエンティティの属性を指定します。 すべてのデータがオブジェクトに格納されているため、このオプションはモデラー自体ではほとんど使用されません。 1つの属性のリストを扱うのを煩雑で複雑にする ただし、様々なJavaアクションはそのようなリストを使用しています。 また、この機能は Part A と組み合わせて使用することで、特定の変数の集計を簡単に作成できます。

要素 クエリのAはオプションで、集計を指定します。 Element A can be one of the following functions: [avg](xpath-avg), [count](xpath-count), [max](xpath-max), [min](xpath-min) and [sum](xpath-sum). 'count' を除き、これらの各関数は、D 要素に特定の属性を指定する必要があります。

これらの基本ガイドラインの例外は ID クエリです。 詳細は [XPath id](xpath-id) を参照してください。

## 3トークン

詳細に関しては、 [XPath トークン](xpath-tokens) を参照してください。

## 4 演算子

詳細に関しては、 [XPath 演算子](xpath-operators) を参照してください。

## 5つの機能

以下の XPath 関数を使用できます。

* [XPath 関数](xpath-query-functions):
    * [avg](xpath-avg)
    * [カウント](xpath-count)
    * [最大](xpath-max)
    * [分](xpath-min)
    * [sum](xpath-sum)
* [制約関数](xpath-constraint-functions):
    * [を含む](xpath-contains)
    * [Starts-with](xpath-starts-with)
    * [ends-with](xpath-ends-with)
    * [いいえ](xpath-not)
    * [true](xpath-true)
    * [false](xpath-false)
