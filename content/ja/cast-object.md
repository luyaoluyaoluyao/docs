---
title: "キャストオブジェクト"
parent: "object-activity"
---

{{% alert type="info" %}}
この活性は、ナノフローではなく、マイクロフローでのみ使用できます。
{{% /alert %}}

## 1つの紹介

[継承分割](inheritance-split) の後に、キャストオブジェクトアクティビティをマイクロフローで使用して、一般化されたオブジェクトタイプから継承分割のパスの特殊なオブジェクトタイプに変更できます。

専門化と一般化の詳細については、 [エンティティ](entities) を参照してください。

{{% alert type="info" %}}

すべてのアクティビティが共有するプロパティ(例えば、キャプション)については、 [Microflow Element Common Properties](microflow-element-common-properties) を参照してください。 このページでは、アクションに固有のプロパティのみを記述します。

{{% /alert %}}

## 2つの出力プロパティ

### 2.1 変数名

これはキャストの結果の変数名です。 このアクティビティに続くすべてのアクティビティで使用できます。

## 3つの例

例えば、 **Question** オブジェクトには3つの専門分野があります。 特殊なタイプ **MultipleChoiceQuestion** のオブジェクトのみが特別なアクションを実行する必要があります。 これらは、入力タイプ **MultipleChoiceQuestion** を持つサブマイクロフローで行われます。 Since an object of the type **Question** cannot get passed to the sub-microflow, the object first needs to be cast to the object type **MultipleChoiceQuestion**.

![](attachments/819203/cast-example.png)