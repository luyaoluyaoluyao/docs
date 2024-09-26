---
title: "バージョン管理サーバーからダウンロード"
parent: "version-control-menu"
menu_order: 60
tags:
  - "studio pro"
aliases:
  - /refguide8/download-from-team-server-dialog.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/download-from-version-control-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

Use the **Download from Version Control Server…** menu item to download an app from an SVN version control server (for example, [Team Server](/developerportal/collaborate/team-server)). 現在アプリを編集している場合 プロジェクトは(変更の保存を促した後)閉じられ、新しくダウンロードしたアプリは現在のバージョンの Studio Pro を使用して開きます。

{{% alert type="info" %}}
ダウンロードしたアプリが Mendix の別のバージョンで作成された場合、現在のバージョンに変換できるかどうかを尋ねられます。

[Open App Dialog](open-app-dialog) を使用して、Team Serverからアプリをダウンロードして開くこともできます。 ただし、 すでにディスクにあるアプリ(および開発ライン)の2番目のコピーをダウンロードする場合は、このオプションを使用する必要があります。
{{% /alert %}}

![バージョン管理サーバーダイアログボックスからダウンロード](attachments/version-control-menu/download-from-version-control-server.png)

## 2 アプリはどこに保存されていますか?

If **Enable private version control** is set in the project [Preferences](preferences-dialog#enable), you can choose between the **Mendix Team Server** or a **Private server**. 有効化されていない場合は、Mendix Team Server からのみアプリを選択できます。

### 2.1 Mendix チームサーバー

**Team Server App** ドロップダウンを使用して、ダウンロードしたいアプリを選択します。

Mendix Team Serverの詳細については、 [Team Server](/developerportal/collaborate/team-server) を参照してください。

### 2.2 プライベートサーバー

**App repository address** にプライベートSVNサーバーのURLを入力し、 **Connect** をクリックします。

![バージョン管理サーバーダイアログボックスからダウンロード](attachments/version-control-menu/download-from-private-server.png)

## 3開発ライン

ダウンロードする **開発ライン** を選択します。

開発ラインの詳細については、 [バージョンコントロール](version-control) を参照してください。

## 4プロジェクトディレクトリ

アプリをダウンロードしたい **プロジェクトディレクトリ** を選択します。 提案された名前は開発行の名前(*main* またはブランチの名前)を含みます。 でもこれなら変えられるわ
