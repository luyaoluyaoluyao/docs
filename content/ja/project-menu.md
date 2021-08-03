---
title: "プロジェクトメニュー"
parent: "menus"
description: "Studio Pro のプロジェクトメニューについて説明します。"
menu_order: 30
tags:
  - "Studio Pro"
  - "プロジェクトメニュー"
  - "トップ バー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/project-menu.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**プロジェクト** メニューで、プロジェクトとデプロイメントに接続されている設定を表示または操作できます。 たとえば、デプロイメントパッケージを作成できます。

{{% image_container width="300" %}}![プロジェクトメニュー](attachments/project-menu/project-menu.png)
{{% /image_container %}}

## 2つのツール

Under **Project** > **Tools**, you can find settings on updating widgets, button icons, and layouts, checking widgets, and converting your classes to **Design** properties.

![ツール](attachments/project-menu/tools.png)

### 2.1 バッチ更新ボタンアイコン

**Batch Update Button Icons** オプションを使用すると、1つのバッチ処理で多くのボタンアイコンを更新できます。

### 2.2 バッチ更新レイアウト

**一括更新レイアウト** オプションを使用すると、一括処理で多数のページのレイアウトを更新できます。

### 2.3 ウィジェットの更新 {#update-widgets}

**Update Widgets** オプションは、アプリで使用しているウィジェットの現在のバージョンを表示します 最新バージョンのウィジェットとアップデートオプションがあります

### 2.4 ウィジェットの確認

**Check Widgets** オプションは、アプリに実装したウィジェットが正しくビルドされていることを確認します。

### 2.5 クラスをデザインプロパティに変換する

**クラスをデザインプロパティに変換する** オプションを使用すると、ウィジェット内のクラスをデザインプロパティに変換して、ウィジェットのスタイルの変更を支援できます。 詳細については、 [Native Mobile Styling](/howto8/mobile/native-styling) の実装方法を参照してください。

## 3 プロジェクトディレクトリの同期

**[プロジェクト ディレクトリの同期** ] オプションは、必要に応じて、プロジェクト ディレクトリ (リソース、ウィジェット、テーマなど) 内にフォルダーを作成します。 また、現在ウィジェットフォルダ内にあるウィジェットパッケージも読み込みます。 たとえば、ウィジェットフォルダにウィジェットを追加する場合。 **Toolbox** に表示されるように、プロジェクトディレクトリを同期する必要があります。

ショートカットキー: <kbd>F4</kbd>

## 4 プロジェクトディレクトリをエクスプローラーに表示

The **Show Project Directory in Explorer** option shows the directory that contains the project file (*.mpr*) and other assets such as resources and Java actions in Windows Explorer. デフォルトでは、ディレクトリは **MyDocuments** セクションにあります。

以下のディレクトリは、アプリのスタイルをカスタマイズしたり、カスタム ウィジェットや Java アクションを追加したりするのに役立ちます。

* **テーマ** - アプリケーションのスタイル設定に使用できる *.css* ファイルを保存します
* **javasource** - JavaScript の動作を保存します。
* **ウィジェット** – ウィジェットを保存

## Eclipse 用にデプロイする

**Eclipse 用のデプロイ** オプションは、プロジェクトをデプロイディレクトリにデプロイします。 Java スタブが生成され、Eclipse 内で編集を開始できます。 このアクションは Java アクションをコンパイルしません。 Java アクションを記述していて、Eclipse を使用してコンパイルおよびデバッグしたい場合に使用します。

ショートカットキー: <kbd>F6</kbd>

## 6 展開パッケージを作成

The **Create Deployment Package** option creates a Mendix Deployment Archive package (*.mda*) that contains all necessary files to run the project. これは、プロジェクトを Windows サーバーまたはカスタム Mendix Cloud にデプロイする場合に使用できます。

ショートカットキー:  <kbd>F7</kbd>

「デプロイメントパッケージの作成」ダイアログ・ボックスに表示される設定の詳細については、「 [デプロイメント・パッケージの作成](create-deployment-package-dialog)」を参照してください。

## 7つのデプロイディレクトリをきれいにする

**デプロイメント ディレクトリ** オプションは、デプロイメントディレクトリをクリアします。

## 8 ライセンスクラウドノードにデプロイする {#deploy}

**ライセンスクラウド ノード** にデプロイするオプションは、Team Serverプロジェクトの最新のコミット済みリビジョンを関連付けられたMendix Cloudノードにデプロイします。

ショートカットキー:  <kbd>Ctrl</kbd> + <kbd>F5</kbd>

{{% alert type="warning" %}}
[Mendix Studios Target](/developerportal/deploy/studio-deployment-settings#target) を設定する必要があり、デプロイユーザーは設定されたターゲットに対するトランスポート権限を持つ必要があります。
{{% /alert %}}

このオプションを使用する方法の詳細については、 [クラウドにデプロイ](deploy-to-the-cloud-dialog) を参照してください。

## 9 続きを読む

* [Studio Pro Overview](studio-pro-overview)
* [配置](/developerportal/deploy)
