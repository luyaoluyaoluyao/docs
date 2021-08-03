---
title: "アプリパッケージをインポート"
parent: "ファイルメニュー"
menu_order: 40
description: "format@@0 および format@@1 ダイアログ ボックスについて説明します。"
tags:
  - "studio pro"
  - "アプリパッケージをインポート"
---

## 1つの紹介

Mendixアプリパッケージ(*.mpk*)から新しいアプリを作成するには、appパッケージをインポートする必要があります。 新しいアプリは、バージョン管理サーバーまたはローカルディスクに保存することができます。

アプリパッケージをインポートするには、次の手順を実行します。

1. トップバーの **ファイル** メニューを選択してください > **アプリパッケージをインポート**

2. インポートしたい *.mpk* ファイルを参照します。

3.  **アプリパッケージのインポート** ダイアログボックスで関連するオプションを選択し、 **OK** をクリックします。 選択できるオプションの詳細については、以下のセクションを参照してください。

    ![format@@0ダイアログ ウィンドウをインポート](attachments/file-menu/import-project-package.png)

[アプリパッケージのエクスポート](export-project-package-dialog) を使用してアプリパッケージを作成できます。

## 2 アプリはどこに保存するべきですか?

この設定を使用して、アプリを保存する場所を選択します。 This can be the [Team Server](#team-server), a [private server](#private-server) (an SVN server other than the Team Server), or a [local disk](#local).

### 2.1 Mendix チームサーバー {#team-server}

Team Serverにアプリをアップロードするときは、新しいリポジトリを作成するか、既存のリポジトリにアップロードするかを選択できます。

#### 2.1.1 新しいMendix チームサーバー

Mendix Team Serverにアプリを保存することを選択すると、新しいTeam Serverアプリが作成されます。 新しいTeam Serverアプリとリポジトリの名前を **アプリ名** フィールドに入力する必要があります。

#### 2.1.2 既存のMendixチームサーバー

既存のリポジトリを使用する場合は、 **Team Server App** オプションでアプリを選択します。 これは既存のリポジトリが空の場合にのみ動作することに注意してください。

Mendix Team Serverの詳細については、 [Team Server](/developerportal/collaborate/team-server) を参照してください。

### 2.2 プライベートサーバー {#private-server}

{{% alert type="info" %}}

The **Private server** option is only available when support for other SVN servers is enabled: **Edit** >**Preferences** > **Version Control** > **Enable private version control**.

{{% /alert %}}

**App repository address** フィールドに、アプリをアップロードしたいリポジトリのアドレスを入力します。

### 2.3 ローカルディスク {#local}

新しいアプリをバージョン管理サーバーにアップロードする必要がない場合は、このオプションを選択します。 この場合、Studio Pro を実行しているコンピュータのローカルディスクにのみ保存されます。

## 3つのアプリディレクトリ

このフィールドを使用して、アプリのアプリファイルを格納するディレクトリを選択します。 バージョンコントロールが有効な場合。 提案された名前は *-main* で終わり、これがアプリの主要な開発ラインになります。

## 4 続きを読む

* [チームサーバー](/developerportal/collaborate/team-server)
* [アプリパッケージのエクスポート](export-project-package-dialog)