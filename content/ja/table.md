---
title: "表"
parent: "container-widgets"
menu_order: 60
tags:
  - "studio pro"
  - "表"
  - "コンテナウィジェット"
  - "ウィジェット"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/table.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}テーブルウィジェットはネイティブのモバイルページではサポートされていません。
{{% /alert %}}

## 1つの紹介

表はページに構造を与えるために使用できます。 [行](table#rows)、列、 [セル](table#cells) を含みます。 各セルにウィジェットを含めることができます。

たとえば、テキストウィジェット、ロゴ、およびデータビュー情報を顧客レポートとして使用するテーブルを作成できます。

![](attachments/container-widgets/table.png)

## 2つのコンポーネント

テーブルは [行](#rows)、列、 [セル](#cells) で構成されます。

### 2.1 行とそのプロパティ {#rows}

テーブルには 1 つまたは複数の行を含めることができます。 各行に列が含まれており、列の数は行ごとに異なります。

行には以下のプロパティがあります。

* **クラス** - 複数のカスケードスタイルシート(CSS)クラスを指定できます。
* **スタイル** - 追加の CSS スタイルを指定できます
* **Visible** – ページから要素を非表示にすることができます

上記のプロパティの詳細については、ページエディターの [プロパティ](common-widget-properties) を参照してください。

### 2.2 セルとそのプロパティ {#cells}

表行または列の各セクションはセルと呼ばれます。 セルにウィジェットを含めることができます。

セルには、次のプロパティがあります。

* **Class** – allows you to specify one or more cascading style sheet (CSS) classes (for more information on this property, see [Properties Common in the Page Editor](common-widget-properties))

* **Style** – allows you to specify additional CSS styling (for more information on this property, see [Properties Common in the Page Editor](common-widget-properties))

* **セルタイプ** - セルの種類を示します。

  * **Normal** – データを含む通常のセル
  * **ヘッダー** – テーブルヘッダーセル

### 2.3 行に対するアクション

行上でアクションを実行するには、行を選択して右クリックします。 アクションのリストが開きます。

次のアクションを実行できます:

* **左に列を追加** - 選択した列の左に列を作成
* **列右に追加** - 選択した列の右に列を作成
* **左に移動** - 行の左に列を移動
* **右に移動** - 行の右に列を移動

### 2.4 列に対するアクション

列でアクションを実行するには、列を選択して右クリックします。 アクションのリストが開きます。

次のアクションを実行できます:

* **** の上に行を追加 - 選択した行の上に行を作成
* **下の行を追加** - 選択した行の下に行を作成
* **上へ移動** - 行を上へ移動
* **下へ移動** - 行を下へ移動

### 2.5 セルに対するアクション

セル上でアクションを実行するには、セルを選択して右クリックします。 アクションのリストが開きます。

次のアクションを実行できます:

* **ウィジェットの追加** - ウィジェットのリストを開き、選択したウィジェットをセルに追加
* **ビルディングブロックの追加** - ビルディングブロックのリストを開き、選択したウィジェットをセルに追加
* **** の上に行を追加 - 選択した行の上に行を作成
* **下の行を追加** - 選択した行の下に行を作成
* **左に列を追加** - 選択した列の左に列を作成
* **列右に追加** - 選択した列の右に列を作成
* **左マージ** - 選択したセルの左にセルをマージします。空のセルのみマージできます。
* **Merge right** – 選択したセルの右側にセルをマージします。空のセルのみマージできます。
* **Merge up** - 選択したセルの上にセルをマージします。空のセルのみマージできます。
* **Merge down** – 選択したセルの下にセルをマージします。空のセルのみマージできます。
* **Unmerge** - 結合されたセルを別々のセルに変換する
* **行の削除** – 選択した行を削除
* **列の削除** – 選択した列を削除

セルを右、左、上、下に統合するには、対応するアイコンをクリックすることもできます。

![アイコンを結合](attachments/container-widgets/merge-icons.png)

## 3つのプロパティ

以下の図に、テーブルプロパティの例を示します。

{{% image_container width="250" %}}![テーブルのプロパティ](attachments/container-widgets/table-properties.png)
{{% /image_container %}}

表のプロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)
* [公開範囲](#visibility)

### 3.1 一般的なセクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 3.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 3.3 一般セクション {#general}

#### 3.3.1 Width Unit

**幅単位** では、 [列幅](#column-widths) プロパティをパーセントまたはピクセルで設定するかを定義します。

| 値             | 説明                                                                        |
| ------------- | ------------------------------------------------------------------------- |
| 割合  *(デフォルト)* | **列の幅** プロパティはパーセンテージで指定されます。 サイズを変更すると、列は同じ相対的な幅を維持しながら、幅/幅が狭くなります。      |
| Pixels        | **列 幅** プロパティはピクセル単位で指定されます。 サイズを変更すると、ピクセル幅の列は同じサイズを維持します。自動列は広く/狭くなります。 |

#### 3.3.2 列幅 {#column-widths}

**列の幅** プロパティは、各列の幅を、セミコロンで区切られた数値のリストとして定義します。 **Width unit** (上記) は、これらの数値がパーセンテージまたはピクセルを意味するかどうかを決定します。

![幅の単位と列の幅](attachments/container-widgets/width-unit-and-column-widths.png)

幅の単位 **を** に *ピクセル*に設定すると、列の幅を以下に設定できます:

* **Auto** - 列は行の利用可能なスペースで均等に分割されています
* **Fixed** - 列が指定されたピクセル値を持っています

For example, you can you can have three columns of which the first is 200 pixels wide (*Fixed* width), the second is 100 pixels (*Fixed* width), and the last one is set to *Auto* which means that it will take up the rest of the space in the row.

### 3.4 表示セクション {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 4 続きを読む

* [ページ](page)
* [コンテナウィジェット](container-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)


