---
title: "リストとリストアイテムの詳細の設定"
category: "ページ"
description: "Mendix Studio で項目のリストを設定する方法を説明します。"
menu_order: 40
tags:
  - "スタジオ"
  - "ページ"
  - "リスト"
  - "どうやって?"
---

## 1つの紹介

この方法では、項目のリストを構成し、このリストで選択した項目の詳細を表示する方法を説明します。

**以下の方法を教えてくれます。**

* 新しいページを作成
* リストビューの設定
* リストビューで選択した項目の詳細を表示するデータビューを構成します

以下のユースケースについて説明します。

会社の営業担当者は、商談の連絡先のリストを表示したいと考えています。 営業担当者がこのリストの行をクリックすると、該当する商談の連絡先の詳細がリストの横に表示されます。

![](attachments/pages-how-to-configure-list/configured-page.png)

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio8/page-editor) を参照してください。

* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio8/domain-models) を参照してください。

* ドメインモデルが次のように構成されていることを確認してください:

    {{% image_container width="200" %}}![](attachments/pages-how-to-configure-list/domain-model.png){{% /image_container %}}

## 3 マスター詳細ページの追加

商談の連絡先リストとその詳細を持つページをあなたのホームページから開きたいです。 次の操作を行います:

1. ホームページを開き、 **Toolbox** > **ウィジェット** に移動します。

2. **** ボタンを検索し、それをページにドラッグ&ドロップします。

    {{% image_container width="250" %}}![Open Page](attachments/pages-how-to-configure-list/open-page-button.png){{% /image_container %}}

3. ボタンのプロパティを開き、以下の手順に従ってください。

    1. **ページ** をオンクリックアクションとして設定し、 **ページ** プロパティをクリックします。

        {{% image_container width="250" %}}![Button Properties](attachments/pages-how-to-configure-list/button-properties.png){{% /image_container %}}

    2.  **ページの選択** ダイアログボックスで、 **新規ページ** をクリックします。

    3.  **新規ページ** の作成ダイアログボックスで、ページタイトルを入力します。

    4. サイドバーの **マスター詳細** をクリックしてページテンプレートを選択し、 **マスター詳細** を選択します:

        {{% image_container width="550" %}}![](attachments/pages-how-to-configure-list/create-master-detail.png){{% /image_container %}}

    5. **Create** をクリックします。


ページが作成されます。 レスポンシブ(デスクトップ)ビューでは、左側にリストが表示され、右側にリスト項目の詳細が表示されます。

![](attachments/pages-how-to-configure-list/master-details.png)

## 4 リストの設定

ページが作成されます。設定する必要があります。 まず、リストにデータを接続する必要があります。 次の操作を行います:

1. リストビューを選択し、プロパティの **エンティティ** オプションをクリックします。

    {{% image_container width="250" %}}![List View Properties](attachments/pages-how-to-configure-list/list-view-entity.png){{% /image_container %}}

2. **エンティティ** ダイアログボックスで、 **OpportunityContact** を選択し、 **Select** をクリックして選択を確認します。 今リストは **OpportunityContact** エンティティに接続されています。

3. 各企業ごとにレポートの名前を表示するには、次の操作を行います。

    1. リスト ビューで **名前** テキストを選択し、 **プロパティ** タブを開きます。

        {{% image_container width="300" %}}![](attachments/pages-how-to-configure-list/text.png){{% /image_container %}}

    2. **Content** プロパティで、 *Name* を削除し、 **Add attribute** をクリックします:

        {{% image_container width="250" %}}![](attachments/pages-how-to-configure-list/text-content.png){{% /image_container %}}

    3. **属性の選択** ダイアログボックスで、 **名前** を選択し、 **選択** をクリックします。

4. この画像が配置されているリストと列から画像を削除します。 今のように、画像には、表示している商談の連絡先に対応していないユーザーの画像が表示されます。
    {{% image_container width="300" %}}![](attachments/pages-how-to-configure-list/list-with-no-image.png){{% /image_container %}}

5. 新しいページの目的は単にデータを表示することです。 リストビューの上にある **New** ボタンと、配置されているコンテナを削除します:

    {{% image_container width="300" %}}![](attachments/pages-how-to-configure-list/container.png){{% /image_container %}}

今リストビューは、彼らの名前で商談の連絡先のリストを表示します:

{{% image_container width="300" %}}![Configured List](attachments/pages-how-to-configure-list/list-configured.png){{% /image_container %}}

## 5 レポートの詳細設定

次に、リストの横に表示される案件連絡先の詳細を設定する必要があります。 アイデアは、リストから名前を選択すると、選択した連絡先の詳細が表示されます。

マスター詳細ページテンプレートには、リストビューをリッスンする事前設定されたデータビューがあります。 つまり、データ ビューには、リスト ビューで選択した商談の連絡先のデータが表示されます。

次に、 *InspectionReport* エンティティの属性を表示するために、データ ビュー内でウィジェットを設定する必要があります。 言い換えれば、機会の連絡先が持っているすべての詳細を表示することができます。例えば、タイトル、名前、肩書き、電話、電子メールなど。

連絡先が持っているすべての詳細を表示するには、次の操作を行います。

1. Delete the empty column and **Edit**, **Send Email**, and **Delete** buttons inside the data view as you will only display data, not change it:

    ![](attachments/pages-how-to-configure-list/data-view-buttons.png)

2. *User Details* テキスト ウィジェット(データ ビュー 見出しとして表示されます)をダブルクリックし、 *Opportunity Contact Details* に名前を変更します。

3. Open the **Toolbox** and search for **Radio Buttons**, drag and drop it *inside* the data view above the **Name** text box.

    ![](attachments/pages-how-to-configure-list/radio-buttons.png)

4. ラジオボタンのプロパティを開き、 **Data Source** > **Attribute** をクリックしてください。

5. **属性の選択** ダイアログボックスで、 **タイトル** を選択し、 **選択** をクリックします。

    {{% image_container width="350" %}}![](attachments/pages-how-to-configure-list/title.png){{% /image_container %}}

6. **Name** テキストボックスを選択し、プロパティで **Data Source** > **Attribute** をクリックします。

7. **属性の選択** ダイアログボックスで、 **名前** を選択し、 **選択** をクリックします。

8. Repeat steps 6 and 7 to set the **Phone** attribute for the **Phonenumber** text box, the **Email** attribute for the **Email** text box, **DateCreated**  for the **Birthday** text box, and **EstimatedValue** for the **Bio** text box.

    ![](attachments/pages-how-to-configure-list/attributes-replaced.png)

9. 連絡先の職名とステータスに関する情報がありません。 To add the job title information, open the **Toolbox**, search for a **Text Box**, drag and drop it inside the data view below the **Name** text box:

    ![](attachments/pages-how-to-configure-list/job-title-text-box.png)

10. テキストボックスのプロパティを開き、 **Data Source** > **Attribute** をクリックしてください。

11. **属性** を選択ダイアログボックスで、 **ジョブタイトル** を選択し、 **選択**をクリックします。

12. To add the information on the opportunity contact's status, open the **Toolbox**, search for for **Radio Buttons**, drag and drop it inside the data view below the **Estimated Value** text box.

13. ラジオボタンのプロパティを開き、 **Data Source** > **Attribute** をクリックします。

14. **属性の選択** ダイアログボックスで、 **ステータス** を選択し、 **選択** をクリックします。

おめでとうございます 商談の連絡先のリストと選択した連絡先の詳細を表示するページがあります:

![設定されたページ](attachments/pages-how-to-configure-list/configured-page.png)

アプリをプレビューしてページをテストできるようになりました。 ページをプレビューする方法の詳細については、 [プレビュー中 & アプリを公開する](/studio8/publishing-app) を参照してください。

ページの詳細などで作業することもできます。 リストに動的な画像を追加すると、商談の連絡先の名前の横にプロフィール画像が表示されます。 動的画像の詳細については、 [イメージ & ファイル](/studio8/page-editor-widgets-images-and-files) を参照してください。