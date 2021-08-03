---
title: "ステップ 1: ドメイン モデルを構築 & マイクロフローを構成する"
parent: "microflows-how-to-configure-decision"
description: "この方法では、Mendix Studio で決定を設定するプロセスを説明します。"
menu_order: 10
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "決定"
  - "ドメインモデル"
---

## 1つの紹介

この方法では、Mendix Studio のマイクロフローエディタで決定を構成する方法を説明します。

決定とは、アプリロジックの条件をモデル化するために使用されるアクティビティです。 決定に関する詳細については、 [Decision](microflows-decision) を参照してください。

**以下の方法を教えてくれます。**

* 決定を構成するために必要なエンティティと属性を追加
* パラメータまたは属性のブール値型を使用して決定を構成します
* パラメータまたは属性の列挙型を使用して決定を構成します

この方法では、次のようなユースケースを説明します。

オンラインショッピングアプリを持っています。 顧客の詳細、名前、成績、および顧客のステータス (アクティブまたはブロック) を管理できるページを作成します。

また、顧客リストのページを作成します。 このページの特定のボタンをクリックすると、異なるページ(注文フォーム)が異なる成績を持つ顧客に表示されます:ブロンズ、シルバー、ゴールド。

このページから注文することができます。 ただし、ブロックされたユーザーが注文しようとすると、アプリはエラーメッセージを表示し、現在のページを閉じます。

## 2 列挙型の属性による決定の設定

この例では、マイクロフローを作成し、顧客グレードに応じて異なる注文フォームを開く決定を構成します。

この場合、列挙型(定義済みの値のリスト)の属性を持つ決定が必要になります。 属性の型についての詳細は、 [属性タイプ](domain-models-attributes) を参照してください。

### 2.1 ドメインモデルにエンティティと属性を追加する

アプリは顧客の成績に応じて対応するページを開きます。 このためには、最初に新しいエンティティと新しい属性を作成する必要があります。 新しいエンティティと属性を作成するには、次の操作を行います。

1. [ドメイン モデル](domain-models) を開きます。
2. エンティティ *顧客* を作成する。 For more information on how to create the entity, see section [3 Adding New Entities](domain-models) in *Domain Models Overview*.
3.  For the **Customer** entity, create attribute (for more information on how to create the attribute, see section [4 Adding New Attributes](domain-models)) and do the following:<br /> a. 属性 **名前**を*成績*に設定します。<br /> b. [****](domain-models-attributes)を**列挙値**に設定します。<br /> c. **Select enumeration**をクリックして新しい列挙を作成します。<br />d. **Select enumeration** ダイアログウィンドウで、 **New**.<br/> eをクリックします。 In the **Create new enumeration** dialog window, click **Add Item** (*Grade* is filled out automatically for the **Name**).<br />

    ![](attachments/microflows-how-to-configure-decision/new-enumeration-add-item.png) <br />

    F *Bronze* を**キャプション** に入力します（**Name** は自動的に *Bronze* として記入されます）。<br />

    ![](attachments/microflows-how-to-configure-decision/new-enumeration-add-item-bronze.png)<br />

    G **アイテム追加** をクリックし、上記のステップを繰り返して、**シルバー**と**ゴールド**の成績を作成します。<br /> h. **Create**をクリックしてダイアログウィンドウを閉じ、新しい属性を作成します。

    ![](attachments/microflows-how-to-configure-decision/new-enumeration-bronze-silver-gold.png)

新しい属性が作成されます。

![](attachments/microflows-how-to-configure-decision/grade-attribute.png)

### 2.2 マイクロフローの設定

列挙型の属性またはパラメータを使用して決定を構成するには、次の手順に従います。

1. [新しいマイクロフロー](microflows) を作成し、例えば、 *Show_grade_specific_page* という名前を付けます。
2. **Toolbox** タブで **Decision**を選択し、それをマイクロフローにドラッグ&ドロップします。
3.  決定を正しく設定するには、パラメータを渡す必要があります。  **Toolbox**で **Parameter** を選択し、それをマイクロフローにドラッグ&ドロップします。

    ![](attachments/microflows-how-to-configure-decision/microflow-not-set-parameter.png)

4.  この例では、ロジックを追加しているページで選択されている単一の顧客に適用する必要があります。 したがって、パラメータとして顧客を追加する必要があります。 **パラメータ**:<br /> a. **Data Type** に **Object**を設定します。<br /> b. **エンティティ** を **顧客** に設定します。

    ![](attachments/microflows-how-to-configure-decision/parameter-properties.png)

5. 決定の **プロパティ** で、 **条件の設定** フィールドをクリックします。
6.  **Configure condition** ポップアップウィンドウで、条件が基になる属性を選択する必要があります。 そのため、 **変数/属性** タブをクリックし、 **** 条件を選択し、 **保存** をクリックします。

    ![](attachments/microflows-how-to-configure-decision/configure-condition-grade.png)

    図表番号 **** は、属性名に基づいて決定がどの条件に基づいて決定されるかを示す自動的に決定に追加されます。
7.  **成績** 属性の値ごとに異なるロジックを追加する必要があります。 これを行うには、 **プロパティ** タブで、以下を行う決定の場合を設定します:<br /> a. **(未設定)** フィールドで **編集** を選択します。<br />

    ![](attachments/microflows-how-to-configure-decision/setting-cases.png) <br/>

    B **** ドロップダウンメニューの **ブロンズ** を設定します。<br /> c. **Go back** アイコンをクリックして、決定プロパティに戻ります。<br />

    ![](attachments/microflows-how-to-configure-decision/go-back-button.png) <br/>

    D **ケース** セクションの **新規ケースの追加** をクリックします。<br /> e. Repeat steps b-d to add all possible cases: **Silver**, **Gold**, and **Empty** (a case when the customer's grade is not set).

    ![](attachments/microflows-how-to-configure-decision/possible-cases.png)

8. To open a corresponding order form (page) for customers with the bronze grade, select **Show Page** in the **Toolbox**, drag and drop it to flow labelled **Bronze** in the microflow.
9.  **Show Page** アクティビティのプロパティを開き、以下の操作を行います:<br /> a. **ページの選択** フィールドをクリックします。<br /> b. In the **Select Page** dialog window, click **New page**, and [create a page](page-editor) for customer grade **Bronze**. **メモ** ページを作成すると、自動的に **フィールド** に追加されます。<br />

    ![](attachments/microflows-how-to-configure-decision/show-page-select-page.png) <br />

    C **Data Source**>**Object to Pass**, set **Customer** to get the data on customers and their grade.
10. シルバーとゴールドのグレードのお客様については、ステップ8-9を繰り返し、シルバーとゴールドのお客様用の注文フォームページを作成します。
11. 成績が示されていないお客様には、エラーメッセージが表示されます。 To do so, select **Show Message** in the **Toolbox**, and add it to the flow labelled **(empty)** in the microflow.

    ![](attachments/microflows-how-to-configure-decision/microflow-empty-flow-show-message.png)

12. **プロパティ** タブの **メッセージ** アクティビティを表示するには、以下を行います:<br /> a. **エラー** をメッセージの種類として選択します。<br /> b. Fill out the **Template** that will be shown to users when this message pops up (in this example: Please select the customer grade first).<br /> c. **ブロック** プロパティを有効にしておくと、ポップアップウィンドウが閉じられるまでユーザーが作業を継続できなくなります。  
    ![](attachments/microflows-how-to-configure-decision/empty-customer-grade-message.png)

おめでとうございます 異なる成績を持つ顧客のために異なる注文フォームを開くマイクロフローを作成しました。 または成績がない場合にエラーメッセージを表示します．

ページに追加してマイクロフローをテストしたい場合。 を参照してください [決定を構成する ステップ2: アプリケーションにマイクロフローを埋め込む](microflows-how-to-configure-decision-p2)。

## 3 ブール型の属性による決定の設定

この例では、マイクロフローを作成し、ブロックされた顧客が注文するのを防ぐように決定を構成します。 顧客をブロックする理由は、顧客のクレジットスコアが低すぎる、またはパスワードの有効期限が切れていることです。

この場合、ブール型の属性を持つ判断が必要になります (true または false)。 属性のタイプについての詳細は、 [属性タイプ](domain-models-attributes) を参照してください。

### 3.1 ドメインモデルにエンティティと属性を追加する

顧客のステータスを確認するため、エンティティに対応する属性を最初に作成する必要があります。 このために、以下の操作を行います。

1. [ドメイン モデル](domain-models) を開きます。
2.  顧客エンティティの場合、属性を作成します(属性の作成方法の詳細については、以下を参照してください)。 See section [3 Adding New Attributes](domain-models)), and do the following: <br /> a. *ブロックされた* に名前を設定します。 <br /> b. [**Type**](domain-models-attributes) を **Boolean** に設定します。 <br /> c. **Create** をクリックします。

    ![](attachments/microflows-how-to-configure-decision/new-attribute-create-dialog.png)

**顧客** エンティティの新しい属性が作成されます。

![](attachments/microflows-how-to-configure-decision/blocked-attribute.png)

### 3.2 マイクロフローの設定

ブール型の属性を使用して決定を構成するには、次の手順に従います。

1. [新しいマイクロフロー](microflows) を作成し、名前を付けます。例えば *Customer_status_check*.
2. **ツールバー** タブで、意思決定を選択し、マイクロフローにドラッグ&ドロップします。

3.  決定を構成するにはパラメータを渡す必要があります。 **Toolbox** タブで **Parameter**を選択し、それをマイクロフローにドラッグ&ドロップします。

    ![](attachments/microflows-how-to-configure-decision/microflow-not-set-parameter.png)

4.  この例では、ロジックは顧客のステータスに適用されます。 したがって、パラメータとして顧客を追加する必要があります。 **パラメーター** の **プロパティ**タブで、以下の操作を行います:<br /> a. **Data Type** に **Object** <br /> b. **エンティティ** を **顧客** に設定します。

    ![](attachments/microflows-how-to-configure-decision/parameter-properties.png)

5. 決定をクリックし、 **プロパティ** タブで **条件を設定** フィールドをクリックします。
6.  **Configure condition** ポップアップウィンドウで、条件が基になる属性を選択する必要があります。 So, in the **Configure condition** pop-up window, click  the **Variables/Attributes** tab, select **Blocked Boolean** attribute of the **Customer**, and click **Save**.

    ![](attachments/microflows-how-to-configure-decision/configure-condition-pop-up.png)

7.  ケース **true** と **false** は、意思決定のプロパティに対して自動的に設定され、対応するフローがマイクロフローに追加されます。 図表番号 **がブロックされましたか?** は属性名に従って自動的に追加されます。

    ![](attachments/microflows-how-to-configure-decision/true-false-flows-microflow.png)

8. To show an error message to the blocked customers, select **Show message** in the **Toolbox**, and add it to the **true** flow in the microflow.
9.  **プロパティ** タブの **メッセージ** アクティビティを表示するには、以下を行います:<br/> a. **エラー** をメッセージの種類として選択します。<br/> b. このメッセージが表示されたときに表示される **テンプレート** を入力してください (この例では、申し訳ありません)。 命令を続けることはできません) <br/> c. **ブロック** プロパティを有効にしておくと、ポップアップウィンドウが閉じられるまでユーザーが作業を継続できなくなります。

    ![](attachments/microflows-how-to-configure-decision/show-message-properties-true-flow.png)

10. **Toolbox** タブで **ページを閉じる** アクティビティを選択し、それをマイクロフローにドラッグ&ドロップします。

    ![](attachments/microflows-how-to-configure-decision/microflow-blocked-completed.png)

おめでとうございます これで、エラーメッセージを表示し、顧客がブロックされている場合は現在のページを閉じるマイクロフローを作成しました。

ページにマイクロフローを埋め込む場合は、 [ステップ2:マイクロフローをアプリに埋め込む](microflows-how-to-configure-decision-p2) を参照してください。
