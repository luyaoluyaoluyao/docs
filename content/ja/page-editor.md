---
title: "ページ"
description: "Mendix Studioでページエディタを説明します。"
menu_order: 30
tags:
  - "スタジオ"
  - "ページエディタ"
  - "ページ"
---

## 1つの紹介

ページエディタを使用すると、Mendixアプリケーションのエンドユーザーインターフェイスを定義できます。

Mendix Studio でアプリの **ページ** を表示するには、Studio の左メニューバーの **ページ** アイコンをクリックします。

{{% image_container width="300" %}}![](attachments/page-editor/pages-icon.png)
{{% /image_container %}}

{{% alert type="warning" %}}

Studio は、Atlas UI フレームワークに基づくアプリのみをサポートしています。 Atlas UI の詳細については、 [Atlas UI](/howto/front-end/atlas-ui) を参照してください。

{{% /alert %}}

## 2つのコンポーネント

Pages of Studio は以下のコンポーネントで構成されています:

* **レイアウト** はページを構成します。 すべてのページはレイアウトに基づいています。 たとえば、 **Atlas_Default** または **PopupLayout** は、ページを作成するときに選択できるレイアウトの種類です。
* **テンプレート** - 新しいページを作成するための出発点。 新しいページを作成するたびに で、ページに表示したいデータと表示方法に応じてテンプレートを選択します。 ダッシュボード、フォーム 例えば、 **ダッシュボードアクションタイル**、 **リストデフォルト**、 **マスター詳細** はテンプレートの種類です。
* **ウィジェット** – 単一のユーザーインターフェイス要素。 詳細については、 [5.2 節を参照してください。 ウィジェット](#widgets) と [ウィジェット](page-editor-widgets)。
* **Building Blocks** – ページの構築とスタイリングのプロセスを高速化する要素を事前に設定しました。 詳細については、 [5.1 Building Blocks](#building-blocks) セクションを参照してください。

上記のコンポーネントはAtlas UIで動作します。 詳細については、 [Atlas UI](/howto/front-end/atlas-ui) を参照してください。

## 3 基本機能の実行 {#page-editor-basic-functions}

### 3.1 ページを開く

Studio を開くと、アプリのホームページが自動的に開きます。

Studio でページを開くには、次の手順を実行します。

1. 左のメニューバーの **ページ** アイコンをクリックします。

2.  表示されるアプリページのリストで、開きたいアプリを選択してクリックします。

    {{% image_container width="400" %}}![](attachments/page-editor/opening-a-page.png)
    {{% /image_container %}}

選択したページが開きます。

### 3.2 新規ページの作成 {#creating-new-page}

Studio で新しいページを作成するには、次の操作を行います。

1. **Pages** アイコンをクリックします。
2.  表示されるサイドパネルの右上隅にある **New** をクリックします。

    {{% image_container width="400" %}}![](attachments/page-editor/new-page.png)
    {{% /image_container %}}

3. **新規ページの作成** ダイアログウィンドウで、ページのタイトルを入力し、レイアウトとページ テンプレートを選択します。
4.  **Create** をクリックします。

    ![](attachments/page-editor/create-new-page-dialog.png)

新しいページが作成されます。

### 3.3 ページの削除

Studio でページを削除するには、次の操作を行います。

1. 削除したいページを開きます。
2. **プロパティ** タブを開きます。
3.  **プロパティ** タブの下部にある **削除** をクリックします。

    ![](attachments/page-editor/page-delete.png)

   選択したページが削除されます。

### 3.4 ページ上の要素の表示

要素と [プロパティ](#page-editor-properties)を表示するには、この要素をクリックします。

選択された要素には青い枠線が表示されます。 さらに、要素がデータコンテナ内(データビューまたはリストビュー)にある場合、データコンテナアイコンが表示されます。

{{% image_container width="400" %}}![](attachments/page-editor/input-widget-example.png)
{{% /image_container %}}

## 4つのパンくずリスト {#breadcrumb}

ページ上で項目を選択すると、Studio の左下隅にパンくずリストが表示されます。

Breadcrumbトレイルは2つの機能を提供します:

* ページ上に選択したアイテムのボトムアップ層を表示します
* ユーザーがページ上の要素を選択し、そのプロパティを表示できるようにします

たとえば、ページ上のボタンを選択すると、そのボタンが列にあるコンテナに配置されていることがわかります。  一方、列は連続しており、この行はページ上のレイアウト グリッドに配置されます。

![](attachments/page-editor/breadcrumb.png)

要素の情報を表示するには、ブレッドクラムトレイルでこの要素をクリックすると、その属性が自動的に表示されます。

### 4.1 パンくずリストでナビゲーションレイアウト情報を表示する

パンくずリストでクリックすると、ナビゲーションレイアウトの情報を表示することもできます。

以下のオプションは **プロパティ** タブに表示されます。

{{% image_container width="300" %}}![](attachments/page-editor/navigation-layout.png)
{{% /image_container %}}

## 5 Toolbox Tab

**ツールバー** には、ページで使用できるツールが表示されます。

このタブは以下で構成されています:

* [ウィジェット](#widgets)
* [Building Blocks](#building-blocks)

### 5.1 ウィジェット {#widgets}

ウィジェットは、設定可能な単一のユーザーインターフェイス要素です。 ページに追加する際に、ほとんどの非カスタム ウィジェットを [すばやく](page-editor-widgets#quick-config) 設定できます。 詳細については、 [ウィジェット](page-editor-widgets) を参照してください。

{{% alert type="info" %}}

[ウィジェットの概要](settings-widget-overview) でウィジェットを更新できます。

{{% /alert %}}

### 5.2 Building Block {#building-blocks}

Building Blocksは、ページを高速に構築するための事前設定されたウィジェットで構成されています。ページにドラッグ＆ドロップするだけで構築できます。

![](attachments/page-editor/building-blocks.png)

Studio のBuilding Blockは次のカテゴリに分類されます:

| Building Block | 説明                                                                            |
| -------------- | ----------------------------------------------------------------------------- |
| ヘッダー           | ヘッダーは、ページタイトルの機能とページのコントロールバーを兼ね備えています。 コンパクトなデザインと汎用性のため、モバイルページでよく使用されています。 |
| リスト            | データのリストを表示するには、このブロックを使用します。                                                  |
| カード            | カードには、さまざまな目的のための様々なビルディングブロックが含まれています。                                       |
| グラフ            | グラフとしてデータを表示する場合は、これらの構成要素を使用します。                                             |
| フォーム           | これらのBuilding Blocksを使用して、アプリのユーザーが記入するフォームを作成します。                             |
| リストコントロール      | データをコントロールリストとして表し、リスト内の項目を並べ替えて検索するのに役立ちます。                                  |
| マスターの詳細        | これらのBuilding Blocksを使用して、多くのアイテムのリストを表示しますが、選択した要素の詳細のみを表示します。                |
| パンくずリスト        | アプリケーションに現在のページの場所を表示する場合は、これらのBuilding Blockを使用します。                          |
| タイムライン         | イベント一覧を表示するBuilding Blocksが含まれています。                                           |
| ウィザード          | 情報をステップバイステップで入力するには、これらの構成要素を使用します。                                          |
| 通知             | 異なる通知に使用されるBuilding Blockが含まれています。                                            |
| 配置             | 要素を揃えるために、これらの構成要素を使用します。                                                     |

Building Blockを挿入するには、選択したBuilding Blockをページ上にドラッグ&ドロップします。

特定のBuilding Blockのドキュメントを読んで、いつ、どのように使うかについて詳しく知りたい場合。 ビルディングブロックの右上隅にある小さなアイコンをクリックします。

![](attachments/page-editor/info-icon-building-blocks.png)

{{% alert type="info" %}}

Studio Proを使用してAtlasのUIをカスタマイズできるため、Building Blocksのカテゴリは異なる場合があります。

{{% /alert %}}

### 5.2 ウィジェット {#widgets}

ウィジェットは、設定可能な単一のユーザーインターフェイス要素です。 ページに追加する際に、ほとんどの非カスタム ウィジェットを [すばやく](page-editor-widgets#quick-config) 設定できます。 詳細については、 [ウィジェット](page-editor-widgets) を参照してください。

{{% alert type="info" %}}

[ウィジェットの概要](settings-widget-overview) でウィジェットを更新できます。

{{% /alert %}}

## 6プロパティタブ {#page-editor-properties}

**プロパティ** タブには、現在選択されている要素のプロパティが表示され、この要素によって異なります。

{{% image_container width="300" %}}![](attachments/page-editor/properties.png)
{{% /image_container %}}


## 7 続きを読む

* [データ ビュー & リスト ビュー プロパティ](page-editor-data-view-list-view)
