---
title: "キャストオブジェクト"
parent: "object-activity"
menu_order: 10
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/cast-object.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

キャストオブジェクトのアクティビティは、 [オブジェクト型の決定](object-type-decision) の後にマイクロフローで使用され、一般化されたオブジェクト型からオブジェクト型の決定からパスの特殊なオブジェクト型に変更されます。

専門化と一般化の詳細については、 [エンティティ](entities) を参照してください。

## 2つのプロパティ

以下の画像では、キャストオブジェクトのプロパティの例を示します。

![オブジェクトのプロパティをキャスト](attachments/object-activities/cast-properties.png)

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

キャストオブジェクトのプロパティペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3つのアクションセクション{#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 オブジェクト名

これはキャストの結果の名前です。 このアクティビティに続くすべてのアクティビティで使用できます。

## 4つの共通セクション{#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}

## 5つの例

例えば、 **Question** オブジェクトには3つの専門分野があります。 特殊なタイプ **MultipleChoiceQuestion** のオブジェクトのみが特別なアクションを実行する必要があります。 これらは、入力タイプ **MultipleChoiceQuestion** を持つサブマイクロフローで行われます。 Since an object of the type **Question** cannot get passed to the sub-microflow, the object first needs to be cast to the object type **MultipleChoiceQuestion**.

![マイクロフローでのキャストの例](attachments/object-activities/cast-example.png)