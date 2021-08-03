---
title: "ペインの変更"
parent: 表示メニュー
menu_order: 10
description: "Mendix Studio Proの変更ペインについて説明します。"
tags:
  - "Studio Pro"
  - "変更"
  - "変更ペイン"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/changes-pane.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

バージョン管理が有効になっているプロジェクト (Team Serverまたは他のSVNサーバーを持つプロジェクト) の場合。 **変更** ペインには、最後のコミット以降のアプリのローカル変更が表示されます。 変更をコミットしたり、最新のリビジョンに更新したり、そこから履歴を表示することができます。

このペインは以下で構成されています:

* トップバー [](#top-bar) には、 **戻る**、 ****、 **タスク**などの様々なボタンが含まれています。
* [トップレベル](#top-level) には、ウィジェットが削除されたページなど、変更されたドキュメントの一覧が表示されます。
* ペインの [ズームインレベル](#zoomed-in-level) は 2 つのグリッドに分割されます。 左側のグリッドにある要素と、右側のグリッド内で選択した要素のプロパティが変更または競合しています。

## 2つのトップバー {#top-bar}

**変更** ペインのトップレベルの上部のバーは、さまざまなボタンで構成されています。

![変更ペインの上部バー](attachments/changes-pane/changes-top-bar.png)

ボタンを使用すると、次の操作を実行できます。

* **戻る** – 1つ上のレベルに戻る; 最上位のレベルでは、このボタンは無効になっています
* **** に移動 - ズームインレベルを開き、選択したドキュメントを開く
* **タスク** - 変更を最新のコミットに戻す、競合を解決するなど、特定のアクションを実行できます
* **Update** – retrieves latest changes from the repository (for more information on the update concept, see the [Update](version-control#update) section in *Version Control*)
* **Commit** – commits your changes to the repository and starts a new revision (for more information on the commit concept, see the [Commit](version-control#commit) section in *Version Control*)
* **History** – opens the **History** dialog box that shows the changes made on the current development line of the project (for more information on history, see [History](history-dialog))

**Back** と **** に移動するボタンは、すべてのレベルで共通です。 他のボタンは特定のボタンにのみ適用されます。

## 3つのトップレベル {#top-level}

**変更点** ペインの最上位レベルは、変更された文書をリストするグリッドです。たとえば、ページやナノレベルなどです。

![変更ペインの最上位レベル](attachments/changes-pane/changes-top-level.png)

グリッドには、次の項目に関する情報が含まれています:

* **ステータス** – 文書に適用される変更の種類を表示します。 ステータスは次のいずれかになります:
  * **追加** - 新しいドキュメントが作成されました。緑色の円で示されます。
  * **Modified** – 要素の追加や削除、要素のプロパティの変更など、既存のドキュメントへの変更が行われました。 黄色の丸で示されています
  * **Deleted** – ドキュメントが削除されました; マイナスの赤い丸印で示されます
  * **競合している** - 文書には競合する変更が含まれています。感嘆符付きの赤い丸で示されています。
* **アイテム** - 変更ドキュメントの名前を示します
* **モジュール** - 変更された文書があるモジュール
* **詳細** - 競合する変更がある場合など、状況の詳細を含めることができます

## 4 ズームイン レベル {#zoomed-in-level}

次のいずれかを実行することで、変更または競合するドキュメントにズームできます。

* トップレベルのグリッド内の線をダブルクリックします
* **** ボタンをクリックします
* <kbd>Enter</kbd> を押します

ズームインを終了するには、 **Back** ボタンをクリックするか、 <kbd>Backspace</kbd> を押します。

ズームインレベルには2種類があります。

* [変更されたドキュメント用](#modified)
* [競合するドキュメントのため](#conflicts)

それぞれ独自のボタンが含まれています。

### 4.1 変更されたドキュメントのズームインレベル {#modified}

変更されたドキュメントのズームインレベルは、左側に要素があり、右側にプロパティが変更された2つのグリッドに分割されます。 要素のプロパティが変更されていない場合、例えば要素が追加または削除されたとき、右のグリッドは空になります:

![表示するプロパティがありません](attachments/changes-pane/element-added.png)

このレベルのツールバーには、次のボタンがあります。

* **戻る** – トップレベルに戻る
* **** に移動 – 変更された要素に直接移動します
* **純粋に視覚的な変更を表示する** – ドメインモデル内の新しい場所にエンティティをドラッグするなど、視覚的な変更を表示します

グリッドの左側には、次の列があります。

* **要素** – 変更された要素の名前
* **Mine** – 現在の開発ラインの変更状況を示します

右側のグリッドには次の列が含まれています。

* **プロパティ** - 変更されたプロパティ
* **オリジナル** – 元のプロパティ値
* **Mine** – 現在の開発ラインで行われたプロパティの変更

### 4.2 競合するドキュメントのズームインレベル {#conflicts}

競合するドキュメントのズームインレベルは、左側に要素があり、右側に矛盾するプロパティがあり、2つのグリッドに分割されます。

このレベルのツールバーには、次のボタンがあります。

* **戻る** – トップレベルに戻る
* **** に移動 - 選択した要素に直接移動します
* **純粋に視覚的な変更を表示する** – ドメインモデル内の新しい場所にエンティティをドラッグするなど、視覚的な変更を表示します
* **競合の表示** – 競合の詳細を表示します。 このレベルに最初にズームするときにデフォルトで選択されます。
* **Show Changes in mine** – it shows changes to a document on a current development line (for more information on how to solve conflicts, see the [Dealing With Conflicts](using-version-control-in-studio-pro#conflicts) section in *Using Version Control in Studio Pro*)
* **Show Changes in theirs** – it shows incoming changes to a document from another development line (for more information on how to solve conflicts, see the [Dealing With Conflicts](using-version-control-in-studio-pro#conflicts) section in *Using Version Control in Studio Pro*)

    {{% alert type="info" %}}**Show Conflicts**, **Show Changes in mine**, and **Show Changes in theirs** described above are toggles, and each selection de-selects the other two.
    {{% /alert %}}

グリッドの左側の列は、ツールバーのトグルボタンによって異なります。

グリッドの左側には、 **Show Conflicts** トグルが有効になっているときに次の列が含まれています:

* **要素** – 変更された要素の名前
* **Theirs** – 別の開発ラインでの変更の状況
* **Mine** – 現在の開発ラインの変更状況を示します

    ![競合グリッド](attachments/changes-pane/conflict-grid.png)

グリッドの左側には、 **地雷の変更を表示** のトグルが有効になっているときに次の列が含まれています:

* **要素** – 変更された要素の名前
* **Mine** – 現在の開発ラインの変更状況を示します

    ![競合グリッド](attachments/changes-pane/changes-in-mine-grid.png)

グリッドの左側には、 **変更を表示** のトグルが有効になっているときに次の列が含まれています:

* **要素** – 変更された要素の名前
* **Theirs** – 他の開発ラインの変更状況を示します

    ![競合グリッド](attachments/changes-pane/changes-in-merge-end-grid.png)


右側のグリッド上の列は、左側でどのような競合要素が選択されているかによって異なります。

左側で選択されたアイテムが競合している場合、両側が同じ要素を変更します。 すると、グリッドの右側に次の列が表示されます。

* **プロパティ** - 変更されたプロパティ
* **オリジナル** – 元のプロパティ値
* **Theirs** – 他の開発ラインで行われたプロパティの変更
* **Mine** – 現在の開発ラインで行われたプロパティの変更

左側で選択された項目が競合している場合、片側で要素が変更され、もう片側で削除されます。 すると、グリッドの右側に次の列が表示されます。

* **プロパティ** - 変更されたプロパティ
* **Theirs** – 元のプロパティ値
* **Mine** – 現在の開発ラインで行われたプロパティの変更

## 5 続きを読む

* [Studio Pro Overview](studio-pro-overview)
* [バージョン管理](version-control) 
