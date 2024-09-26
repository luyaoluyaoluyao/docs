---
title: "プロジェクトパッケージのインポート"
parent: "ファイルメニュー"
menu_order: 40
description: "「プロジェクトパッケージのインポート」プロセスと「プロジェクトパッケージのインポート」ダイアログ・ボックスについて説明します。"
tags:
  - "studio pro"
  - "プロジェクトパッケージをインポート"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/import-project-package-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

Mendixプロジェクトパッケージ(*.mpk*)ファイルから新しいアプリケーションを作成するには、プロジェクトパッケージをインポートする必要があります。 新しいアプリは、バージョン管理サーバーまたはローカルディスクに保存することができます。

プロジェクトパッケージをインポートするには、次の手順を実行します。

1. トップバーの **ファイル** メニューを選択してください > **プロジェクトパッケージをインポート**

2. インポートしたい *.mpk* ファイルを参照します。

3.  **プロジェクトパッケージのインポート** ダイアログボックスで関連するオプションを選択し、 **OK** をクリックします。 選択できるオプションの詳細については、以下のセクションを参照してください。

    ![「プロジェクトパッケージ」ダイアログ・ウィンドウをインポート](attachments/file-menu/import-project-package.png)

[プロジェクトパッケージのエクスポート](export-project-package-dialog) を使用してプロジェクトパッケージを作成することができます。

## 2 アプリはどこに保存するべきですか?

この設定を使用して、アプリを保存する場所を選択します。 This can be the [Team Server](#team-server), a [private server](#private-server) (an SVN server other than the Team Server), or a [local disk](#local).

### 2.1 Mendix チームサーバー {#team-server}

Team Serverにアプリをアップロードするときは、新しいリポジトリを作成するか、既存のリポジトリにアップロードするかを選択できます。

#### 2.1.1 新しいMendix チームサーバー

Mendix Team Serverにアプリを保存することを選択すると、新しいTeam Serverプロジェクトが作成されます。 新しいTeam Serverプロジェクトとリポジトリの名前を **アプリ名** フィールドに入力する必要があります。

#### 2.1.2 既存のMendixチームサーバー

既存のリポジトリを使用する場合は、 **Team Server App** オプションでアプリを選択します。 これは既存のリポジトリが空の場合にのみ動作することに注意してください。

Mendix Team Serverの詳細については、 [Team Server](/developerportal/collaborate/team-server) を参照してください。

### 2.2 プライベートサーバー {#private-server}

{{% alert type="info" %}}

The **Private server** option is only available when support for other SVN servers is enabled: **Edit** >**Preferences** > **Advanced** > **Enable private version control**.

{{% /alert %}}

**App repository address** フィールドに、アプリをアップロードしたいリポジトリのアドレスを入力します。

### 2.3 ローカルディスク {#local}

新しいアプリをバージョン管理サーバーにアップロードする必要がない場合は、このオプションを選択します。 この場合、Studio Pro を実行しているコンピュータのローカルディスクにのみ保存されます。

## 3プロジェクトディレクトリ

このフィールドを使用して、アプリのプロジェクト ファイルを保存するディレクトリを選択します。 バージョンコントロールが有効な場合。 提案された名前は *-main* で終わり、これがアプリの主要な開発ラインになります。

## 4 続きを読む

* [チームサーバー](/developerportal/collaborate/team-server)
* [プロジェクトパッケージのエクスポート](export-project-package-dialog)