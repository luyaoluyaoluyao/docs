---
title: "フォームを設定し、関連するアイテムを表示します"
category: "ページ"
description: "Mendix Studio で項目のリストを設定する方法を説明します。"
menu_order: 10
tags:
  - "スタジオ"
  - "ページ"
  - "リスト"
  - "どうやって?"
---

## 1つの紹介

この方法では、フォームを使用してページを構成する方法と、同じページにこのフォームに関連するアイテムを表示する方法を説明します。 たとえば、このレポートに関連付けられたレポートとチェックリストを表示します。

**以下の方法を教えてくれます。**

* フォームの設定 (データビュー)
* このフォームに関連するアイテムをテーブルに表示

以下のユースケースについて説明します。

あなたの会社の HSE 部門には、以下の検査レポートがあります。

![](attachments/pages-how-to-configure-form/report-example.png)

あなたの会社は異なった会社に旅行し、これらの会社が安全規則に準拠しているかどうか点検する検査官によって使用される適用を有する。 彼らは彼らの名前、会社名、サイトの場所、検査が行われた日時を記入します。 査察に出席していた警視のフルネームと同様に

検査者はまた、安全検査 *チェックリスト* を持っています。 このチェックリストに基づいて、検査官は会社が検査に合格したかどうかを評価します。 以下の *質問* の要件が満たされているかどうかを確認する必要があります。

* 緊急連絡先のポスターが表示される場合
* 安全訓練が定期的に行われる場合
* 救急キットが利用可能な場合
* 緊急事態が存在し、ブロックされていない場合。

上記のいずれかの要件が満たされていない場合、次回検査中に検査官は安全違反が修正された日付を示します。

アプリにはすでにすべての検査レポートのリストが含まれています:

{{% image_container width="600" %}}![](attachments/pages-how-to-configure-form/inspection-report-list.png){{% /image_container %}}

このリストの **詳細** ボタンをクリックすると、選択したレポートの詳細と、このレポートに関連するチェックリストの質問のあるテーブルが表示されます。 また、新しいチェックリストをテーブルに追加したり、既存のチェックリストを編集したりすることもできます。

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio8/page-editor) を参照してください。

* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio8/domain-models) を参照してください。

* ドメインモデルが次のように構成されていることを確認してください:

    {{% image_container width="200" %}}![Domain Model](attachments/pages-how-to-configure-form/domain-model.png){{% /image_container %}}

    * **Question** 属性を以下の列挙として設定していることを確認してください:

        {{% image_container width="550" %}}![](attachments/pages-how-to-configure-form/enumeration.png){{% /image_container %}}

* アプリに検査レポートリストと **詳細** ボタンが含まれていることを確認してください。

    {{% image_container width="600" %}}![](attachments/pages-how-to-configure-form/inspection-report-list.png){{% /image_container %}}

## 3 フォームでページを追加する

検査レポート一覧の **詳細** ボタンをクリックすると、検査レポートの詳細が記載されたページが開きます。 ページを構成するには、次の手順を実行します。

1. **詳細** ボタンをクリックし、プロパティに移動します。

2. **ページ** をオンクリックアクションとして設定し、 **ページ** プロパティをクリックします。

    {{% image_container width="250" %}}![Button Properties](attachments/pages-how-to-configure-form/button-properties.png){{% /image_container %}}

3.  **ページの選択** ダイアログボックスで、 **新規ページ** をクリックします。

1.  In the **Create new page** dialog box, set the **Title** to **Reports_Details**, and set the **Layout** to **Atlas_Default**.

2.  **InspectionReport エンティティ** オプションに基づく事前入力ページの内容がオンになっているため、ページテンプレート(フォーム)が自動的に選択されます。 **フォームを垂直に選択**:

    {{% image_container width="550" %}}![Create New Page](attachments/pages-how-to-configure-form/create-new-page.png){{% /image_container %}}

3. **Create** をクリックします。

3. フォーム(データビュー)のページが作成されます。 ただし、データビューのデータソースが **List ウィジェット**に自動的に設定されており、それを変更する必要があります。 データ ビューを選択し、そのプロパティに移動します。

1. データ ソースを **リスト ウィジェット** から **コンテキスト** に変更します。

2. **エンティティ** プロパティをクリックし、 **検査レポート** エンティティを設定します。

      {{% image_container width="250" %}}![](attachments/pages-how-to-configure-form/data-view-source.png){{% /image_container %}}

ページのフォームが設定されています:
{{% image_container width="600" %}}![](attachments/pages-how-to-configure-form/data-view-configured.png){{% /image_container %}}

## 4チェックリストの質問を表示

インスペクターには *質問* のリストがあり、 **はい** または **いいえ** 会社が要件を満たしているかどうかを示します。 安全訓練を定期的に行っているかどうかなど チェックリストの質問と検査レポートの下に結果が表示されます:

{{% image_container width="550" %}}

![](attachments/pages-how-to-configure-form/inspection-report-example.png)

{{% /image_container %}}

チェックリストの詳細を表に表示するには、データ グリッドを追加できます。 データ ビューを ** 内に配置することが重要です。この方法で、データ グリッドは、すべてのレポートに追加されたすべてのチェックリスト項目を表示するのではなく、現在のレポートに関連付けられているチェックリスト項目にのみアクセスして表示します。 これは、この場合、 *Checklist_InspectionReport* と呼ばれるデータグリッドが関連付けを介してデータを取得することを意味します。

以下の手順に従ってください。

1. Open **Toolbox** > **Data Containers**.

2. データ ビューの **内に** データグリッド ** をドラッグ&ドロップします。

    {{% image_container width="550" %}}![](attachments/pages-how-to-configure-form/data-grid-inside-data-view.png){{% /image_container %}}

3. データ グリッドのプロパティに移動し、 **エンティティ** をクリックします。

4. 現在の検査レポートに関連付けられているチェックリスト項目だけを表示するには 関連する **チェックリスト** 図形(*Checklist_InspectionReport/Checklist*)を選択し、 **図形を選択** ダイアログボックスで **選択**をクリックします:

    {{% image_container width="450" %}}![](attachments/pages-how-to-configure-form/data-grid-over-association.png){{% /image_container %}}

5. ページの主な目的は情報を表示することであるため、データ グリッドに **検索** セクションは必要ありません。 データ グリッドのプロパティを開く > **** セクションを検索し、 **検索を有効にする** トグル:

    ![データグリッド検索](attachments/pages-how-to-configure-form/data-grid-search.png)

6. レポートに新しいチェックリスト項目を追加できるようにするには、データ グリッドの **New** ボタンを選択し、そのプロパティを開きます。

7. **on Click Action** を **Page** に設定します。

8. **Create Object** プロパティを有効にします。 **エンティティ** プロパティは自動的に **チェックリスト**に設定されます:

    {{% image_container width="250" %}}![](attachments/pages-how-to-configure-form/new-button-properties.png){{% /image_container %}}

9. **ページ** プロパティをクリックします。

10. **ページの選択** ダイアログボックスで、 **新規ページ** をクリックします。

11. In the **Create new page** dialog box, set the **Title** to **Checklist_Details** and the **Layout** to **PopupLayout**.

12. The **Pre-fill page contents based on the Checklist entity** option is on, so the page template (*Forms*) is selected automatically for you. **フォームを垂直に選択**:

    {{% image_container width="550" %}}![](attachments/pages-how-to-configure-form/manage-checklist.png){{% /image_container %}}

13. **Create** をクリックします。

14. エンドユーザーが新しいチェックリスト項目を追加できるポップアップページが作成されます。 これで、 **編集** ボタンのオンクリック操作と同じページを選択して、選択したチェックリストを編集することができます。 データ グリッドの **編集** ボタンをクリックし、そのプロパティを開きます。

15. **on Click Action** を **Page** に設定します。

16. **Page** プロパティを **Manage_Checklist** に設定します。

      {{% image_container width="250" %}}![](attachments/pages-how-to-configure-form/edit-button-properties.png){{% /image_container %}}

チェックリスト項目が表に表示されるようになりました。 You can add new checklist by clicking the **New** button in the table, and edit the selected checklist by clicking the **Edit** button.

{{% image_container width="80%" %}}

![](attachments/pages-how-to-configure-form/data-grid-configured.png)

{{% /image_container %}}

おめでとうございます このレポートの選択したレポートとチェックリスト項目の詳細を表示するページがあります。

{{% image_container width="80%" %}}

![設定されたページ](attachments/pages-how-to-configure-form/configured-page.png)

{{% /image_container %}}

アプリをプレビューしてページをテストできるようになりました。 ページをプレビューする方法の詳細については、 [プレビュー中 & アプリを公開する](/studio8/publishing-app) を参照してください。

ページの詳細などで作業することもできます。 検査レポートのリストに動的画像を追加すると、その名前の横に独自の会社ロゴが表示されます。 動的画像の詳細については、 [イメージ & ファイル](/studio8/page-editor-widgets-images-and-files) を参照してください。

新しい機能を追加することもできます。 たとえば、検査官がレポートに画像を添付できるようにできます。 詳細については、 [エンドユーザーが画像を添付できるようにする方法](pages-how-to-attach-images) を参照してください。