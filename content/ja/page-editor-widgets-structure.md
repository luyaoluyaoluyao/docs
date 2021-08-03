---
title: "ストラクチャーウィジェット"
parent: "page-editor-widgets"
description: "Mendix Studio の構造ウィジェットの説明"
menu_order: 60
tags:
  - "スタジオ"
  - "ページエディタ"
  - "レイアウト"
  - "レイアウトウィジェット"
  - "構造ウィジェット"
---

## 1つの紹介

ストラクチャーウィジェットは、ページに構造を提供したり、内部の他のウィジェットをグループ化したりすることができるウィジェットです。

レイアウト ウィジェットは次のものです:

* [列とサイドバー](#columns)
* [コンテナ](#container-overview)
* [グループボックス](#group-box-overview)
* [タブコンテナ](#tab-container)

## 2 列とサイドバー{#columns}

**列** と **サイドバー** のウィジェットは事前に設定された列数を持つウィジェットです。 このカテゴリのすべてのウィジェットは [レイアウト グリッド](#layout-grid) に基づいています。これは、ページを行と列で構成する要素です。

## 3 レイアウトグリッドの概要 {#layout-grid}

**Layout Grid** を使用すると、ページを設定し、すぐに応答させることができます。 これは、レイアウトグリッドには、異なるデバイスでページがどのように見えるかを示す組み込みの動作があることを意味します。 画面上部の端末 **** モードを切り替えると、端末、タブレット、デスクトップにページがどのように表示されるかを確認できます。

{{% image_container width="350" %}}![デバイスモード](attachments/page-editor-widgets-structure/device-modes.png)
{{% /image_container %}}

レイアウト グリッドには [列と行](#columns-and-rows) が含まれています。

行は、レスポンシブ(デスクトップ)ビューで隣接するアイテムで構成されます。

![行の例](attachments/page-editor-widgets-structure/row-example.png)

列は行内のセルです。 1つまたは複数の要素を列の中に配置できます。たとえば、2つのボタンをその中に配置できます。

{{% image_container width="400" %}}![列の例](attachments/page-editor-widgets-structure/column-example.png)
{{% /image_container %}}

列を使用して、行内のアイテムを整列します。  行と列の詳細については、 [2.2 行と列のプロパティ](#columns-and-rows) セクションを参照してください。

### 2.1 レイアウトグリッドのプロパティ {#layout-grid-properties}

You can access the **Layout Grid** properties through the breadcrumb trail (for more information, see the **[Breadcrumb Trail](page-editor#breadcrumb)** section in *Pages*). レイアウト グリッド プロパティは以下のセクションで構成されます。

* [展開](#expand-section)
* [全般](#general-section)
* [デザイン](page-editor-widgets-design-section)

#### 2.1.1 セクションを展開 {#expand-section}

**Expand** section > **Add Row** を使用すると、選択した行の上または下に行を追加して、ウィジェットを配置するスペースを増やすことができます。

{{% image_container width="300" %}}![セクションを展開](attachments/page-editor-widgets-structure/layout-grid-expand-row.png)
{{% /image_container %}}

行を追加するには、レイアウト グリッドで行を選択し、 **Add Row** 内のボタンのいずれかをクリックします。 選択した行と同じ行が挿入されます。

{{% alert type="info" %}}

**行** と **列** には、同じプロパティを持つ **展開** セクションもあります。

{{% /alert %}}

#### 2.1.2 一般セクション {#general-section}

レイアウト グリッドの **一般** セクションには **全幅** プロパティが含まれます。 このプロパティが有効になっている場合、レイアウト グリッドは配置されているコンテナーの幅全体を取ります。 無効にすると、レイアウトグリッドのサイズがページの中央に固定され、デバイスに応じて自動的に調整されます。

#### 2.1.3 デザインセクション

**デザイン** セクションとそのプロパティについては、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

### 2.2 行と列のプロパティ {#columns-and-rows}

**行** と **列** のプロパティは以下のセクションで構成されています:

* [展開](#expand-section)
* [行のレイアウト](#row-layout)

{{% image_container width="300" %}}![行と列のプロパティ](attachments/page-editor-widgets-structure/row-and-column-sections.png)
{{% /image_container %}}

#### 2.2.1 セクションを展開

**列** と **行** の **展開** セクションには、レイアウト グリッドの **展開** セクションと同じプロパティと機能があります。 詳細については、 [レイアウトグリッド概要](#expand-section) の *拡張セクション* を参照してください。

#### 2.2.2 行レイアウトセクション {#row-layout}

**Row Layout** セクションでは、例えば、行の列の配置方法を変更できます。 列数を変更し、デスクトップ、タブレット、電話での表示方法を選択します。

| 属性     | 説明                                                                               |
| ------ | -------------------------------------------------------------------------------- |
| デスクトップ | デスクトップの列の数と幅を変更します。                                                              |
| タブレット  | タブレットの列の数と幅を変更します。 **タブレット** レイアウトで使用可能なオプションは、 **デスクトップ** で選択されたオプションによって異なります。 |
| 電話番号   | 携帯電話の列の数と幅を変更します。 **Phone** レイアウトで利用可能なオプションは、 **Desktop** で選択されたオプションによって異なります。 |

以下の例では、 では、デバイスの種類ごとに異なる行レイアウトを選択して、レイアウトの表示方法をアプリで確認できます。

![さまざまなデバイスの行レイアウト](attachments/page-editor-widgets-structure/row-layout-scheme.png)

## 4コンテナの概要 {#container-overview}

**コンテナ** は、ウィジェットやウィジェットのグループを同時に配置するレイアウト要素として使用されます。 ドラッグまたは削除します。 たとえば、プログラムの詳細を1つのコンテナに記入するためのセクションタイトルと入力ウィジェットを配置できます。 その後、ページ上の別の場所にコンテナ全体を一度に再配置します。

{{% image_container width="400" %}}![コンテナの例](attachments/page-editor-widgets-structure/container.png)
{{% /image_container %}}

コンテナ プロパティは **デザイン** セクションで構成されます。 詳細については、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

## 5 グループボックスの概要 {#group-box-overview}

グループ ボックスは、ウィジェットをグループ化するために使用されます。 グループボックスは、内部のすべての要素を使用して動的に折りたたんだり展開したりするように構成できます。

{{% image_container width="400" %}}![グループボックスの例](attachments/page-editor-widgets-structure/group-box.png)
{{% /image_container %}}

### 5.1 グループ ボックス プロパティ

グループ ボックス プロパティは、 **一般** セクションと **デザイン** セクションで構成されます。 **デザイン** セクションとそのプロパティについては、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

**一般** セクションで使用可能なプロパティについては、以下の表を参照してください。

| 属性      | 説明                                                                                                                                  |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| ヘッダを表示  | **ヘッダの表示** は、ヘッダがグループボックスの上に表示されるかどうかを定義します。 <br />*このプロパティはデフォルトで有効になっています。*                                                 |
| 図表番号    | このプロパティは、 **ヘッダーの表示** オプションが有効な場合にのみ表示されます。 ヘッダーに表示されるキャプションを定義します。                                                                 |
| 折りたたみ可能 | このプロパティは、 **ヘッダーの表示** オプションが有効な場合にのみ表示されます。 グループボックスとその要素を折りたたんだり展開したりできるかどうかを定義します。 このプロパティの可能な値は次のとおりです。<ul><li>**はい (展開開始)** – グループボックス内の要素は最初に展開され、ヘッダー内のマイナスアイコンをクリックすると折りたたむことができます</li><li>**はい (折りたたみを開始)** – グループボックス内の要素は最初に折りたたまれ、ユーザーがヘッダーのプラスアイコンをクリックすると拡張できます </li><li>**いいえ** – グループボックス要素を展開または折りたたむことはできません</li></ul> |

## 6タブコンテナの概要 {#tab-container}

タブコンテナは、タブに分類された情報を表示するために使用されるコンテナです。 これは、表示したい情報の量が画面上のスペースの量よりも大きい場合に便利です。 たとえば、1 つのタブに顧客リストを表示し、もう一方のタブに注文を表示できます。

{{% image_container width="400" %}}![format@@0 タブ](attachments/page-editor-widgets-structure/tab-container-example.png)
{{% /image_container %}}

各タブ内にウィジェットまたはウィジェットのグループを配置し、個別に情報を設定できます。

### 6.1 タブ コンテナ 全般プロパティ

**一般** セクションでは、次のプロパティを設定できます。

*  **Tabs** – use radio buttons to switch from one tab to another; click the tab and drag it to change the order of tabs; click the **Edit** icon to open the tab properties and configure it (for more information, see section [5.3 Tab Properties](#tab-properties))

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-container-tabs-property.png)
    {{% /image_container %}}

*  **Add New Tab** – adds a new tab to your tab container; tab properties will open automatically (for more information, see section [5.3 Tab Properties](#tab-properties))

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/add-new-tab.png)
    {{% /image_container %}}

### 6.2 format@@0 タブ

**デザイン** セクションとそのプロパティについては、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

### 6.3 タブのプロパティ {#tab-properties}

各タブには以下のプロパティがあります。

* **図表番号** - タブの名前を定義します。ページ内をダブルクリックして図表番号を編集することもできます。

*  **Default Tab** - ページが開かれたときにアクティブなタブを定義します。 デフォルトのタブが設定されていない場合、最初のタブページが表示されます。 デフォルトでは、タブのどれもデフォルトタブとして設定されていません。

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-properties.png)
    {{% /image_container %}}

## 7 続きを読む

* [ページ](page-editor)
* [ウィジェット](page-editor-widgets)
