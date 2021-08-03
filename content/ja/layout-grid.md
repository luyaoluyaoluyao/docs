---
title: "レイアウト グリッド"
parent: "container-widgets"
menu_order: 10
tags:
  - "studio pro"
  - "レイアウト グリッド"
  - "コンテナウィジェット"
  - "列"
  - "行"
  - "グリッド"
  - "レイアウト"
---

## 1つの紹介

レイアウト グリッドは、ページに構造を与えるウィジェットです。

レイアウト グリッドは [行](#rows) と [列](#columns) で構成されています: ![レイアウトグリッド例](attachments/container-widgets/layout-grid.png)

ブラウザでは、レイアウトグリッドはBootstrapグリッドシステムに基づいています。 Bootstrapグリッドシステムの詳細については、 [公式のBootstrapドキュメント](http://getbootstrap.com/css/#grid) を参照してください。

{{% alert type="info" %}}

アプリに [Atlas UI Resources](/appstore/modules/atlas-ui-resources) バージョン 2.4.0 以上がある場合は、下記の行と列のプロパティを使用できます。

行と列のプロパティの詳細については、 [行とプロパティ](#rows) と [列とプロパティ](#columns) のセクションを参照してください。

{{% /alert %}}

## 2 レイアウトグリッドのプロパティ

以下の画像にレイアウト グリッド プロパティの例を示します。

{{% image_container width="250" %}}![レイアウトグリッドのプロパティ](attachments/container-widgets/layout-grid-properties.png)
{{% /image_container %}}

レイアウト グリッド プロパティは以下のセクションで構成されます。

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 デザインプロパティセクション{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 一般セクション {#general}

#### 2.3.1 Width

**一般** セクションには、レイアウト グリッドの幅を決定する **幅** プロパティがあります。

| 値   | 説明                                                                                   |
| --- | ------------------------------------------------------------------------------------ |
| 全幅  | レイアウト グリッドは、利用可能なスペースの最大幅に広がり、ストレッチおよび縮小します。                                         |
| 固定幅 | レイアウト グリッドの幅は固定されていますが、ビューポートの変更に対応します。 Studio Pro では幅は設定できませんが、Bootstrapによって設定されます。 |

{{% alert type="warning" %}}

レイアウトグリッドは、そのコンテナの幅ではなく、ビューポートの幅に応答します。 固定幅レイアウトグリッドはトップレベルでのみ使用する必要があります。

{{% /alert %}}

### 2.4 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3行とそのプロパティ {#rows}

レイアウト グリッドには 1 つまたは複数の行を含めることができます。 各行に [列](#columns) があり、列の数は行ごとに異なります。

以下の画像では、レイアウト グリッド 行 プロパティの例を示します。

{{% image_container width="300" %}}![行のプロパティ](attachments/container-widgets/row-properties.png)
{{% /image_container %}}

行プロパティは以下のセクションで構成されています:

* [一般的な](#row-common)
* [全般](#row-general)
* [公開範囲](#row-visibility)

### 3.1 一般的なセクション {#row-common}

{{% snippet file="refguide/common-section-link.md" %}}

### 3.2 一般セクション {#row-general}

行の **General** セクションには、次のプロパティがあります。

* **Columns** – 行の列数を設定します。

* **縦方向に列を配置** – このプロパティは行内のすべての列を縦方向に揃えます。 次のオプションを選択できます。

  * **未設定** - アライメントが設定されていません

  * **上部** - 列がレイアウト グリッドの上部に揃えられます

  * **Center** - 列がレイアウト グリッドの中心に揃えられます

  * **下部** - 列がレイアウトグリッドの下部に揃っています

{{% alert type="info" %}}この設定は、個々の列の **垂直方向に揃える** 設定によって上書きできます。
{{% /alert %}}

* **列間の間隔** - *はい*, 列間の間隔を追加

### 3.3 表示セクション {#row-visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 4 列とプロパティ {#columns}

列はレイアウト グリッドの行を形成します。

 以下の画像では、レイアウト グリッド 列プロパティの例を示します。

{{% image_container width="300" %}}
![列のプロパティ](attachments/container-widgets/column-properties.png)
{{% /image_container %}}

レイアウト グリッド 列プロパティは次のセクションで構成されます。

* [一般的な](#column-common)
* [全般](#column-general)

### 4.1 共通セクション {#column-common}

{{% snippet file="refguide/common-section-link.md" %}}

### 4.2 一般セクション {#column-general}

#### 4.2.1 **Width** {#column-width}

このプロパティでは、列の幅を定義できます。

For *web* pages, it is divided into **Desktop Width**, **Tablet Width**,and **Phone Width** which allows you to define column width per device type.

*ネイティブ* ページには、 **Width** というプロパティがあります。

**** プロパティには、次のオプションが含まれています。

* **自動入力** - 列の空き容量を取得します (例えば、列が1つある場合)。 列全体に渡って2列分割されます)
* **自動フィットコンテンツ** - 列のサイズをコンテンツに自動的に合わせる
* **マニュアル** - 列のサイズを手動で設定できます

列幅を使用すると、レイアウトをより柔軟に、さまざまなタイプのデバイスに適応できます。

たとえば、1 行と 2 列のレイアウト グリッドがあります。画像は 1 列にあります。 細かいことが書かれています

For the *desktop* and *tablet*, you might want to set the first column with a picture to **Auto-fit content** and and the second one to **Auto-fill**, this way the first column will adjust to the size of the picture, while the second one will take the rest of the row:

![レイアウト例、デスクトップ](attachments/container-widgets/layout-example-desktop.png)

For *phone*, it can be a good idea to place two columns one under another, setting them to **Manual** width of *12* (for more information on the column size property, see the [Size](#column-size) section). この場合、2 列目は自動的に別の行にラップされます。

 {{% image_container width="300" %}}
![携帯電話のレイアウト例](attachments/container-widgets/layout-example-phone.png)
{{% /image_container %}}

下の写真では、上記の2列の設定を確認できます。

![](attachments/container-widgets/column-settings-example.png)

#### 4.2.2 **サイズ** {#column-size}

**Size** オプションは、 [width](#column-width) が **Manual** に設定されている場合にのみ表示されます。

この設定では、デスクトップ、タブレットの列サイズを手動で設定できます。 または、対応するプロパティを使用して携帯電話: **デスクトップサイズ**, **タブレットサイズ**, **携帯電話サイズ**.

#### 4.2.3 垂直に揃え

**垂直揃え** プロパティは行の **縦方向揃え** プロパティを上書きし、個々の列の配置を設定します。

## 5 Basic アクションの実行

### 5.1 行または列の追加

新しい行を追加するには、次の操作を行います。

1. レイアウト グリッドで既存の行を選択します。

2. 右クリックして **** の上に行を挿入 または **下に行を挿入** を選択します:

    ![新しい行の追加](attachments/container-widgets/adding-row.png)

3. 列のレイアウトを選択します(列数と重みの列数)。

レイアウト グリッドに新しい行が追加されます。

新しい列を追加するには、次の操作を行います。

1. 新しい列を追加する列を選択します。
2. 右クリックして **Add column left** または **Add column right** を選択します。

新しい列が追加され、重量1が自動的に設定されます。

### 5.2 行に対するその他のアクション

新しい行を挿入するには、行を右クリックすると次のアクションを実行できます。

* **Move up** – moves a row up in the layout grid, you can use a shortcut for it  <kbd>Ctrl</kbd> + <kbd>↑</kbd>
* **Move down** – moves a row down in the layout grid, you can use a shortcut for it  <kbd>Ctrl</kbd> + <kbd>↓</kbd>

### 5.3 列に対するその他のアクション

新しい列を挿入するには、列を右クリックすると次のアクションを実行できます。

* **Move left** – moves a column left in the row, you can use a shortcut for it  <kbd>Ctrl</kbd> + <kbd>←</kbd>
* **Move right** – moves a column right in the row, you can use a shortcut for it  <kbd>Ctrl</kbd> + <kbd>→</kbd>
* **Row** - 列の行に対してアクションを実行できます

## 6もっと読む

* [ページ](page)
* [コンテナウィジェット](container-widgets)
* [ウィジェットに共通するプロパティ](common-widget-properties)
