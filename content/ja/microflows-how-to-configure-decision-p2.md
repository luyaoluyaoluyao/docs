---
title: "ステップ 2: マイクロフローをアプリに埋め込み"
parent: "microflows-how-to-configure-decision"
description: "ここでは、Mendix Studio で決定を構成するプロセスを説明します。"
menu_order: 20
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "決定"
  - "ページ"
---

## 1つの紹介

[前のステップ](microflows-how-to-configure-decision-p1)では、列挙属性型とブール型の属性型を持つマイクロフローと決定を設定しています。 これでページに追加することでマイクロフローを検証できます この方法では、Mendix Studio のページに決定を伴うマイクロフローを追加する方法を説明します。

**以下の方法を教えてくれます。**

* 作成したマイクロフローをページに埋め込みます。

## 2 つの前提条件

このチュートリアルを開始するには、以下の前提条件を満たしていることを確認してください。

* [ステップ 1: ドメイン モデルを構築 & マイクロフローを構成する](microflows-how-to-configure-decision-p1)

## 3 ページにマイクロフローを埋め込み

マイクロフローが作成されたら、それらをページに追加してアプリケーションで実行できます。

### 3.1 マイクロフローの埋め込み 列挙型の属性を持つ決定 {#embedding-decision-enumeration}

エニュメレーションタイプの属性を決定するマイクロフローをページに埋め込むには、次の手順を実行します。

1. 既存の顧客の詳細ページを作成し、 *Customer_details* に名前を付けます。 ページの作成に関する詳細は、 [ページ](/studio/page-editor) の *新規ページ* の作成セクションを参照してください。

2.  In **Toolbox** > **Widgets** > **Data Containers**, find **Data View**.

    ![](attachments/microflows-how-to-configure-decision/data-view.png)

3. **Data View** をページにドラッグ&ドロップします。

4.  データ ビューの **プロパティ** タブで、次の操作を行います:

    1. **Data Source** を **Context に設定します。**
    2. **エンティティ** を **顧客** に設定します。

        ![](attachments/microflows-how-to-configure-decision/data-view-properties.png)

5. In **Toolbox**>**Widgets** >**Buttons** find **Create Object**, drag and drop it inside the data view container (it is named **New** by default).

6. ユーザーが **New** ボタンをクリックしたときに開かれる新しいページを作成します。 作成されたボタンの **プロパティ** タブを開き、次の操作を行います:

    1. **イベント** セクションの **顧客** を **エンティティ** に設定します。
    2. **Select Page** をクリックします。

        ![](attachments/microflows-how-to-configure-decision/create-button-properties.png)

    3. **ページの選択** ダイアログボックスで、右上隅のプラスアイコンをクリックします。
    4. **新規ページの作成** ダイアログボックスで、ページのタイトルを入力します。たとえば、 *新規_顧客* です。
    5. 顧客エンティティに基づいて、 **事前にページの内容を入力する** を選択し、 **作成** をクリックします。

        ![](attachments/microflows-how-to-configure-decision/pre-fill-contents.png)

   顧客詳細ページが生成されます。

7. Return to the **Customer_details** page, and in **Toolbox**>**Widgets** >**Data Containers**, find **List View**, drag and drop it to the page.

8. リスト ビューの **プロパティ** を開き、 **顧客** を **データ ソース**>**エンティティ** として設定します。

9. **Toolbox** > **Building Blocks** > **List** select **List 4**リストビューにドラッグ&ドロップします。

    ![](attachments/microflows-how-to-configure-decision/list-view-list4.png)

10. リストビューから次の要素を削除します。

    1. サブタイトルの**TEXT**ウィジェット。
    2. **イメージ** ウィジェット。

11. **詳細** ボタンの **プロパティ** を開き、次の操作を行います:

    1. Set **Events**>**On Click Action** to **Microflow**.
    2. **Select microflow** and set **Show_grade_specific_page**.

        ![](attachments/microflows-how-to-configure-decision/details-button-microflow.png)

おめでとうございます エンドユーザーが **詳細**をクリックすると、対応する顧客グレードのフォームが開かれます。

[アプリを](/studio/publishing-app) プレビューするか、公開できます。

### 3.2 マイクロフローの埋め込み ブール型の属性を持つ決定を持つ

マイクロフローを決定(ブール型の属性)で埋め込むには、次の手順を実行します。

1. 顧客をブロックとしてマークするオプションを追加する必要があります。 これを行うには、前のセクションで作成された **New_customer** ページを開きます。 詳細については、 [マイクロフローの埋め込み 列挙型の属性を持つ](#embedding-decision-enumeration) を参照してください。

2. In **Toolbox** > **Widgets** > **Input Elements** select **Radio Buttons**, このウィジェットを **データビュー** コンテナにドラッグ&ドロップします。

3.  ラジオボタンの **プロパティ** で、 **Data Source** > **Attribute** をクリックし、 **Blocked Boolean** を選択します。 以下のようにあなたのページに表示されます。

    ![](attachments/microflows-how-to-configure-decision/new-customer-page-blocked-attribute.png)

4. これで、ページにマイクロフローを追加します。 **Order_form_for_bronze_customers ページを開きます。**

5.  In **Toolbox** > **Widgets** > **Data Containers**, find **Data View**.

    ![](attachments/microflows-how-to-configure-decision/data-view.png)

6.  **Data View** をページにドラッグ&ドロップします。

    ![](attachments/microflows-how-to-configure-decision/data-view-select-data-view-source.png)

7.  データ ビューの **プロパティ** で、次の操作を行います:

    1. **Data Source** を **Context に設定します。**
    2. **エンティティ** を **顧客** に設定します。

        ![](attachments/microflows-how-to-configure-decision/data-view-properties.png)

8. In **Toolbox**>**Widgets**>**Buttons**, find the **Call Microflow** button, drag and drop it into the **Data View** container.

    ![](attachments/microflows-how-to-configure-decision/call-microflow-button-in-data-view.png)

9. **Call Microflow** ボタンをクリックして、そのプロパティを表示します。

10. **プロパティ** タブで、 **Customers_status_check microflow** を選択します。

    ![](attachments/microflows-how-to-configure-decision/call-microflow-button-selected-microflow.png)

11. **図表番号** を **マイクロフロー** から **注文**に変更します。

12. Open the page **Order_form_for_silver_customers** and repeat steps 4-11.

13. **Order_form_for_gold_customers** ページを開き、手順 4-11 を繰り返します。

おめでとうございます エンドユーザーが **注文**をクリックすると、ブロックされていない顧客のみが続行できます。 顧客がブロックされると、エラーメッセージが表示されます。

アプリをプレビューおよび/または公開できます。 アプリをプレビューして公開する方法については、 [プレビューする & アプリを公開する](/studio/publishing-app) を参照してください。
