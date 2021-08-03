---
title: "コントロール バー"
parent: "グリッド"
menu_order: 30
tags:
  - "studio pro"
  - "コントロールバー"
  - "追加ボタン"
  - "すべてのボタンの選択を解除"
  - "CSVボタンにエクスポート"
  - "グリッドアクションボタン"
  - "グリッド新しいボタン"
  - "削除ボタン"
  - "検索ボタン"
  - "選択ボタン"
  - "すべてのボタンを選択"
  - "データグリッド"
  - "テンプレートグリッド"
  - "参照セットセレクター"
  - "コントロールバーボタン"
aliases:
  - /refguide8/add-button.html
  - /refguide8/deselect-all-button.html
  - /refguide8/export-to-csv-button.html
  - /refguide8/export-to-excel-button.html
  - /refguide8/grid-action-button.html
  - /refguide8/grid-new-button.html
  - /refguide8/remove-button.html
  - /refguide8/search-button.html
  - /refguide8/select-all-button.html
  - /refguide8/select-button.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/control-bar.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

A control bar of a [template grid](template-grid), [data grid](data-grid), and [reference set selector](reference-set-selector) allows you to manipulate the objects displayed by means of buttons. By default, both grids will be created with [Search](#search-button), [New](#create-button), [Edit](#grid-action-button), and [Delete](#grid-action-button) buttons in the control bar:

![データグリッドコントロール バー](attachments/data-widgets/control-bar-example.png)

コントロールバーには、選択オプションとスプレッドシートのエクスポートボタンのほか、カスタムアクション用のマイクロフローボタンも含めることができます。

## 2コントロールバーボタン

コントロールバーボタンのほとんどのプロパティは、ボタンウィジェットのプロパティと同じです。 ボタンのプロパティの詳細については、 [ボタンのプロパティ](button-properties) を参照してください。

以下のセクションでは、各コントロールバーボタンの目的と、それぞれのプロパティがある場合について説明します。

### 2.1 検索ボタン {#search-button}

**検索バーの切り替え** ボタン (既定の図表番号 **検索**) は、 [検索バー](search-bar) を開いたり非表示にしたりします。 グリッドの **検索バー** プロパティが *ボタン (最初に開く)* または *ボタン (最初に閉じる)* に設定されている場合にのみ存在します。

{{% alert type="info" %}}
[リファレンスセットセレクタ](reference-set-selector) では、デフォルトでは検索フィールドが設定されていません。 検索フィールドの詳細については、 [検索バー](search-bar) を参照してください。
{{% /alert %}}

### 2.2 ボタンを追加 {#add-button}

**Add** ボタンは [reference set selector](reference-set-selector) でのみ使用できます。 このボタンを使用すると、ユーザーは参照セットセレクターに追加する必要があるオブジェクトを選択できます。

#### 2.2.1 ページ

**ページ** プロパティは、このボタンをクリックした後にユーザーに表示されるページを示します。 ユーザーは、このページを使用して、参照セットセレクターに追加する必要があるオブジェクトを選択できます。 このページには、データグリッド、テンプレートグリッド、または参照セットセレクタと同じエンティティに接続されたリストビューが含まれている必要があります。

既存のページを使用することも、適切なページを生成することもできます。

1. 追加ボタンを右クリックし、 **ページの生成…** を選択します。
2. ページの **New** を選択します。

両方のオプションを使用すると、追加ボタンで使用するための正しい形式のページを作成できます。 もちろん、生成されたページを自分の要件に合わせて編集することもできます。

[Show a Page](on-click-event#show-page) section of *On Click Event & Events Section* を参照してください。 選択ページには [ポップアップ レイアウト](layout#layout-type) が必要です。

### 2.3 作成ボタン {#create-button}

**Create** ボタン (デフォルトの図表番号 **New**) により、エンドユーザーはグリッドまたは参照セットセレクタで新しいオブジェクトを作成できます。

#### 2.3.1 エンティティ

**Entity** プロパティは、このボタンでインスタンスを作成するエンティティを決定します。 グリッドまたは参照セットセレクターに接続されているエンティティに特殊化がない場合。 ページエディターが自動的にこのプロパティを設定します。 それ以外の場合は、専門分野のいずれかを選択する必要があります。

たとえば、エンティティ *車両* と2つの専門分野があります: *自転車* と *車*。 In a grid, when you select *Vehicle* as a data source, you have to specify whether a *Vehicle*, a *Bicycle* or a *Car* will be created when the **Create** button is clicked. 3つの **新しい** ボタンを持つこともできます。

### 2.4 アクションボタン {#grid-action-button}

アクションボタンは、マイクロフローの呼び出しやページを開くなど、さまざまなアクションを実行できるボタンです。 **編集** と **削除** ボタンは、データグリッドとテンプレートグリッドコントロールバーでデフォルトで作成されたアクションボタンです。 アクションボタンの詳細については、 [ボタンウィジェット](button-widgets) を参照してください。

### 2.5 削除ボタン {#remove-button}

**Remove** ボタンは、リファレンスセットセレクタ固有のボタンです。 このボタンを使用すると、エンドユーザーはリファレンスセットセレクターに追加されたオブジェクトを削除できます。 リファレンスセットセレクタの詳細については、 [リファレンスセットセレクタ](reference-set-selector) を参照してください。

### 2.6 ボタンの選択 {#select-button}

**Select** ボタンは、参照セレクタまたは参照セットセレクタのオブジェクトを選択するために使用されるグリッドの行の選択を確認します。 このため、 **Select** ボタンは、参照セレクタに接続されているページまたは参照セットセレクタの **Add** ボタンにのみ配置できます。

### 2.7 すべてのボタンを選択 {#select-all-button}

**Select all** ボタンを使用すると、エンドユーザはグリッド内のすべてのオブジェクトまたは参照セットセレクタを選択できます。

#### 2.7.1 選択タイプ

**選択タイプ** プロパティにより、 **すべて選択** ボタンが現在のページ上のオブジェクトを選択するかどうかを決定します。 またはすべてのページ上のオブジェクト:

| 値                 | 説明                                       |
| ----------------- | ---------------------------------------- |
| ページ *(デフォルト)* を選択 | このボタンをクリックすると、現在のページ上のすべてのオブジェクトが選択されます。 |
| すべて選択             | このボタンをクリックすると、すべてのオブジェクトが選択されます。         |

{{% alert type="warning" %}}

Due to technical limitations, a button with the **Select all** selection type cannot be combined with [Remove](#remove-button), [Delete](#grid-action-button), or [Select](#select-button) buttons.

An **Edit** button always behaves as if the selection type is **Select page**, regardless of the actual settings of the **Select all** button that had been used to select objects.

{{% /alert %}}

### 2.8 すべてのボタンの選択を解除 {#deselect-all-button}

**** ボタンをクリックすると、ユーザーはグリッド内のすべての行または参照セットセレクタの選択を解除できます。

### 2.9 Excel ボタンにエクスポート {#export-to-excel-button}

**Excel にエクスポート** ボタンを使用すると、エンドユーザーはグリッドの内容や参照セットセレクタを Excel ファイルにエクスポートできます。

{{% alert type="info" %}}

Excel エクスポート関数は、 [XPath データ ソース](xpath-source) を持つリストウィジェットでのみ使用することができます。

検索フィールドやソートに使用する制約もエクスポートされます。

{{% /alert %}}

#### 2.9.1 行の最大数

**行の最大数** プロパティは、エクスポート時にデータ グリッドに存在できる行の最大数を示します。 エンドユーザーが大量のデータをエクスポートしないようにすると、サーバーに負荷がかかる可能性があります。

#### 2.9.2 日付のエクスポート形式

**日付エクスポートフォーマット** プロパティは、エクスポートされる書式の日付を定義します。 可能なオプションは以下のとおりです:

* **日付値** *(デフォルト)*  - 日付値は実際の日付としてエクスポートされます。 Excel日付関数の並べ替えなどを利用できるようにします
* **テキスト** - 日付の値は、データグリッドに表示されるように正確にエクスポートされます

{{% alert type="warning" %}}

**日付値**を選択すると、日付は Windows アカウントのタイムゾーンにのみ表示されます。 Excelは特定のタイムゾーンの定義をサポートしていないためです。

{{% /alert %}}

### 2.10 CSV ボタンにエクスポート {#export-to-csv-button}

**CSV にエクスポート** ボタンを使用すると、エンドユーザーはグリッドの内容や参照セットセレクタを CSV ファイルにエクスポートできます。

{{% alert type="info" %}}

CSV 関数へのエクスポートは、 [XPath データ ソース](xpath-source) を持つリストウィジェットでのみ使用することができます。

検索フィールドやソートに使用する制約もエクスポートされます。

{{% /alert %}}

#### 2.10.1 小数点の区切り

**小数点セパレーター** は小数部位を小数部位全体から区切るために使用される文字列である。

デフォルト: *.*

#### 2.10.2 グループセパレーター

**グループセパレータ** は、大きな数字でグループを分けるために使われる文字列です。

デフォルト: *,*

#### 2.10.3 区切り文字

**区切り文字** は、結果の CSV ファイルの値を区切るために使用される文字列です。

デフォルト: *;*

#### 2.10.4 最大行数

**行の最大数** プロパティは、エクスポート時にデータ グリッドに存在できる行の最大数を示します。 エンドユーザーが大量のデータをエクスポートしないようにすると、サーバーに負荷がかかる可能性があります。

#### 2.10.5 Excelセパレータのヒントを生成

**Excel セパレーターヒントの生成** プロパティは、区切り文字が何であるかを Excel に通知する CSV ファイルヘッダーに追加されます。 これにより、Excelやローカライゼーションとの互換性の問題が解決されます。

#### 2.10.6 グリッドの日付フォーマットを使用

**[グリッド日付書式] プロパティ** が有効な場合、列の日付書式が使用されます。 このプロパティが無効になっている場合、Excel が日付として認識する形式が使用されます (yyyy-MM-dd)。

## 3 続きを読む

* [ボタンのプロパティ](button-properties)
* [データグリッド](データグリッド)
* [テンプレートグリッド](template-grid)
* [参照セットセレクター](reference-set-selector)