---
title: "ドメインモデル"
description: "Mendix Studio でドメインモデルの説明をします。"
category: "データの操作"
menu_order: 10
tags:
  - "スタジオ"
  - "ドメインモデル"
---

## 1つの紹介

Mendix アプリは *モジュール* で構成されています。 モジュールは、アプリの機能を個別のパーツに分割するユニットです。 デフォルトでは、MyFirstModuleと呼ばれるStudioに1つのモジュールがあります。

各モジュールには独自の *ドメインモデル* があります。 ドメインモデルは、アプリケーションドメイン内の情報を抽象的な方法で記述するデータモデルです。 それはあなたのアプリケーションのアーキテクチャの中心です。

Studio のドメイン モデルは、以下のとおりです。

* [エンティティ](#entity-types)
* [関連](domain-models-association-properties)

以下の表のようなCDのコレクションがあるとしましょう。

| タイトル      | アーティスト           |
| --------- | ---------------- |
| 原爆を分解する方法 | U2               |
| Exodus    | ボブ・マーリー & ウェイラーズ |

表の行は CD です。 したがって、 *CD* は *エンティティ* です。 バンドU2の「原子爆弾を解体する方法」のような特定のCDは、 *CD* エンティティの *オブジェクト* です。 つまり、 *オブジェクト* はエンティティの 1 つのインスタンスであるということです。 「タイトル」や「アーティスト」のような特徴は *属性*です。

To view the **Domain Models** of your app in Studio, click the **Domain Models** icon in the left menu bar of Studio.

![](attachments/domain-models/domain-model.png)

ドメインモデルを開くと、すべてのエンティティ、属性、および関連付けの概要が表示されます。 ドメインモデルの複雑さは、アプリケーションの複雑さによって異なります。

![](attachments/domain-models/domain-overview.png)

左上隅の **Auto Arrange** オプションで、関連付けごとに図形を整列します。 関連付けがないエンティティは垂直方向に整列されます。

## 2つのコンポーネント

ドメインモデルには、次のコンポーネントを含めることができます。

* [エンティティ](#entity-types) - 実際のオブジェクトのクラスを表す。エンティティは属性を持つことができる。
    * [属性](#attributes) - エンティティの説明および/または識別
* [Association](#associations) – エンティティ間の関係を説明する

### 2.1 エンティティとそのタイプ {#entity-types}

エンティティは、顧客、請求書、ワークアイテムなどの実際のオブジェクトのクラスを表します。 データベースと並列に描画すると、実体はテーブルになります。

ドメインモデルに異なるタイプのエンティティを追加できます。

* **エンティティ** - 属性、関連性、および実世界のオブジェクトのクラスを表すことができるエンティティ。
* **Image Entity** – 画像を格納できる特別なタイプのエンティティ。 例えば、ページ上では、ユーザーは画像エンティティの助けを借りて画像を表示およびアップロードすることができます。
* **ファイルエンティティ** – ファイルを保存できる特殊なエンティティ。 たとえば、ページ上では、ユーザーはファイルをアップロードおよびダウンロードすることができます(例: ファイルエンティティの助けを借りて文書ドキュメント、pdf、表計算ドキュメントなど。
* **ワークフロー エンティティ** - [ワークフロー](workflows) のコンテキストとして使用される特殊なタイプのエンティティ。
* **外部エンティティ** - 組織でデータハブ機能が有効になっている場合にのみ利用できます。 外部エンティティの詳細については、 [Studio 内のデータハブ](data-hub-in-studio) を参照してください。

### 2.2 エンティティのプロパティ

エンティティには次のプロパティがあります:

* **一般的な** プロパティはエンティティの名前とその [永続性](/refguide/persistability) を定義します:

    * **名前** - エンティティの名前を定義します

    * **Persistable** – defines whether objects of the entity are stored in the database (for more information on persistability, see [Persistability](/refguide/persistability) in the *Studio Pro Guide*)

    ![エンティティの一般プロパティ](attachments/domain-models/entity-general-properties.png)

* **格納された情報** プロパティは、エンティティに関する情報がデータベースに格納されているかどうかを定義します。 情報が保存されていれば、後で取得でき、 [ページ フィルター](data-filters) で使用できます。 たとえば、フィルターを追加して、現在のユーザーが作成したオブジェクトのみを表示できます。

    次のプロパティを切り替えることができます:

    * **ストア '作成者'** - 有効にすると、エンティティを作成したユーザーがデータベースに保存されます

    * **ストア '作成日'** - 有効にすると、エンティティが作成された日時がデータベースに保存されます

    * **'Last Changed by'**– 有効な場合。 エンティティを最後に変更したユーザーはデータベースに保存されます

    * **ストア '最終変更日'** - 有効にすると、エンティティが最後に変更された日時がデータベースに保存されます

        ![エンティティの格納された情報プロパティ](attachments/domain-models/entity-stored-info.png)

        {{% alert type="info" %}}You cannot toggle **Stored Information** properties for Image, File, and Workflow entities.{{% /alert %}}

### 2.3 属性 {#attributes}

属性は、エンティティを記述および/または識別する特性です。 例えば、 *顧客* エンティティは通常、顧客の名前、電子メールアドレス、およびその他の個人情報に対する属性を持ちます。 データベースと並列に描画すると、属性はカラムになります。

属性の型とそれらのプロパティの詳細については、 [属性](domain-models-attributes) を参照してください。

### 2.4 関連 {#associations}

関連付けはエンティティ間の関係を記述します。 ドメイン モデルでは、関連は、2 つのエンティティの間の線によって表されます。 データベースと並列に描画すると、関連付けは外部キーになります。

関連タイプとそれらのプロパティの詳細については、 [Associations](domain-models-association-properties) を参照してください。

## 3 新しいエンティティを追加する {#adding-new-entities}

**ツールボックス**に新しい図形を追加できます。

{{% image_container width="300" %}}![](attachments/domain-models/toolbox-entity.png)
{{% /image_container %}}

エンティティを追加するには、次の操作を行います:

1. ドメインモデルの **Toolbox** タブを開きます。

2. 追加したい図形の種類を選択し、作業領域をドラッグ&ドロップします。

3.  エンティティの名前を入力し、 **Create** をクリックします:

    ![](attachments/domain-models/create-new-entity-dialog.png)

新しいエンティティがドメインモデルに追加されます。

{{% image_container width="250" %}}![](attachments/domain-models/new-entity.png)
{{% /image_container %}}

### 3.1 新しいイメージまたはファイルエンティティの追加 {#adding-image-or-file-entities}

**Toolbox** から新しい図形を追加するときは、すべての種類の図形で動作します。 ドメインモデルに画像とファイルエンティティを追加する特定の方法を使用できます。

例えば、 *Laptop* という名前のエンティティがあり、ラップトップモデルに応じてユーザーに特定の画像を表示できるようになります。 この場合、イメージエンティティを作成する必要があります (例えば、 *Product_Image* という名前)。 しかし、データを取得し、ラップトップのモデルごとに正しい画像を動的に表示するには. *Product_Image* エンティティは、 *ラップトップ* エンティティに特定の接続 (関連) を持つ必要があります。 関連付けとそのタイプの詳細については、 [Associations](domain-models-association-properties) を参照してください。

自動的に関連付けられた新しいイメージ/ファイルエンティティを作成するには、以下の手順に従います。

1. 新しいイメージまたはファイルエンティティに接続する *エンティティ* タイプのエンティティを選択します。

2. **新しい属性** ボタンをクリックします。

3.  **属性の作成** ダイアログボックスで、右下の **画像またはファイル** をクリックします。

    ![画像またはファイルを追加](attachments/domain-models/add-image-or-file.png)

4. **イメージ と ファイル** ダイアログボックスで、タイプまたは図形(イメージまたはファイル)を選択します。

5. **Create New Image/File Entity** ダイアログボックスで、特殊エンティティの名前を指定し、 **Create** をクリックします。

新しいイメージまたはファイルエンティティは、デフォルトの *名前* と *サイズ* 属性と最初のステップで選択したエンティティへの関連付けで作成されます: ![イメージエンティティの例](attachments/domain-models/image-entity-example.png)

## 4 新しい属性を追加する {#adding-new-attributes}

ドメインモードで属性を追加するには、次の操作を行います。

1.  属性を追加するエンティティを持つブロックを選択します。 **新しい属性** オプションが表示されます。

    {{% image_container width="250" %}}![](attachments/domain-models/adding-attribute.png)
    {{% /image_container %}}

2.  **New attribute** をクリックし、 **Name** と **Type** を指定します:

    ![](attachments/domain-models/create-new-attribute-dialog.png)

3. **Create** をクリックします。

新しい属性がエンティティに追加されます。

{{% image_container width="250" %}}![](attachments/domain-models/new-attribute.png)
{{% /image_container %}}

## 5 新しい関連付けの追加

ドメインモデルに関連付けを追加する方法はいくつかあります。 次のいずれかを実行できます:

1. 表示されるドットアイコンをクリックし、次のいずれかを実行します:

    ![](attachments/domain-models/adding-association-dot-icon.png)

    1. 既存のエンティティとの関連付けを作成するには、ドットを2番目のエンティティにドラッグします。

    2.  新しいエンティティとの関連付けを作成するには ドットアイコンをドラッグして、プラスアイコンに変わるまで数秒間保持します。 プラスアイコンを削除すると、最初のエンティティから関連付けを持つ新しいエンティティを作成できます:

        ![](attachments/domain-models/plus-icon.png)

4. 関連付けを追加するエンティティを持つブロックを選択します。

    1.  矢印アイコンをクリック:

        {{% image_container width="250" %}}![](attachments/domain-models/adding-association.png)
        {{% /image_container %}}

    2.  既存のエンティティのリストから新しい関連付けの2番目のエンティティを選択し、 **Select** をクリックします。 ダイアログボックスから関連付けの新しい図形を作成することもできます。

        ![](attachments/domain-models/new-association.png)

        モジュール名は、括弧内のエンティティ名の横に表示されます。

        {{% alert type="info" %}} 別のモジュールからエンティティを選択すると、クロスモジュールの関連付けが作成されます。 詳しい情報については、 [Associations](domain-models-association-properties#cross-module-associations) の *Cross-Module Associations* セクションを参照してください。 現在のモジュールのエンティティが最初にリストされます。
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

* 属性の **名前**
* 属性の [タイプ](domain-models-attributes)

    ![](attachments/domain-models/attribute-properties.png)

属性プロパティを変更するには、ドメインモデルの属性をクリックします。 選択した属性の **プロパティ** タブが自動的に表示されます。

![](attachments/domain-models/selecting-attribute.png)


{{% alert type="info" %}}

**プロパティ** に表示されるフィールドは、属性の種類によって異なる場合があります。

{{% /alert %}}

{{% alert type="info" %}}

*名前* と *サイズ* のプロパティ イメージとファイルのエンティティの属性は読み取り専用で、それらを編集することはできません。

{{% /alert %}}

### 6.3 関連プロパティの指定

関連付けの次のプロパティを管理できます:

*   関連付けの **名前**
*   **関連付けの多重度**
*   オブジェクトの削除動作

詳細については、 [関連](domain-models-association-properties) を参照してください。

関連付けを変更するには、ドメインモデルの行をクリックします。 選択した図形の **プロパティ** タブが自動的に表示されます。

関連タイプが1対多または多対多の場合、対応するアイコンをクリックして方向を変更できます。 For more information, see section [3 Multiplicity](domain-models-association-properties#multiplicity) in *Associations*.

{{% image_container width="350" %}}![](attachments/domain-models/managing-associations.png)
{{% /image_container %}}

## 7 エンティティ、属性、または関連付けを削除しています

エンティティ、属性、または関連付けを削除するには、次の操作を行います。

1. 削除するエンティティ、属性、または関連付けを選択します。

2.  **削除** を押すか、 **プロパティ** タブの下部にある **削除** ボタンをクリックします。

    {{% image_container width="300" %}}![](attachments/domain-models/deletion.png)
    {{% /image_container %}}

{{% alert type="info" %}}

画像とファイルエンティティの *名前* と *サイズ* 属性は削除できません。

{{% /alert %}}

