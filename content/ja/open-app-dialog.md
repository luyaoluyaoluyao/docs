---
title: "アプリを開く"
parent: "ファイルメニュー"
menu_order: 20
description: "アプリを開くフローとアプリを開くダイアログボックスについて説明します"
tags:
  - "studio pro"
  - "アプリを開く"
aliases:
  - /ja/refguide/open-project-dialog.html
---

## 1つの紹介

Mendix Studio Proでアプリを開くには、次のいずれかを実行します。

* **ファイル** > **アプリを開く**
* Studio Pro のランディングページで **アプリを開く** をクリックします

**アプリを開く** ダイアログボックスが開き、アプリの場所を選択できます。

![アプリを開く](attachments/file-menu/open-app.png)

アプリの場所の詳細については、 [アプリはどこに保存されていますか?](#location) セクションを参照してください。

アプリはチームサーバー、別のSVNサーバー、またはローカルディスク上に配置できます。 Team Serverまたは別のSVNサーバーからアプリを開くと、このアプリが既にダウンロードされているかどうかをStudio Proが確認します。 もしそうなら、それは単にそれを開きます。 そうでない場合は、最初にバージョン管理サーバーからアプリがダウンロードされます。

## 2 アプリはどこに保存されていますか? {#location}

この設定を使用して、アプリが保存されている場所を選択します。 This can be the [Team Server](#team-server), a [private server](#private-server), that is an SVN server other than the Team Server, or a [local disk](#local). ディスク上のアプリは、Team Serverまたは別のSVNサーバーにも保存できます。 この場合、 **チームサーバー**/**プライベートサーバー** オプションと **ローカルディスク** オプションを使用して開くことに違いはありません。

### 2.1 Mendix チームサーバー {#team-server}

開きたいチームサーバーアプリを選択し、開発ラインを選択します。

Mendix Team Serverの詳細については、 [Team Server](/developerportal/collaborate/team-server) を参照してください。

開発ラインの詳細については、 [バージョンコントロール](version-control) を参照してください。

### 2.2 プライベートサーバー {#private-server}

{{% alert type="info" %}}

The **Private server** option is only available when support for other SVN servers is enabled: **Edit** >**Preferences** > **Version Control** > **Enable private version control**.

{{% /alert %}}

In the **App repository address** field, enter the address of the app you want to open and press the **Connect** button to load development lines from the repository. 次に、開発を開始する開発ラインを選択します。

### 2.3 ローカルディスク {#local}

すでにディスク上にあるアプリを開くには、アプリファイルを指すだけです。

## 3 続きを読む

* [アプリパッケージをインポート](import-project-package-dialog)