---
title: "Merge の設定 & Object Activities の変更"
category: "マイクロフロー"
menu_order: 70
description: "ここでは、Mendix Studio でマージと変更オブジェクトのアクティビティを設定するプロセスを説明します。"
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "マージ"
  - "表現"
  - "オブジェクトの変更"
---

## 1つの紹介

この方法では、Mendix Studio でマージと変更オブジェクトのアクティビティを設定することで、高度なロジックをマイクロフローに追加する方法を説明します。

マージはフローを結合するために使用されます。 マイクロフローフローを分割して(決定を行うと)、これらの分離されたフローに対して同じ動作を実行する必要があります。 は、マージを使用してこれらの2つ(またはそれ以上)フローを結合できます。 決定の詳細については、 [Decision](/studio8/microflows-decision) を参照してください。

**以下の方法を教えてくれます。**

* 意思決定を含むマイクロフロー内のマージを設定します
* マージ後の変更オブジェクトのアクティビティを設定します

この方法では、次のようなユースケースを説明します。

In [Configure a Decision ステップ1: Build the Domain Model & Configure a Microflow ](microflows-how-to-configure-decision-p1) you have configured the decision to open a specific page based on the customer grade. 顧客の成績が設定されていない場合は、エラーメッセージが表示されます。 決定後に4つのフローがあります

* ブロンズグレードの顧客のためのページを表示
* シルバーグレードの顧客向けページを表示
* ゴールドグレードの顧客のためのページを表示
* 顧客の成績が示されていない場合にエラーメッセージを表示する

この方法では、あなたは青銅、銀の流れをマージします。 顧客が個人的な注文フォームを開いたときに、アクティブなステータスにオブジェクト(顧客)を設定するための金の顧客グレード。

## 2 つの前提条件

このチュートリアルを開始するには、以下の前提条件を満たしていることを確認してください。

* 意思決定でマイクロフローを作成する: [決定を構成する ステップ 1: ドメインモデルを構築 & マイクロフローを構成する](microflows-how-to-configure-decision-p1)

## 3 マージの作成

ゴールド、シルバー、ブロンズの顧客グレードをマイクロフローでマージするには、次の手順に従います。

1. *Show_grade_specific_page* : という名前のマイクロフローを開く

    ![](attachments/microflows-how-to-merge-and-change-object/microflow-without-merge.png)

2. Open the **Toolbox** tab > the **General** section, drag and drop the **Merge** activity before the end event of the flow labelled **Bronze**:

    ![](attachments/microflows-how-to-merge-and-change-object/adding-merge.png)

3. **Gold** と **Bronze** のフローをマージするには、次の操作を行います:<br/>

    a **Gold** というラベルの付いたフローの **終了イベント** を削除します。<br/>

    B **ページを表示** アクティビティにカーソルを合わせます。<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/hover-over.png)<br/>

    C 矢印に変わる点をクリックします。<br/>

    D 矢印をマージにドラッグします。 **ページの表示 アクティビティ** がマージに接続されました:

    ![](attachments/microflows-how-to-merge-and-change-object/connecting-activity-and-merge.png)<br/>

4. **Silver** と書かれたフローについてステップ3を繰り返します。

その結果、3つのフローが1つに統合されます。

![](attachments/microflows-how-to-merge-and-change-object/flows-into-one.png)

## 4 変更オブジェクトの設定

これで、マイクロフローにロジックを追加します。 顧客のステータスをそれぞれの成績にそれぞれアクティブに設定するには、3つのフローを1つにマージしています。 例えば、顧客のステータスをアクティブに設定することができます。 顧客の誰が自分のアカウントを使用しているかを特定し、そうでない人を特定します。

 次の操作を行います:

1.  まず第一に ドメインモデルの **顧客** エンティティに新しい属性を追加し、顧客がアクティブかどうかを示す必要があります。 左メニューバーのドメインモデルアイコンをクリックして、ドメインモデルを開き、次の操作を行います:<br/>

    a **Customer** entity > **New attribute** をクリックしてください。<br/>

    B In the **Create New Attribute** dialog box, set **Name** to *Active* and **Type** to *Boolean*.<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/new-attribute-active.png)<br/>

    C **Create** をクリックします。

2. これで、マイクロフローで新しいアクティビティを設定します。 *Show_grade_specific_page* という名前のマイクロフローを開きます。
3.  **Toolbox** > **Object Activities** で **Change Object** activityを選択します。 マイクロフロー内のマージの後にドラッグ&ドロップします。

     ![](attachments/microflows-how-to-merge-and-change-object/change-object-added.png)

4.  **オブジェクトの変更** アクティビティの **プロパティ** タブで、次の操作を行います:<br/>

    a **変数** を **顧客** に設定します ( **顧客** を編集しようとしているため)。<br/>

    B **Add New Value** をクリックします。<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/change-object-add-new-value.png)<br/>

    C In the **Change value** dialog box, select the attribute named **Active**, then click the **Expression** tab, and type *true*. これは、特定の顧客に対して注文フォームが開かれた後であることを意味します 顧客のステータスは、この顧客が持っているグレードに関係なく、アクティブ(アクティブ=true)に設定されます。<br/>

    ![](attachments/microflows-how-to-merge-and-change-object/change-value-expression-editor.png)<br/>

    D **Add** をクリックして、 **Active** 属性の値の設定を終了します。<br/>

    E. **プロパティ** タブ > **動作** セクションでは、以下を行います: **コミット** オプションを **はい**に設定しておいてください。 (つまり、オブジェクトはさらに変更されず、変更はデータベースに保存されます) 。  <br/>

    ![](attachments/microflows-how-to-merge-and-change-object/change-object-properties.png)

おめでとうございます これで、次のように動作するマイクロフローがあります。

1. 顧客に成績があるかどうかを確認し、以下のいずれかを実行します:<br/> a. 顧客に成績がある場合、対応する顧客グレードの注文フォームが開きます。<br/> b. 顧客に成績がない場合、エラーメッセージが表示されます。<br/>
2. 顧客に成績がある場合、注文フォームが開かれると、顧客のステータスは成績に関係なく有効に設定されます。

アプリをプレビューまたは公開できるようになりました。 アプリをプレビューして公開する方法については、 [プレビューする & アプリを公開する](/studio8/publishing-app) を参照してください。
