---
title: "列挙型"
parent: "domain-models"
description: "Mendix Studioで列挙について説明します。"
tags:
  - "スタジオ"
  - "ドメインモデル"
  - "属性"
  - "列挙型"
---

## 1つの紹介

このドキュメントでは、Mendix Studio の列挙について説明します。 列挙型は、1 つ以上の項目(値)のリストです。 各アイテムは一つのオプションを表します。 たとえば、顧客に *ブロンズ*、 *シルバー*、 *ゴールド* のグレードを割り当てることができます。 したがって、 *顧客グレード* は列挙、 *ブロンズ*、 *シルバー*、 *ゴールド* は列挙項目です。  アイテムの詳細については、 [列挙項目](#enumeration-items) セクションを参照してください。

*列挙型* の属性を作成するとき、既存の列挙型を割り当てるか、新しい列挙型を作成します。 列挙型の属性のプロパティの詳細については、 [属性](domain-models-attributes#attribute-properties) の *属性*セクションを参照してください。

## 列挙項目 2 {#enumeration-items}

列挙は、列挙項目または値で構成されます。 各アイテムはオプションのいずれかを表します。

列挙は *初期化されていない状態* を表すこともできます。 たとえば、顧客に成績を割り当てない場合、成績ステータスは *空*です。

## 3つの基本アクション

enumeration は、enumeration 型の属性をドメインモデルに追加するときに構成されます。 [新しい列挙の作成](#create-new-enumeration) または [既存の列挙の選択](#select-existing-enumeration) を選択することができます。

### 3.1 新しい列挙の作成 {#create-new-enumeration}

新しい列挙を作成するには、次の手順を実行します。

1. [ドメイン モデル](domain-models) を開きます。

2. 属性を作成するエンティティを選択します。 エンティティの作成方法については、 [ドメインモデルの概要](domain-models#adding-new-entities) の *新規エンティティの追加* セクションを参照してください。

3.  列挙型の新しい属性を作成するには、 **新しい属性** をクリックし、次の操作を行います:<br /> a. 属性 **名前** を設定します。 この例では、属性の名前は *Grade*です。<br /> b. [Type](domain-models-attributes)に**列挙値**を設定します。<br /> c. **Select enumeration**.<br />d. **列挙の選択** ダイアログボックスで、右上隅のプラスアイコンをクリックします。<br/> e. In the **Create new enumeration** dialog box, click **Add Item** to add possible options of the enumeration (**Name** is filled out automatically and is the same as the attribute name).<br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item.png)<br />

    F **図表番号** の名前を入力します(**名前** が自動的に入力されます)。 以下の例では、  *ブロンズ*に記入する必要があります。 ブロンズ、シルバー、ゴールドの3つの可能性のある項目の1つとして挙げられます。 <br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item-bronze.png)<br />

    G **Add Item** をクリックし、上記の手順を繰り返して、他の列挙項目を作成します。<br /> h. **Create**をクリックしてダイアログボックスを閉じ、新しい属性を作成します。

    ![](attachments/domain-models-enumeration/new-enumeration-bronze-silver-gold.png)

属性と列挙項目が作成されます。

### 3.2 列挙を選択する {#select-existing-enumeration}

列挙型の属性に既存の列挙を設定することもできます。 次の操作を行います:

1. [ドメイン モデル](domain-models) を開きます。

2. 属性を作成するエンティティを選択します。 For more information on how to create the entity, see section [3 Adding New Entities](domain-models#adding-new-entities) in *Domain Models Overview*.

3.  列挙型の新しい属性を作成するには、 **新規属性** をクリックして、次の操作を行います:<br />

    a 属性 **名前** を設定します。 この例では、属性の名前は *Grade*です。<br /> b. [Type](domain-models-attributes)に**列挙値**を設定します。<br /> c. **Select enumeration** をクリックします。<br />

    ![](attachments/domain-models-enumeration/new-attribute-select-enumeration.png) <br/>

    D **列挙の選択** ダイアログボックスでは、既存の列挙がリストに表示されます。 使用したいものをクリックし、 **Select** をクリックします。<br />

    ![](attachments/domain-models-enumeration/selecting-existing-enumeration.png)

既存の列挙は列挙型の属性に選択されます。

### 3.3 列挙のコピーと貼り付け

他のStudioアプリにエニュメレーションをコピー&ペーストできます。 以下の手順に従ってください。

1. [ドメイン モデル](domain-models) を開きます。

2. 列挙型の属性を選択し、そのプロパティの **列挙値** をクリックします。

3. **列挙の選択** ダイアログボックスで、コピーする列挙を選択し、省略記号アイコンをクリックします。

4. ドロップダウンメニューから **Copy to clipboard** オプションを選択します。 ![列挙をコピー](attachments/domain-models-enumeration/copy-to-clipboard.png)

5. 別のモジュールまたはStudioアプリを開き、ドメインモデルに移動し、 <kbd>Ctrl</kbd> + <kbd>V</kbd> を押します。

列挙が貼り付けられます。 Studio のコピー/貼り付け機能の詳細については、 [一般情報](general#copy-paste-documents) の *コピー/貼り付けページ、マイクロフロー、および列挙* セクションを参照してください。

### 3.4 列挙型を複製

列挙を複製するには、以下の手順に従ってください:

1. [ドメイン モデル](domain-models) を開きます。

2. 列挙型の属性を選択し、そのプロパティの **列挙値** をクリックします。

3. **列挙の選択** ダイアログボックスで、複製する列挙を選択し、省略記号アイコンをクリックします。

4.  ドロップダウンメニューで **複製** オプションを選択します。

    ![列挙型の重複](attachments/domain-models-enumeration/duplicate.png)

5. ダイアログボックスを閉じます。

列挙は重複しています。

#### 3.5 列挙の削除

列挙を削除するには、以下の手順に従ってください:

1. [ドメイン モデル](domain-models) を開きます。

2. 列挙型の属性を選択し、そのプロパティの **列挙値** をクリックします。

3. **列挙の選択** ダイアログボックスで、削除する列挙を選択し、省略記号アイコンをクリックします。

4. ドロップダウンメニューから **削除** オプションを選択します。

    ![列挙を削除](attachments/domain-models-enumeration/delete-enumeration.png)

5. 選択を確認し、ダイアログボックスを閉じます。

列挙が削除されました。

## 4 続きを読む

* [ドメインモデル](domain-models)
* [属性](domain-models-attributes) 
