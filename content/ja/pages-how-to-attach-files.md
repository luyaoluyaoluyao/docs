---
title: "ファイルのアップロードとダウンロード"
category: "ページ"
description: "Mendix Studio でファイルマネージャを設定する方法を説明します。"
menu_order: 70
tags:
  - "スタジオ"
  - "ページ"
  - "ファイル"
  - "ファイルをアップロード"
  - "添付ファイル"
  - "ファイルマネージャー"
---

## 1つの紹介

これにより、エンドユーザーがPDFファイルやMicrosoft Word文書などのファイルを添付およびダウンロードできるようにする方法を説明します。 電話、タブレット、デスクトップなど、さまざまなデバイスからファイルを添付することができ、リストから添付ファイルをダウンロードすることもできます。

**以下の方法を教えてくれます。**

* ファイルエンティティを作成
* エンドユーザーがファイルをアップロードできるようにするフォームのページを作成します
* リストに添付ファイルを表示
* エンドユーザーにファイルのダウンロードを許可する

以下のユースケースについて説明します。

会社には、企業のIT部門が従業員に割り当てられた資産を追跡するアプリがあります。 **従業員プロファイル** ページに、従業員の名前などの詳細が記載されたフォーム (データビュー) があります。 部署、電子メール、電話番号、タイトル、およびそれらに割り当てられた資産(例えば、携帯電話やラップトップ)。 この情報は、IT 管理者によって入力および更新されます。

{{% image_container width="600" %}}
![従業員プロフィールページ](attachments/pages-how-to-attach-files/employee-profile-form.png)
{{% /image_container %}}

ドメインモデルは次のようになります:

{{% image_container width="200" %}}![Domain Model](attachments/pages-how-to-attach-files/domain-model.png){{% /image_container %}}

新しい機能を追加する必要があります。IT管理者は、従業員プロファイルにファイルを添付できる必要があります。 例えば従業員が署名した電話やノートパソコンのポリシーを

また、IT管理者が添付ファイルをファイルのリストからダウンロードできるようにすることもできます。

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio8/page-editor) を参照してください。
* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio8/domain-models) を参照してください。

## 3 ファイルエンティティの作成

まず第一に ドメインモデルに特別な種類のエンティティを追加する必要があるファイルを添付および/またはダウンロードできるようにするには、 [ファイルエンティティ](/studio8/domain-models#entity-types) を使用します。 次の操作を行います:

1. ドメインモデルを開き、 **Toolbox** タブを開きます。

2. **File Entity** を選択し、ドメインモデルにドラッグ&ドロップします。

3. **Create New File Entity** ダイアログボックスで、 **Name** を *Document* に設定し、 **Create** をクリックします。

    {{% image_container width="450" %}}![Create File Entity](attachments/pages-how-to-attach-files/create-file-entity.png){{% /image_container %}}

4. 次に、 **ファイル** エンティティから **従業員** エンティティへの関連付けを作成する必要があります。 次のいずれかを実行します。

    1. **ファイル** エンティティにカーソルを合わせて、ドットアイコンをクリックし、 **従業員** エンティティに点をドラッグします。

        {{% image_container width="500" %}}![Create Association](attachments/pages-how-to-attach-files/create-association-method-one.png){{% /image_container %}}

    2. **ファイル** エンティティを選択し、矢印アイコンをクリックし、関連付けの2番目のエンティティとして **従業員** を選択します。

        {{% image_container width="250" %}}![Create Association](attachments/pages-how-to-attach-files/create-association-method-two.png){{% /image_container %}}

よくできました！ ファイルエンティティと関連付けを **従業員** エンティティに作成しました:

{{% image_container width="600" %}}![Domain Model Configured](attachments/pages-how-to-attach-files/domain-model-configured.png){{% /image_container %}}

## 4 ファイルマネージャーの追加

**ファイル マネージャー** は、エンドユーザーがファイルを添付またはダウンロードできるウィジェットです。 ただし、データコンテナ(リストビューまたはデータビュー)内でのみ機能できます。 そして、リストビューまたはデータビューはファイルエンティティをデータソースとしてのみ持つことができます。 If you just drag and drop the file manager to your employee profile form, it will not work correctly, because your current data view has the **Employee** entity as its data source, and you need the data source to be a file entity, which is in this case the **Document** entity:

{{% image_container width="600" %}}![Employee Profile Page](attachments/pages-how-to-attach-files/employee-profile-form.png){{% /image_container %}}

これを解決するために、エンドユーザー(IT管理者)が画像をアップロードできるポップアップページを開くボタンを追加できます。 このページは、 *Document_Employee* 関連付けを介して現在のレポートフォームに接続され、この特定のレポートに関連付けられているファイルをアップロードします。

以下の手順に従ってください。

1. IT管理者が割り当てられた従業員と資産に関する情報を作成および編集する **従業員プロファイル** ページを開きます。

2. **Toolbox** を開き、 **Create Object** ボタンを探します。

3. ボタンを **保存** ボタンと **キャンセル** ボタンの上にドラッグ&ドロップします。

    {{% image_container width="450" %}}![Create Object Button](attachments/pages-how-to-attach-files/create-object-button.png){{% /image_container %}}

4. ボタンのプロパティを開き、次の操作を行います:

    1. **図表番号** プロパティを選択し、 *新規* から *ファイルを添付* に名前を変更します。

    2. **アイコン** プロパティをクリックします。

    3. **アイコンの選択** ダイアログボックスで、 *ファイル* アイコンを検索し、 **選択** をクリックします。

    4. **スタイル** プロパティをクリックし、 **デフォルト** から **成功** に変更します。 変更後、ボタンは次のようになります:

        {{% image_container width="150" %}}![Attach Files](attachments/pages-how-to-attach-files/attach-file-button.png){{% /image_container %}}

    5. **エンティティ** プロパティをクリックします。

    6. In the **Select Entity** dialog box, choose the **Document** entity over **Document_Employee** association (*Document_Employee/Document*) and click **Select**:

        {{% image_container width="400" %}}![Select File Entity](attachments/pages-how-to-attach-files/select-file-entity.png){{% /image_container %}}

    7. **ページ** プロパティをクリックします。

    8. 開いた **ページの選択** ダイアログボックスで、 **新規ページ** をクリックします。

    9. **新規ページの作成** ダイアログボックスで、次の操作を行います:

         1. **タイトル** を *ファイルを添付する* に設定します。

         2. **レイアウト** を *PopupLayout* に設定します。

         3. **ドキュメントエンティティ** オプションに基づいてページを事前に入力するformat@@2 がオンになっているため、ページテンプレート(フォーム)が自動的に選択されます。 **フォームを垂直に** を選択し、 **作成** をクリックします。

             {{% image_container width="500" %}}![](attachments/pages-how-to-attach-files/create-attach-file-page.png){{% /image_container %}}

        4. 事前設定されたフォーム(データビュー)を持つ新しいポップアップページが作成されます。

             {{% image_container width="500" %}}![Attach Files Page](attachments/pages-how-to-attach-files/attach-file-page.png){{% /image_container %}}

        5. このページにファイルを添付するには、エンドユーザーのみが必要です。 **の名前** と **サイズ** のテキストボックスをデータビューから削除します。

        6. **Toolbox**を開き、 **File Uploader**を検索し、データビューの中にドラッグ&ドロップします。

IT管理者が従業員プロフィールフォームにファイルを添付できるポップアップページを作成しました。

{{% image_container width="450" %}}![Attach Files Page Configured](attachments/pages-how-to-attach-files/attach-file-page-configured.png){{% /image_container %}}


## 5つのファイルをダウンロード中

エンドユーザーがファイルを添付した後 リストにファイルを表示し、必要に応じて添付ファイルをダウンロードする機会を与えることができます。 これを行うには、リストを追加する必要があります。

1. **Employee_Profile** ページを開きます。

2. In the **Building Blocks**, search for **List 4** and drag and drop it under the **Attach File** button (make sure you drop it *inside* the data view, this way you will be able to list only files associated with a selected employee instead of all files that were attached to any employee profile). ウィジェットを含むリストビューがページに追加されます。

    {{% image_container width="550" %}}![List 4](attachments/pages-how-to-attach-files/list-4.png){{% /image_container %}}

3. リストビューを選択し、そのプロパティを開き、次の操作を行います:

    1. **エンティティ** プロパティをクリックします。

    2. In the **Select Entity** dialog box, choose the **Document** entity over **Document_Employee** association (*Document_Employee/Document*) and click **Select**:

        ![エンティティを選択](attachments/pages-how-to-attach-files/select-file-entity.png)

4. 画像とリストから配置されている列を削除します。

    ![リストから列を削除](attachments/pages-how-to-attach-files/column-list.png)

5. *字幕* をつけることができます。

6. リスト ビューで **名前** のテキストを選択し、プロパティを開き、次の操作を行います:

    1. **Content** プロパティで、 *Name* テキストを削除し、 **Add attribute** をクリックします。
    2. In the **Select Attribute** dialog box, choose the **Name** attribute and click **Select** to display the name of the attached file.

        {{% image_container width="400" %}}![Select Attribute](attachments/pages-how-to-attach-files/select-attribute.png){{% /image_container %}}

7. リスト ビューの **詳細** ボタンを削除します。

8. Open the **Toolbox** and search for a **File Downloader**, drag and drop it to the column where the **Details** button was placed.

9. **File Downloader** (**File Manager**) properties > **Label** プロパティを開き、そこから *File* テキストを削除します。

よくできました！ 添付ファイルを表示するリストがあり、ユーザーはこのリストからファイルをダウンロードできます:

{{% image_container width="500" %}}![Configured List View](attachments/pages-how-to-attach-files/list-view-configured.png){{% /image_container %}}

おめでとうございます IT管理者がファイルを添付し、これらのファイルをリストに表示できるようにフォームを構成していること。

[](/studio8/publishing-app) アプリをプレビューして、ファイルのアップロードとダウンロードの仕組みをテストします。

![プレビューリスト](attachments/pages-how-to-attach-files/list-previewed.png)

ファイルの代わりに画像を添付するボタンを設定することもできます。 詳細については、 [エンドユーザーが画像を添付できるようにする方法](pages-how-to-attach-images) を参照してください。