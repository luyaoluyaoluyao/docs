---
title: "バージョン管理サーバーにアップロード"
parent: "ダイアログ"
aliases:
  - /refguide7/upload-to-team-server-dialog.html
---

## 1つの紹介

このダイアログボックスを使用すると、バージョン管理サーバーにまだ保存されていないアプリケーションをアップロードできます。

![](attachments/upload-to-version-control-dialog/upload-to-version-control-server-dialog.png)

To open the **Upload to Version Control Server** dialog box, go to **Project > More Versioning > Upload to Version Control Server**.

![](attachments/upload-to-version-control-dialog/project-more-versioning-upload-to-version-control-server.png)

## 2 アプリはどこにアップロードしますか?

この設定を使用して、アプリを保存する場所を選択します。 これは、チームサーバー、プライベートサーバー(Team Server以外のSVNサーバー)、またはローカルディスクです。

### 2.1 新しいMendixチームサーバー

**App name** フィールドに、新しい Team Server プロジェクトとリポジトリの名前を入力します。 **OK**をクリックすると、新しいリポジトリが [Mendix Team Server](team-server) に作成され、アプリを保存します。

### 2.2 既存のMendixチームサーバー

**Team Server App** リストで、対応するTeam Serverアプリを選択します。 **OK**をクリックすると、選択したリポジトリにアプリがアップロードされます。

{{% alert type="info" %}}

これは、既存のリポジトリが空の場合にのみ機能します。

{{% /alert %}}

### 2.3 プライベートサーバー

**App repository address** フィールドに、アプリをアップロードしたいリポジトリアドレスを入力します。 **OK**をクリックすると、このリポジトリにアプリがアップロードされます。

{{% alert type="info" %}}

このオプションは、 [環境設定](preferences-dialog#enabled) ダイアログボックスで他のサーバーのサポートが有効になっている場合にのみ使用できます。

{{% /alert %}}

## 3 続きを読む

* [チームサーバー](team-server)
