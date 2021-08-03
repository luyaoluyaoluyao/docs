---
title: "バージョン管理サーバーダイアログからダウンロード"
parent: "ダイアログ"
aliases:
  - /refguide7/download-from-team-server-dialog.html
---

## 1つの紹介

**バージョン管理サーバーからダウンロード** ダイアログボックスを使用して、SVN バージョン管理サーバーからアプリをダウンロードします。

![](attachments/download-from-version-control-server-dialog/download-from-version-control-server-dialog-original.png)

{{% alert type="info" %}}

[アプリを開く](open-app-dialog) ダイアログボックスを使用して、Team Serverからアプリをダウンロードして開くことができます。 ただし、 すでにディスクにあるアプリ(および開発ライン)の2番目のコピーをダウンロードする場合は、このオプションを使用する必要があります。

{{% /alert %}}

To open the **Download from Version Control Server** dialog box, go to **Project > More Versioning > Download from Version Control Server**.

## 2 アプリはどこに保存されていますか?

この設定を使用して、アプリが保存されている場所を選択します。 Team ServerまたはTeam Server以外のSVNサーバーから選択できます。

### 2.1 Mendix チームサーバー

In the **Team Server App** drop-down list, select the Team Server app you wish to open, and then choose the development line you want to download in the **Development line** drop-down list.

![](attachments/download-from-version-control-server-dialog/download-from-version-control-server.png)

Mendix Team Serverの詳細については、 [Team Server](team-server) を参照してください。

開発ラインの詳細については、 [バージョン管理コンセプト](version-control) を参照してください。

### 2.2 プライベートサーバー

In the **App repository address** field, enter the repository address of the app you want to open and click **Connect** to load the development lines from the repository. 次に、 **開発ライン** ドロップダウンリストからダウンロードする開発ラインを選択します。

![](attachments/download-from-version-control-server-dialog/download-from-private-server.png)

{{% alert type="info" %}}

このオプションは、 [環境設定](preferences-dialog#enabled) ダイアログボックスで他のサーバーのサポートが有効になっている場合にのみ使用できます。

{{% /alert %}}

## 3 ディスクの場所

**プロジェクト ディレクトリ** フィールドで、ダウンロードしたアプリを格納するディレクトリを選択します。 提案された名前は開発行の名前(**main** またはブランチの名前)を含みます。
