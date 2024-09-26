---
title: "画像を添付するためにエンドユーザーを有効にする"
category: "ページ"
description: "Mendix Studioで画像アップローダーを設定する方法を説明します。"
menu_order: 60
tags:
  - "スタジオ"
  - "ページ"
  - "画像"
  - "画像アップローダー"
  - "添付ファイル"
  - "画像を添付"
---

## 1つの紹介

この方法では、エンドユーザーが画像を添付できるようにする方法を説明します。 スマートフォン、タブレット、デスクトップなど、さまざまなデバイスから画像を添付したり、新しい画像を携帯電話のカメラで撮影したりできます。

**以下の方法を教えてくれます。**

* 画像エンティティを作成
* エンドユーザーが画像を添付できるようにするフォームを持つページを作成します
* 添付画像を一覧に表示

以下のユースケースについて説明します。

従業員が払い戻しのために旅行レポートを提出するフォーム(データビュー)の **新しいレポート** ページがあります。 彼らは旅行の名前、部署、目的、日付、および払い戻し額を記入します:

{{% image_container width="600" %}}![](attachments/pages-how-to-upload-images/form-example.png){{% /image_container %}}

ドメインモデルは次のようになります:

{{% image_container width="200" %}}
![](attachments/pages-how-to-upload-images/domain-model.png)
{{% /image_container %}}

新しい機能を追加したい場合: 払い戻しレポートを作成する場合。 従業員はレシートを添付する必要があります – スクリーンショットや支払ったもののスキャン画像。

レポートの下のリストに添付された画像を表示し、必要に応じてエンドユーザーがリストから画像を削除できるようにしたい場合もあります。

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio/page-editor) を参照してください。
* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio/domain-models) を参照してください。

## 3 イメージエンティティの作成

まず第一に ドメインモデルに特別なタイプのエンティティを追加する必要がある画像を添付したりアップロードしたりできます:画像エンティティ。 次の操作を行います:

1. ドメインモデルを開き、 **Toolbox** タブを開きます。

2. **イメージ エンティティ** を選択し、ドメインモデルにドラッグ&ドロップします。

3. **Create New Image Entity** ダイアログボックスで、 **Name** を *Receipt* に設定し、 **Create** をクリックします。

    {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/create-new-image-entity.png){{% /image_container %}}

4. 次に、 **イメージ** エンティティから **レポート** エンティティへの関連付けを作成する必要があります。 次のいずれかを実行します。

    1. **イメージ** エンティティにカーソルを合わせて、ドットアイコンをクリックし、 **レポート** エンティティに点をドラッグします。

        {{% image_container width="500" %}}![](attachments/pages-how-to-upload-images/association-method1.png){{% /image_container %}}

    2. **イメージ** エンティティを選択し、矢印アイコンをクリックし、関連付けの2番目のエンティティとして **レポート** を選択します。

        {{% image_container width="250" %}}![](attachments/pages-how-to-upload-images/association-method2.png){{% /image_container %}}

よくできました！ 画像エンティティと関連付けを **レポート** エンティティに作成しました。

{{% image_container width="600" %}}![](attachments/pages-how-to-upload-images/domain-model-configured.png){{% /image_container %}}

## 4 画像アップローダーを追加する

**Image Uploader** は、エンドユーザーが画像を添付できるようにするウィジェットです。 ただし、 データコンテナ(リストビューまたはデータビュー)内でのみ機能することができ、データソースとしてのみイメージエンティティを持つことができます。 画像アップローダーをレポートフォームにドラッグ&ドロップするだけで、正しく動作しません。 現在のデータビューには、 **レポート** エンティティがデータソースとして含まれているため、画像エンティティではありません:

{{% image_container width="600" %}}![](attachments/pages-how-to-upload-images/form-example.png){{% /image_container %}}

これを解決するために、エンドユーザーが画像を添付できるポップアップページを開くボタンを追加できます。 このページは、 *Image_Report* アソシエーションを介して現在のレポートフォームに接続され、 **Image** エンティティとして画像をアップロードし、この特定のレポートに関連付けられます。

以下の手順に従ってください。

1. 従業員が新しいレポートを提出する **新しいレポート** ページを開きます。

2. **Toolbox** を開き、 **Create Object** ボタンを検索します。

3. ボタンを **保存** ボタンと **キャンセル** ボタンの上にドラッグ&ドロップします。

    {{% image_container width="450" %}}![](attachments/pages-how-to-upload-images/new-button.png){{% /image_container %}}

4. ボタンのプロパティ > **図表番号** プロパティを開き、 *新規* から *画像を添付* に名前を変更します。

5. **アイコン** プロパティをクリックします。

6. **アイコンの選択** ダイアログボックスで、 *画像* アイコンを検索して選択します。

7. ボタンのプロパティで、 **Style** プロパティをクリックし、 **Default** から **Success** に変更します。 変更後、ボタンは次のようになります:

    {{% image_container width="150" %}}![](attachments/pages-how-to-upload-images/button-style-change.png){{% /image_container %}}

8. ボタンのプロパティで、 **Entity** プロパティをクリックします。

9. **図形の選択** ダイアログボックスで、 **レシート** 図形を **Receipt_Report** 関連付けから **選択** をクリックします。

    {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/image-report-association.png){{% /image_container %}}

10. ボタンのプロパティで、 **ページ** をクリックします。

11. **ページの選択** ダイアログボックスで、右上隅のプラスアイコンをクリックします。

12. **新規ページの作成** ダイアログボックスで、次の操作を行います:

     1. **タイトル** を *画像を添付する* に設定します。

     2. **レイアウト** を *PopupLayout* に設定します。

     3. **レシートエンティティ** オプションに基づいてページを事前に入力するformat@@2 がオンになっているので、ページテンプレート (フォーム) が自動的に選択されます。 **フォームを垂直に** を選択し、 **作成** をクリックします。

         {{% image_container width="500" %}}![](attachments/pages-how-to-upload-images/create-new-page-images.png){{% /image_container %}}

13. 事前設定されたフォーム(データビュー)を持つ新しいポップアップページが作成されます。

     {{% image_container width="500" %}}![](attachments/pages-how-to-upload-images/attach-images-page.png){{% /image_container %}}

     As you only need your end-users to attach images on this page, delete the **Dynamic image** widget, **Name** and **Size** text boxes from the data view.

14. **Toolbox**を開き、 **Image Uploader**を検索し、データビューの中にドラッグ&ドロップします。

従業員が払い戻しレポートに画像を添付できるポップアップページを作成しました：

{{% image_container width="450" %}}![](attachments/pages-how-to-upload-images/attach-images-pop-up-page.png){{% /image_container %}}


## 5添付画像を表示する

ユーザーが画像を添付した後 添付ファイルを表示し不要なものを削除する機会を与えるのもいいでしょう これを行うには、動的な画像を含むリストを追加する必要があります。

1. **新しいレポート** ページを開きます。

2. In the **Building Blocks**, search for **List with image** and drag and drop it under the **Attach Images** button (*inside* the data view). ウィジェットを含むリストビューがページに追加されます。

    ![](attachments/pages-how-to-upload-images/list-4.png)

3. リストビューのプロパティを開き、次の操作を行います:

    1. **エンティティ** プロパティをクリックします。
    2. In the **Select Entity** dialog box, choose the **Select Entity** dialog box, choose the **Receipt** entity over **Receipt_Report** association and click **Select**:

        {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/image-report-association.png){{% /image_container %}}

4. リストビューで画像をクリックし、プロパティを開き、次の操作を行います。

    1. ユーザがアタッチした画像を表示するには、 **イメージソース** を **スタティックイメージ** から **ダイナミックイメージ** に変更します。
    2. **Image Entity** プロパティをクリックします。
    3. **Select Image Entity**で、 **Receipt** を選択し、 **Select** をクリックします。
    4. In the **Default Image** property, click **Select image**, and in the **Select image** dialog box, click **Clear**.

        {{% image_container width="300" %}}![](attachments/pages-how-to-upload-images/image-properties.png){{% /image_container %}}

5. *セカンダリテキスト* のサブタイトルをリストビューで削除します。

6. リストビューで **リスト アイテム タイトル** テキストを選択し、そのプロパティを開きます。

    1. **Content** プロパティで、 *List item title* テキストを削除し、 **Add**  > **Attribute** をクリックします。
    2. In the **Select Attribute** dialog box, choose the **Name** attribute and click **Select** to display the name of the attached image.

        {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/select-attribute.png){{% /image_container %}}

7. リストビューでボタンを選択し、プロパティを開き、次の操作を行います:

    1. **イベント** セクション > **** プロパティをクリックして、 **詳細** を選択します。

    2. **Action** プロパティで、 **Delete Object** を選択します。

    3. **一般** セクション > **図表番号** プロパティで、ボタンキャプションを *削除* に設定します。

    4. iconプロパティをクリックし、 **Select icon** ダイアログボックスの **Clear** をクリックしてアイコンを削除します。

    5. **レンダリングモード** を **リンク** から **ボタン** に変更します。

    6. **Style** プロパティで、 **Default** を **Danger** に変更します。

      ![](attachments/pages-how-to-upload-images/button-properties.png)

よくできました！ これで添付された画像を表示する画像リストがあり、必要に応じてユーザーはリストから画像を削除することができます:

![](attachments/pages-how-to-upload-images/configured-image-list.png)

おめでとうございます ユーザが画像を添付し、リストにこれらの画像を表示できるレポートを構成していること。

[アプリ](/studio/publishing-app) をプレビューして、画像のアップロードの仕組みをテストします。 画像の代わりにファイルを添付するボタンを設定することもできます。 ファイルの詳細については、 [イメージ & ファイル](/studio/page-editor-widgets-images-and-files) を参照してください。