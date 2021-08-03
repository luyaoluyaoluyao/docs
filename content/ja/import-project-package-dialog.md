---
title: "プロジェクトパッケージのインポート"
parent: "ダイアログ"
---

## 1つの紹介

Mendixプロジェクトパッケージ(*.mpk*)から新しいアプリを作成するには、アプリパッケージをインポートする必要があります。 新しいアプリは、バージョン管理サーバーまたはローカルディスクに保存することができます。

To open this dialog box,  go to **File > Import App Package**, browse to the *.mpk* file, and then open it.

![](attachments/import-project-package-dialog/import-project-package.png)

## 2 アプリはどこに保存するべきですか?

この設定を使用して、アプリを保存する場所を選択します。 This can be the [Mendix Team Server](#team-server), a [private server](#private-server) (an SVN server other than the Team Server), or a [local disk](#local).

### 2.1 Mendix チームサーバー {#team-server}

Mendix Team Serverにアプリをアップロードするときは、新しいリポジトリを作成するか、既存のリポジトリにアップロードするかを選択できます。

#### 2.1.1 新しいMendix チームサーバー

このオプションを選択すると、新しいTeam Serverリポジトリが作成され、アプリを保存します。 新しいTeam Serverアプリとリポジトリの名前を **アプリ名** フィールドに入力する必要があります。

#### 2.1.2 既存のMendixチームサーバー

このオプションを選択すると、既存のTeam Serverリポジトリにアプリがアップロードされます。 **Team Server App** ドロップダウンリストでリポジトリを選択する必要があります。

{{% alert type="info" %}}

これは、既存のリポジトリが空の場合にのみ機能します。

{{% /alert %}}

### 2.2 プライベートサーバー {#private-server}

このオプションを選択すると、アプリはプライベートサーバーに保存されます。 アプリをアップロードする **アプリリポジトリアドレス** を入力する必要があります。

{{% alert type="info" %}}

このオプションは、 [環境設定](preferences-dialog#enabled) ダイアログボックスで他のサーバーのサポートが有効になっている場合にのみ使用できます。

{{% /alert %}}

### 2.3 ローカルディスク {#local}

このオプションを選択すると、Desktop Modelerを実行しているコンピュータのローカルディスクにアプリが保存されます。

{{% alert type="info" %}}

新しいアプリをバージョン管理サーバーにアップロードする必要がない場合は、このオプションを選択します。

{{% /alert %}}

## 3 ディスクの場所

**プロジェクト ディレクトリ** フィールドで、アプリケーションのプロジェクト ファイルを格納するディレクトリを指定します。 バージョン管理が有効な場合。 提案された名前には、アプリのメイン開発ラインになることを示す **-main** の末尾が含まれています。

## 4 続きを読む

* [プロジェクトパッケージのエクスポート](export-project-package-dialog)

