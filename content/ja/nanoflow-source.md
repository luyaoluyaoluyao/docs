---
title: "Nanoflow Source"
parent: "データソース"
tags:
  - "studio pro"
  - "ナノフローソース"
  - "データソース"
menu_order: 50
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/nanoflow-source.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**Nanoflow** データソースは [データ ビュー](data-view) および [リスト ビュー](list-view) で使用できます。

In most cases, you use the *database*, *association* or *XPath* data sources to fill a [data widget](data-widgets). ただし、対象となるオブジェクトは特定の基準に準拠する必要がある場合があります。 [XPath](xpath-constraints) では扱えない、または異なるオブジェクトが異なる状況下で表示されます。 このような状況では、 *nanoflow data source* が必要となる場合があります。 ナノフローとその利点の詳細については、 [Nanoflows](nanoflows) を参照してください。

ナノレベルのデータソースを持つデータウィジェットがブラウザに表示または更新されたとき。 指定されたナノフローを実行し戻り値を表示します ナノの中で物体が獲得される方法は、完全にあなた次第です。 どの物体が戻ってくるかを無限にコントロールできるのです

nanoflow データソースはすべてのコンテキストを無視します。 ナノの中で記述された動作を実行します たとえば、nanoflow データソースを持つネストされたデータウィジェットは、自動的にデータウィジェットを作成したり、データウィジェットへの関連付けを呼び出したりすることはありません。

## 2 Nanoflow Data Source Example

たとえば、注文タイプに基づいて潜在的な注文のリストを表示する必要があるリストがあります。

![Nanoflow Source](attachments/data-widgets/nanoflow-source.png) If the *OrderType* of the *Order* entity is set to *Cars*, then the data grid should display all *Products* for which the Boolean *Motorized* is set to true. *OrderType* が *Bicycles* の場合、 *Motorized* がfalse に設定されているオブジェクトのみを表示する必要があります。 *OrderType* が空の場合、データグリッドは空のままにします。

![エンティティの例](attachments/data-widgets/entities-example.jpg) 属性型の不一致のため、XPath により制約を受けることができず、ナノレベルのデータソースが必要となります。

ユースケースのnanoflowは次のようになります:

![Nanoflow Example](attachments/data-widgets/microflow-nanoflow-example.jpg) このナノフローは以下のようになります:

1. パラメータとして、囲まれたデータビューの *Order* を渡します。

2. その後、 *OrderType* 属性に分割され、各列挙値に対して異なる製品セットを取得します。

3. nanoflowは製品のリストを返し、各エンドイベントはリストを返すように構成されています。

    {{% alert type="info" %}} *空の* パスも値を必要とします。 `空の` も値です。
    {{% /alert %}}

## 3つのプロパティ

### 3.1 Nanoflow

ウィジェットを作成するために使用するナノフローを定義します。 このnanoflowは、ウィジェットがブラウザにロードされたりリフレッシュされたりするたびに実行されます。 nanoflowは使用されているウィジェットに応じて、オブジェクトまたはオブジェクトのリストの戻り値を持たなければなりません。

## 4 続きを読む

* [Nanoflows](ナノフロー)
* [データウィジェット](data-widgets)