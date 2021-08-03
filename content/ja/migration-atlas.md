---
title: "アトラスUI変更のトラブルシューティング"
parent: "moving-from-7-to-8"
menu_order: 20
description: "このドキュメントでは、Mendix 7からMendix 8にプロジェクトを移行する際のスタイリングを修正する方法を説明します。"
tags:
  - "ウィジェット"
  - "テーマ"
  - "クラス"
  - "Atlas"
  - "アトラスUI"
  - "スタイル"
  - "SAS"
  - "CSS"
---

## 1つの紹介

Mendix 8 にアップグレードすると、ウィジェットの DOM 構造が変更されます。 これは、Sass のスタイルが期待どおりに機能しなくなることを意味します。 このドキュメントでは、Mendix 8とあなたのテーマを互換性があるようにすることができます。

このドキュメントの各セクションはアプリに適用されますが、いくつかのセクションは *適用されません*。 あなたの場合にセクションが適用されない場合は、それをスキップすることができます。

{{% alert type="warning" %}} **Atlas_UI_Resource モジュール**に任意のコンテンツを追加した場合は、そのコンテンツをモジュールから移動する必要があります。 そうでない場合は、上書きされます。{{% /alert %}}

アプリが変更されていないAtlas UIリソースを使用している場合、Mendix 8にアプリをアップグレードすると、Atlas UIリソースが自動的にバージョン2.1に更新されます。 カスタムフォルダに変更を加えなかった場合は、このガイドの残りの部分をスキップすることができます。

変更されていないAtlas UIリソースを使用していて、カスタムフォルダに変更を加えた場合。 これらの変更は保存され、新しいAtlas UIバージョンで使用されます。 この場合、一貫性のエラーが表示されます。 このエラーを解決するために、以下の [変更されたカスタムフォルダ](#modified) セクションで説明されている手順に進みます。

AtlasのUIリソースの変更バージョンを使用している場合、Mendixは自動的に更新できません。 この場合、一貫性のエラーが表示されます。 テーマの問題を解決するには、Atlasを自分でアップデートする必要があります。

以下の手順に従って、Atlas UI Resources モジュールのアップグレードを開始してください。

1. 最新の [Atlas UI Resources](/appstore/modules/atlas-ui-resources) モジュール (v2.0.0 以上) をダウンロードします。
2. このモジュールをアプリにインポートし、古いリソースモジュールを置き換えます。 これにより、リソースモジュール内のレイアウト、ページテンプレート、およびビルディングブロックが上書きされます。 古いリソース・モジュールに関連する **テーマ** フォルダは **theme_old** に移動されます。 最新の変更を加えた新しい **テーマ** フォルダを取得します。 ここから、カスタム スタイルを持っているかどうかに応じて、次のいずれかを選択する必要があります。<br />
    * If you did not change anything in the old **theme** folder, you can safely remove **theme_old** and leave everything else as is. スタイリングが機能し、このドキュメントを参照することはできます。 <br />
    * 古い **テーマ** フォルダで何か変更があった場合は、スタイルを整列させるために手作業で作業する必要があります。 あなたのニーズに応じて何をすべきかを決定するには、以下の情報を参照してください。

## 2 古いテーマフォルダを新しいものに統合

Mendix 7 から Mendix 8 に移行する場合は、いくつかのガイドラインを遵守しつつ、 **theme_old** を **テーマ** に統合する必要があります。 どのガイドラインに従わなければならないかは、特定のプロジェクトによって異なります。 ユニークなケースに基づく手順については、以下のサブセクションを参照してください。

{{% alert type="info" %}}If you customized any widget where the DOM structure has changed, consult [Troubleshoot DOM Changes when Migrating to Mendix 8](migration-dom-issues) to ensure your custom styling works.{{% /alert %}}

### 2.1 HTMLファイルの操作

HTMLファイルを変更した場合は、以下の手順を参照してください。 ない場合は、このサブセクションを無視してください。

**index\*.html** ファイルを変更した場合は、以下の操作を行ってください。

* 古いファイルで行ったのと同じ変更を新しいHTMLファイルに適用します
* **bootstrap.min.css**, **bootstrap-rtl.min.css**, および **mxui.css** のインポートがないことを確認してください
* **styles/css/lib/lib.css** をもうインポートしないようにしてください
* `<link rel="stylesheet" type="text/css" href="styles/web/css/main.css?{{cachebust}}">` または `{{themecss}}` を `<head></head>` タグの中に入れていることを確認してください

**login\*.html** ファイルを変更した場合は、以下の操作を行います。

* 古いファイルで行ったのと同じ変更を新しいHTMLファイルに適用します
* **bootstrap.min.css** と **mxui.css** のインポートが失われていることを確認します (そうでない場合は削除してください)
* `styles/css/lib/lib.css` をもうインポートしないようにしてください
* `<link*rel*="stylesheet" *type*="text/css" *href*="styles/web/css/main.css?{{cachebust}}">` または `{{themecss}}` `<head></head>` タグの中に配置する

### 2.2 JSON ファイルの操作

*settings.json* または *components.json* ファイルを変更した場合は、以下の手順を参照してください。 ない場合は、このサブセクションを無視してください。

#### 2.2.1 デザインプロパティ

テーマでデザインプロパティを変更した場合は、新しいAtlas UIに手動で統合する必要があります。

デザインプロパティは `settings.json` ファイルの *designProperties* セクションに保存されます。

新しいAtlas UIテーマに移動されていないカスタムデザインプロパティがある場合。 一貫性エラー(エラーコード **CE6083**)が表示され、プロジェクトのデザインプロパティがないことを通知します。

新しいAtlas UIテーマの *settings.json* ファイルにカスタムデザインプロパティを移動してください。

### 2.2.2 追加の CSS ファイル

{{% alert type="warning" %}}
`cssFiles` の変更は推奨されません。 カスタム CSS ファイルを *theme/styles/web/sass/app/_custom.scss* ファイルに移動することを検討してください。
{{% /alert %}}

`settings.json` で *cssFiles*を変更した場合、新しい *settings.json* ファイルに変更を統合する必要があります。

デフォルトでAtlasのUIバージョン1には2つのファイルが含まれています:

```javascript
"cssFiles": [
    "styles/css/lib/lib.css",
    "styles/css/custom/custom.css"
],
```

Atlas 2.1.0, しかしながら, 単一のファイルを使用します:

```javascript
"cssFiles": [
    "styles/web/css/main.css"
],
```

`cssFiles` セクションにファイルが追加される場合は、新しいテーマの *settings.json* ファイルに追加する必要があります。

*components.json*でハイブリッドモバイルアプリのインポートを変更した場合は、以下の操作を行ってください。

* 古い *components.json* を新しいフォルダに手動で統合
* *bootstrap.min.css*, *bootstrap-rtl.min.css*を確認し、 *mxui.css* のインポートがなくなっている場合は削除してください)
* *styles/css/lib/lib.css* が *styles/web/css/main.css に変更されていることを確認します*

### 2.3 カスタムフォルダファイルの操作

カスタムフォルダを変更した場合は、以下の手順を参照してください。 ない場合は、このサブセクションを無視してください。

If you added, removed, or changed custom variables in a custom folder, copy your content from *theme_old/styles/sass/custom/_custom-variables.scss* to *theme/styles/web/sass/app/_custom-variables.scss*.

カスタム フォルダーにカスタム スタイルを追加または変更した場合は、 *theme_old/styles/sass/custom/* から *theme/styles/web/sass/app/* にコンテンツまたはファイルをコピーします。
* この場合、古い *custom.scss* ファイルが *_custom.scss に改名されていることを確認してください*

### 2.4 Libフォルダファイルの操作

*styles/sass/lib* フォルダを変更した場合は、以下の手順を参照してください。 ない場合は、このサブセクションを無視してください。

*styles/sass/lib* フォルダ内のファイルを変更した場合は、以下の操作を完了してください::

* ファイルの内容や名前を変更した場合 新しいファイルと新しいテーマフォルダに同じ変更を加える必要があります (Mendix 8 [DOM 変更](migration-dom-issues) を念頭に置いてください)
* ファイルを削除した場合、アクションは必要ありません

*lib/base* フォルダにファイルを追加した場合、 *theme_old/styles/sass/lib/base/* から *theme/styles/web/sass/core/base/* へそのファイルをコピーしてください。 次のアクションを完了する必要があります：

* *theme/styles/web/sass/main.scss* にアルファベット順の `Base` グループにファイルをインポート

*lib/components* フォルダにファイルを追加した場合、 *theme_old/styles/sass/lib/components/* から *theme/styles/web/sass/core/widgets/* にそのファイルをコピーします。 次の操作も完了する必要があります。

1. *theme/styles/web/sass/main.scss* に、アルファベット順の `ウィジェット` グループの下にファイルをインポートします
2. すべてのデザインプロパティと追加のクラスをファイルから切り取って（後で貼り付ける）、デフォルトのスタイルのみを残します
3. 同じ名前の *theme/styles/web/sass/helpers/* で新しいファイルを作成する
4. この新しいファイルにこれらのデザインプロパティと追加クラスを貼り付けます
5. 上記のインポートの下で *theme/styles/web/sass/main.scss* にファイルをインポート

*lib/customwidgets* フォルダにファイルを追加した場合は、 *theme_old/styles/sass/lib/customwidgets/* から *theme/styles/web/sass/core/widgetscustom/* へコンテンツをコピーします。 次のアクションを完了する必要があります：

* *theme/styles/web/sass/main.scss* に `カスタムウィジェット` グループをアルファベット順にインポートします

*lib/buildingblocks* フォルダにファイルを追加した場合、そのファイルを *theme_old/styles/ss/lib/buildingblocks/* から *theme/styles/web/sass/resources/atlas_resources_default/buildingblocks* にコピーします。 次のアクションを完了する必要があります：

* *theme/styles/web/sass/main.scss* のアルファベット順の `Building Blocks` グループの下にファイルをインポートします

*lib/layouts* フォルダにファイルを追加した場合、 *theme_old/styles/ss/lib/layouts/* から *theme/styles/web/sass/resources/atlas_default/layouts* にそのファイルをコピーします。 次のアクションを完了する必要があります：

* *theme/styles/web/sass/main.scss* に `レイアウト` グループをアルファベット順にインポートします。

カスタムまたは追加された Sass ファイルが *styles/web/sass/main.scss* または *styles/web/sass/app/_custom.scss* でインポートされていることを確認してください。

上記のガイダンスで問題をトラブルシューティングした後、以下の手順を実行して移行したアプリをテストします。

### 2.5 変更されたカスタムフォルダの操作 {#modified}

1. Sass を CSS に再コンパイルします。
2. アプリをテストして、すべてが期待どおりに動作するかどうかを確認します。
3. *theme_old* を削除する。

## 3 続きを読む

* [DOM の変更のトラブルシューティング](migration-dom-issues)
* [アトラスUI](/howto8/front-end/atlas-ui)
