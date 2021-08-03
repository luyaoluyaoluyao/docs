---
title: "ドメインモデル"
description: "Mendix Studio でドメインモデルの説明をします。"
menu_order: 20
tags:
  - "スタジオ"
  - "ドメインモデル"
---

## 1つの紹介

ドメインモデルは、アプリケーションドメイン内の情報を抽象的な方法で記述するデータモデルです。 それはあなたのアプリケーションのアーキテクチャの中心です。

Studio のドメイン モデルは、以下のとおりです。

* [エンティティ](#entity)
* [関連](domain-models-association-properties)

{{% alert type="info" %}}

以下の表のようなCDのコレクションがあるとしましょう。

| タイトル      | アーティスト           |
| --------- | ---------------- |
| 原爆を分解する方法 | U2               |
| Exodus    | ボブ・マーリー & ウェイラーズ |

表の行は CD です。 2つの行の型は "CD" で、これがエンティティ名です。 バンドU2の「原子爆弾を解体する方法」のような特定のCDは、「CD」エンティティのオブジェクトと呼ばれています。 「タイトル」や「アーティスト」のような特性を属性と呼びます。

{{% /alert %}}

To view the **Domain Models** of your app in Studio, click the **Domain Models** icon in the left menu bar of Studio.

{{% image_container width="350" %}}![](attachments/domain-models/domain-model.png)
{{% /image_container %}}

ドメインモデルを開くと、エンティティのすべてのエンティティ、属性、および関連付けの概要が表示されます。

![](attachments/domain-models/domain-overview.png)

{{% alert type="info" %}}

ドメインモデルの複雑さは、アプリケーションの複雑さによって異なります。

{{% /alert %}}

ドメインモデルグループの上部にある **Auto Arrange** オプションを使用し、関連付けごとに図形を整列します。 関連付けがないエンティティは垂直方向に整列されます。

## 2つのコンポーネント

| ドメインモデルコンポーネント                               | 説明                                                                                                                     | プロパティー                                                                                                                                                   |
| -------------------------------------------- |:---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| エンティティ<a name="entity"></a>              | エンティティは、顧客、請求書、ワークアイテムなどの実際のオブジェクトのクラスを表します。 <br />データベースと並列に描画すると、実体はテーブルになります。                                 | <br />[の永続性](/refguide/persistability) の名前                                                                                                         |
| [属性](domain-models-attributes)               | 属性は、エンティティを記述および/または識別する特性です。 例えば、 *顧客* エンティティは通常、顧客の名前、電子メールアドレス、およびその他の個人情報に対する属性を持ちます。 データベースと並列に描画すると、属性はカラムになります。 | 名前<br />タイプ                                                                                                                                        |
| [関連付け](domain-models-association-properties) | 関連付けはエンティティ間の関係を記述します。 ドメイン モデルでは、関連は、2 つのエンティティ間の行/矢印で表されます。 データベースと並列に描画すると、関連付けは外部キーになります。                          | 名前<br />[Multiplicity](domain-models-association-properties#multiplicity)<br />[動作を削除](domain-models-association-properties#delete-behavior) |

For examples and more technical details, see [Domain Model](/refguide/domain-model), [Entities](/refguide/entities), [Attributes](/refguide/attributes), and [Associations](/refguide/associations) in the *Studio Pro Guide*.

## 3 新しいエンティティを追加する {#adding-new-entities}

**ツールボックス**に新しい図形を追加できます。

{{% image_container width="250" %}}![](attachments/domain-models/toolbox-entity.png)
{{% /image_container %}}

エンティティを追加するには、次の操作を行います:

1. ドメインモデルの **Toolbox** タブを開きます。

2. **新しいエンティティ** を作業領域にドラッグ＆ドロップします。

3.  名前を入力し、 **Create** をクリックします:

    ![](attachments/domain-models/create-new-entity-dialog.png)

新しいエンティティがドメインモデルに追加されます。

{{% image_container width="250" %}}![](attachments/domain-models/new-entity.png)
{{% /image_container %}}

## 4 新しい属性を追加する {#adding-new-attributes}

ドメインモードで属性を追加するには、次の操作を行います。

1.  属性を追加したいブロックを選択します。 **新しい属性** オプションが表示されます。

    {{% image_container width="250" %}}![](attachments/domain-models/adding-attribute.png)
    {{% /image_container %}}

2.  **New attribute** をクリックし、 **Name** と **Type** を指定します:

    ![](attachments/domain-models/create-new-attribute-dialog.png)

3. **Create** をクリックします。

新しい属性がエンティティに追加されました。

{{% image_container width="250" %}}![](attachments/domain-models/new-attribute.png)
{{% /image_container %}}

## 5 新しい関連付けの追加

ドメインモデルに関連付けを追加するには、次の操作を行います。

1. 関連付けを追加するエンティティを持つブロックを選択します。
2.  表示される矢印アイコンをクリックします。

    {{% image_container width="250" %}}![](attachments/domain-models/adding-association.png)
    {{% /image_container %}}

3.  既存のエンティティのリストから新しい関連付けの2番目のエンティティを選択し、 **Select** をクリックします。 ダイアログボックスから関連付けの新しい図形を作成することもできます。

    ![](attachments/domain-models/new-association.png)

{{% alert type="info" %}}

モジュールは、括弧内のエンティティ名の横に表示されます。 別のモジュールから図形を選択すると、クロスモジュールの関連付けが作成されます。 詳しい情報については、 [関連プロパティ](domain-models-association-properties#cross-module-associations) の *セクション* を参照してください。 現在のモジュールのエンティティが最初にリストされます。

{{% /alert %}}

## 6プロパティの指定

ドメイン モデルでは、 **プロパティ** タブで、エンティティ、属性、および関連付けのプロパティを管理できます。

タブの下部に **Delete** ボタンがあります。

### 6.1 エンティティプロパティの指定

エンティティの次のプロパティを管理できます:

* エンティティの **名前**

* [エンティティの永続性](/refguide/persistability)

    ![](attachments/domain-models/entity-properties.png)

エンティティプロパティを変更するには、ドメインモデル内のエンティティをクリックします。 選択した図形の **プロパティ** タブが自動的に表示されます。

### 6.2 属性プロパティの指定

属性の次のプロパティを管理できます。

*   属性の **名前**
*   属性の [****と入力](domain-models-attributes)

    ![](attachments/domain-models/attribute-properties.png)

属性プロパティを変更するには、ドメインモデルの属性をクリックします。 選択した属性の **プロパティ** タブが自動的に表示されます。

![](attachments/domain-models/selecting-attribute.png)


{{% alert type="info" %}}

**プロパティ** に表示されるフィールドは、属性の種類によって異なる場合があります。

{{% /alert %}}

### 6.3 関連プロパティの指定

関連付けの次のプロパティを管理できます:

*   関連付けの **名前**
*   **関連付けの多重度**
*   オブジェクトの削除動作

詳細については、 [関連プロパティ](domain-models-association-properties) を参照してください。

関連付けを変更するには、ドメインモデルの行をクリックします。 選択した図形の **プロパティ** タブが自動的に表示されます。

関連タイプが1対多または多対多の場合、対応するアイコンをクリックして方向を変更できます。 詳細については、 [関連プロパティ](domain-models-association-properties#multiplicity) の *セクション* を参照してください。

{{% image_container width="350" %}}![](attachments/domain-models/managing-associations.png)
{{% /image_container %}}

## 7エンティティ、属性、関連付けを削除しています

エンティティ、属性、または関連付けを削除するには、次の操作を行います。

1. 削除するエンティティ、属性、または関連付けを選択します。

2.  **削除** を押すか、 **プロパティ** タブの下部にある **削除** ボタンをクリックします。

    {{% image_container width="300" %}}![](attachments/domain-models/deletion.png)
    {{% /image_container %}}

## 8 続きを読む

* [属性タイプ](domain-models-attributes)
* [関連のプロパティ](domain-models-association-properties) 
