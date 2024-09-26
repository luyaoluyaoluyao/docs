---
title: "列挙型"
category: "ドメインモデル"
description: "Mendix Studio で列挙型の属性を説明します。"
tags:
  - "スタジオ"
  - "ドメインモデル"
  - "属性"
  - "属性タイプ"
  - "列挙型"
---

## 1つの紹介

このドキュメントでは、Mendix Studio の列挙属性タイプについて説明します。 列挙型は、定義済みのオプションのリストを持つ属性の型です。 列挙項目(値)が1つ以上あります。 各アイテムは一つのオプションを表します。 たとえば、顧客グレードのステータスはブロンズ、シルバー、ゴールドです。 従って、顧客グレードの列挙は3つの項目で構成されます: *Bronze*, *Silver*, *Gold*.  詳細については、 [列挙項目](#enumeration-items) を参照してください。

## 列挙項目 2 {#enumeration-items}

列挙は、列挙項目または値で構成されます。 各アイテムはオプションのいずれかを表します。

列挙型の属性は、初期化されていない状態を表すこともできます。 たとえば、顧客に成績を割り当てない場合、成績ステータスは *空*です。

## 3つの基本アクション

enumeration は、enumeration 型の属性をドメインモデルに追加するときに構成されます。 [新しい列挙の作成](#create-new-enumeration) または [既存の列挙の選択](#select-existing-enumeration) を選択することができます。

### 3.1 新しい列挙の作成 {#create-new-enumeration}

新しい列挙を作成するには、次の手順を実行します。

1. [ドメイン モデル](domain-models) を開きます。

2. 属性を作成するエンティティを選択します。 For more information on how to create the entity, see section [3 Adding New Entities](domain-models#adding-new-entities) in *Domain Models Overview*.

3.  列挙型の新しい属性を作成するには、 **新しい属性** をクリックし、次の操作を行います:<br /> a. 属性 **名前** を設定します。 この例では、属性の名前は *Grade*です。<br /> b. [****](domain-models-attributes)を**列挙値**に設定します。<br /> c. **Select enumeration**をクリックして新しい列挙を作成します。<br />d. **Select enumeration** ダイアログウィンドウで、 **New**.<br/> eをクリックします。 In the **Create new enumeration** dialog window, click **Add Item** to add possible options of the enumeration (**Name** is filled out automatically and is the same as the attribute name).<br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item.png)<br />

    F **図表番号** の名前を入力します(**名前** が自動的に入力されます)。 この例では、最初に  *Bronze*に記入し、列挙の3つの可能な項目の1つとして: Bronze, Silver, Gold. <br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item-bronze.png)<br />

    G **Add Item** をクリックし、上記の手順を繰り返して、他の列挙項目を作成します。<br /> h. **Create**をクリックしてダイアログウィンドウを閉じ、新しい属性を作成します。

    ![](attachments/domain-models-enumeration/new-enumeration-bronze-silver-gold.png)

属性と列挙項目が作成されます。

### 3.2 既存の列挙を選択する {#select-existing-enumeration}

列挙型の属性に既存の列挙を設定することもできます。 次の操作を行います:

1. [ドメイン モデル](domain-models) を開きます。

2. 属性を作成するエンティティを選択します。 For more information on how to create the entity, see section [3 Adding New Entities](domain-models#adding-new-entities) in *Domain Models Overview*.

3.  列挙型の新しい属性を作成するには、 **新規属性** をクリックして、次の操作を行います:<br />

    a 属性 **名前** を設定します。 この例では、属性の名前は *Grade*です。<br /> b. [****](domain-models-attributes)を**列挙値**に設定します。<br /> c. **Select enumeration**をクリックして新しい列挙を作成します。<br />

    ![](attachments/domain-models-enumeration/new-attribute-select-enumeration.png) <br/>

    D **列挙の選択** ダイアログウィンドウでは、既存の列挙がリストに表示されます。 使用したいものをクリックし、 **Select** をクリックします。<br />

    ![](attachments/domain-models-enumeration/selecting-existing-enumeration.png)

既存の列挙は列挙型の属性に選択されます。

## 4つのプロパティ

列挙型の属性のプロパティの詳細については、 [属性タイプ](domain-models-attributes#attribute-properties) のセクション *属性タイプ* を参照してください。

## 5 続きを読む

* [ドメインモデル](domain-models)
* [属性タイプ](domain-models-attributes) 
