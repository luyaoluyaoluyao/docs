---
title: "構成"
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

次の構造ウィジェットがあります。

* [列とサイドバー](#columns)

* [コンテナ](#container-overview)

* [グループボックス](#group-box-overview)

* [タブコンテナ](#tab-container)

* [Snippet](#snippet)

    ![](attachments/page-editor-widgets-structure/structure-widgets.jpg)

## 2 列とサイドバー{#columns}

**列** と **サイドバー** のウィジェットは [レイアウト グリッド](#layout-grid) に基づいています。これはページを行と列で構成するウィジェットです。 **列とサイドバー** はあらかじめ設定された列数を持つレイアウトグリッド構成です。

## 3 レイアウトグリッドの概要 {#layout-grid}

**レイアウト グリッド** を使用すると、ページを構成してすぐに応答させることができます。 これは、レイアウトグリッドには、異なるデバイスでページがどのように見えるかを示す組み込みの動作があることを意味します。 **デバイス** モードを切り替えて、電話、タブレット、またはデスクトップにページを表示する方法を確認します。

{{% image_container width="300" %}}![デバイスモード](attachments/page-editor-widgets-structure/device-modes.png)
{{% /image_container %}}

レイアウト グリッドには [列](#column) と [行](#row) が含まれています。

行は、応答性の高い(デスクトップ)ビューで隣接して配置された列で構成されています。

![行の例](attachments/page-editor-widgets-structure/row-example.png)

列は行内のセルです。 1 つまたは複数のウィジェットを列に配置できます。たとえば、2 つのボタンを列の中に配置できます。

{{% image_container width="300" %}}![列の例](attachments/page-editor-widgets-structure/column-example.png)
{{% /image_container %}}

行と列の詳細については、 [行プロパティ](#row) および [列プロパティ](#column) のセクションを参照してください。

### 3.1 レイアウトグリッドのプロパティ {#layout-grid-properties}

You can access the **Layout Grid** properties through the breadcrumb (for more information, see the [Breadcrumb](page-editor#breadcrumb) section in *Pages*). レイアウト グリッド プロパティは以下のセクションで構成されます。

* [展開](#expand-section)

* [全般](#general-section)

* [デザイン](page-editor-widgets-design-section)

    {{% image_container width="250" %}}![レイアウトグリッドのプロパティ](attachments/page-editor-widgets-structure/layout-grid-properties.png)
    {{% /image_container %}}

#### 3.1.1 セクションを展開 {#expand-section}

**Expand** section > **Add Row** を使用すると、選択した行の上または下に行を追加して、ウィジェットを配置するスペースを増やすことができます。

{{% alert type="info" %}}

[行](#row) と [列](#column) には同じ設定の **展開** セクションがあります。

{{% /alert %}}

新しい行を追加するには、次のいずれかを実行します。

1. パンくずリストのレイアウトグリッドを選択し、 **プロパティ** > **行を追加**、 いずれかのボタンをクリックして、上または下の行を挿入します。
2. 行を選択し、 **プロパティ** > **行を追加**, いずれかのボタンをクリックして、上または下の行を挿入します。
3. 列を選択し、 **プロパティ** > **行を追加**, いずれかのボタンをクリックして、上または下の行を挿入します。

空の行が挿入されます。

#### 3.1.2 一般セクション {#general-section}

**一般** セクションでは、レイアウト グリッドの幅を設定できます。 次のいずれかを選択できます:

* **全幅** - レイアウトグリッドはコンテナ全体の幅をとります
* **Fixed Width** - レイアウトグリッドはページの中央に固定されたサイズで、デバイスに応じて自動的に調整されます。

#### 3.1.3 デザインセクション

**デザイン** セクションとそのプロパティについては、 [デザイン セクション](page-editor-widgets-design-section) を参照してください。

### 3.2 行のプロパティ {#row}

*行* プロパティは以下のセクションで構成されています:

* [展開](#expand-section-row)

* [コンテナ設定](#container-settings)

* [全般](#general-section-row)

    {{% image_container width="250" %}}![行のプロパティ](attachments/page-editor-widgets-structure/row-sections.png)
    {{% /image_container %}}

#### 3.2.1 セクションを展開 {#expand-section-row}

**展開** セクション > **行の追加** では、選択した行の上または下に行を追加できます。 詳細については、 [レイアウト グリッド](#expand-section) の *拡張セクション* を参照してください。

#### 3.2.2 コンテナ設定セクション {#container-settings}

**Container Settings** セクションでは、レイアウト グリッドの幅を設定し、最大幅または固定幅を選択できます。

{{% alert type="info" %}}

このプロパティはレイアウト グリッドの [一般セクション](#general-section) のプロパティと同じです。 詳細については、 [一般セクション](#general-section) を参照してください。

{{% /alert %}}

#### 3.2.3 一般セクション {#general-section-row}

行の **一般** セクションでは、列の数を選択し、列の整列や間隔を追加できます。 このセクションには、次の設定が含まれています:

* **Columns** – 行の列数を設定します。

    * 作業領域の列数を設定することもできます。列のいずれかを選択し、その上にあるプラスアイコンをクリックして、右に新しい列を追加します。

        {{% image_container width="300" %}}![Adding New Column](attachments/page-editor-widgets-structure/adding-new-column.png){{% /image_container %}}

* <a name="align-columns"></a>**列を垂直に配置** – 行のすべての列を垂直に揃えます。次のオプションを選択できます。

    {{% image_container width="280" %}}![](attachments/page-editor-widgets-structure/align-columns.png)
    {{% /image_container %}}

* **列間の間隔** - 有効な場合、列間の間隔を追加

### 3.3 列のプロパティ {#column}

列プロパティは以下のセクションで構成されています:

* [展開](#expand-section-column)

* [全般](#general-section-column)

    {{% image_container width="250" %}}![列のセクション](attachments/page-editor-widgets-structure/column-sections.png)
    {{% /image_container %}}

#### 3.3.1 セクションを展開 {#expand-section-column}

列のformat@@0セクションでは、行または列を追加できます。


##### 3.3.1.1 行の追加

**行を追加** 選択した行の上または下に行を追加できます。 詳細については、 [レイアウト グリッド](#expand-section) の *拡張セクション* を参照してください。

##### 3.3.1.2 列を追加

**列を追加** すると、選択した列の左側または右側に列を追加できます。

#### 3.3.2 一般セクション {#general-section-column}

**一般** セクションでは、列 [幅](#column-width) を設定し、 [個々の列を](#align-column) 揃えることができます。

##### 3.3.2.1 Width {#column-width}

対応するデバイスモードを選択すると、デスクトップ、タブレット、または携帯電話の列幅を設定できます。

![](attachments/page-editor-widgets-structure/width-per-device.png)

次のオプションを選択できます。

* **自動入力** - 列の空き容量を取得します (例えば、列が1つある場合)。 列全体に渡って2列分割されます)

* **自動フィットコンテンツ** - 列のサイズをコンテンツに自動的に合わせる

* **マニュアル** - 列のサイズを手動で設定できます

    * **Manual** を選択すると、列の幅を 1 から 12 まで設定できるスライダーが表示されます。

        ![](attachments/page-editor-widgets-structure/column-size.png)

作業領域で列のサイズを手動で変更することもできます。列の境界線をドラッグしてサイズを変更します。

{{% image_container width="300" %}}
![列のサイズ変更](attachments/page-editor-widgets-structure/resizing-column.png)
{{% /image_container %}}

**** プロパティを使用すると、レイアウトをより柔軟に、さまざまなタイプのデバイスに適応できます。

たとえば、1 行と 2 列のレイアウト グリッドがあります。画像は 1 列にあります。 細かいことが書かれています

For the *desktop* and *tablet*, you might want to set the first column with a picture to **Auto-fit content** and and the second one to **Auto-fill**, this way the first column will adjust to the size of the picture, while the second one will take the rest of the row:

![レイアウト例、デスクトップ](attachments/page-editor-widgets-structure/layout-example-desktop.png)

For *phone*, it can be a good idea to place two columns one under another, setting them to **Manual** width of *12*. この場合、2 列目は自動的に別の行にラップされます。

 {{% image_container width="300" %}}
![携帯電話のレイアウト例](attachments/page-editor-widgets-structure/layout-example-phone.png)
{{% /image_container %}}

##### 3.3.2.2 垂直に揃え {#align-column}

**** プロパティは、行の [整列](#align-columns) プロパティを上書きし、個々の列の整列を設定します。

## 4コンテナの概要 {#container-overview}

**コンテナ** は、ウィジェットやウィジェットのグループを同時に配置するレイアウト要素として使用されます。 ドラッグまたは削除します。 たとえば、プログラムの詳細を1つのコンテナに記入するためのセクションタイトルと入力ウィジェットを配置できます。 その後、ページ上の別の場所にコンテナ全体を一度に再配置します。

{{% image_container width="300" %}}![コンテナの例](attachments/page-editor-widgets-structure/container.png)
{{% /image_container %}}

コンテナ プロパティは **デザイン** セクションで構成されます。 詳細については、 [デザインセクション](page-editor-widgets-design-section) を参照してください。

## 5 グループボックスの概要 {#group-box-overview}

グループ ボックスは、ウィジェットをグループ化するために使用されます。 グループボックスは、内部のすべての要素を使用して動的に折りたたんだり展開したりするように構成できます。

{{% image_container width="300" %}}![グループボックスの例](attachments/page-editor-widgets-structure/group-box.png)
{{% /image_container %}}

### 5.1 グループ ボックス プロパティ

グループ ボックス プロパティは、 **一般** セクションと **デザイン** セクションで構成されます。 **デザイン** セクションとそのプロパティについては、 [デザイン セクション](page-editor-widgets-design-section) を参照してください。

**一般** セクションで使用可能なプロパティについては、以下の表を参照してください。

| 属性      | 説明                                                                                                                                  |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| ヘッダを表示  | **ヘッダの表示** は、ヘッダがグループボックスの上に表示されるかどうかを定義します。 <br />*このプロパティはデフォルトで有効になっています。*                                                 |
| 図表番号    | このプロパティは、 **ヘッダーの表示** オプションが有効な場合にのみ表示されます。 ヘッダーに表示されるキャプションを定義します。                                                                 |
| 折りたたみ可能 | このプロパティは、 **ヘッダーの表示** オプションが有効な場合にのみ表示されます。 グループボックスとその要素を折りたたんだり展開したりできるかどうかを定義します。 このプロパティの可能な値は次のとおりです。<ul><li>**はい (展開開始)** – グループボックス内の要素は最初に展開され、ヘッダー内のマイナスアイコンをクリックすると折りたたむことができます</li><li>**はい (折りたたみを開始)** – グループボックス内の要素は最初に折りたたまれ、ユーザーがヘッダーのプラスアイコンをクリックすると拡張できます </li><li>**いいえ** – グループボックス要素を展開または折りたたむことはできません</li></ul> |

## 6タブコンテナの概要 {#tab-container}

タブコンテナは、タブに分類された情報を表示するために使用されるコンテナです。 これは、表示したい情報の量が画面上のスペースの量よりも大きい場合に便利です。 たとえば、1 つのタブに顧客リストを表示し、もう一方のタブに注文を表示できます。

{{% image_container width="300" %}}![format@@0 タブ](attachments/page-editor-widgets-structure/tab-container-example.png)
{{% /image_container %}}

各タブ内にウィジェットまたはウィジェットのグループを配置し、個別に情報を設定できます。

### 6.1 一般セクション

**一般** セクションでは、次のプロパティを設定できます。

*  **Tabs** – use radio buttons to switch from one tab to another; click the tab and drag it to change the order of tabs; click the **Edit** icon to open the tab properties and configure it (for more information, see section the [Tab Properties](#tab-properties) section)

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-container-tabs-property.png)
    {{% /image_container %}}

*  **Add New Tab** – adds a new tab to your tab container; tab properties will open automatically (for more information, see section the [Tab Properties](#tab-properties) section)

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/add-new-tab.png)
    {{% /image_container %}}

### 6.2 デザインセクション

**デザイン** セクションとそのプロパティについては、 [デザイン セクション](page-editor-widgets-design-section) を参照してください。

### 6.3 タブのプロパティ {#tab-properties}

各タブには以下のプロパティがあります。

* **図表番号** - タブの名前を定義します。ページ内をダブルクリックして図表番号を編集することもできます。

*  **Default Tab** - ページが開かれたときにアクティブなタブを定義します。 デフォルトのタブが設定されていない場合、最初のタブページが表示されます。 デフォルトでは、タブのどれもデフォルトタブとして設定されていません。

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-properties.png)
    {{% /image_container %}}

## 7 スニペットの概要 {#snippet}

スニペットはページの再利用可能な要素を定義し、Studio Pro で作成します。 スニペットを使用すると、ページを変更する際に、より少ない場所で変更を加えることができます。

例えば、 Studio Proのチームメンバーがスニペットを作成し、顧客フォームを追加してこのフォームを再利用可能なページ要素にしました。 Studio のページでもこのスニペットを使用できます。

{{% image_container width="500" %}}![](attachments/page-editor-widgets-structure/snippet-example.jpg)
{{% /image_container %}}

Studio 内のページでスニペットを呼び出すことはできますが、作成、変更、削除することはできません。 Studio Pro のスニペットの詳細については、 [スニペット](/refguide/snippet) を参照してください。

{{% alert type="info" %}}
スニペットが含まれていない場合、 **スニペット** ウィジェットは表示されません。
{{% /alert %}}

スニペットを呼び出し、あなたのページに追加するには、次の操作を行います:

1. **Toolbox** > **Widgets**で、 **Snippet** ウィジェットを見つけて、ページにドラッグ&ドロップします。

2. プロパティを開き、 **スニペット** プロパティをクリックします。

3. **Select Snippet** ダイアログボックスで、ページで使用するスニペットを選択し、 **Select** をクリックします。

    ![](attachments/page-editor-widgets-structure/select-snippet.jpg)

スニペットがページに追加されます。

## 8 続きを読む

* [ページ](page-editor)
* [ウィジェット](page-editor-widgets)
