---
title: "バージョン管理サーバーにアップロード"
parent: "version-control-menu"
menu_order: 70
tags:
  - "studio pro"
aliases:
  - /refguide8/upload-to-team-server-dialog.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/upload-to-version-control-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このダイアログボックスを使用して、バージョン管理サーバーにまだ保存されていないアプリをアップロードします。

![バージョン管理サーバーメニューオプションにアップロード](attachments/upload-to-version-control/upload-to-version-control-server.png)

## 2つの場所

この設定を使用して、アプリを保存する場所を選択します。 以下に3つの選択肢があります。

### 2.1 新しいMendixチームサーバー

[Mendix Team Server](/developerportal/collaborate/team-server) で新しいアプリを作成できます。

* **新しいMendix Team Serverを選択**
* 新しいTeam Serverプロジェクトとリポジトリの名前を **アプリ名** フィールドに入力します。

    ![New Mendix Team Serverのアプリ名を入力してください](attachments/upload-to-version-control/new-team-server-app.png)

### 2.2 既存のMendixチームサーバー

{{% alert type="warning" %}}
リポジトリが空の場合にのみ、既存のリポジトリにアップロードできます
{{% /alert %}}

* **既存のMendixチームサーバーを選択**
* リストから **チームサーバーアプリ** を選択します

    ![既存のmendixチームサーバーを選択](attachments/upload-to-version-control/existing-team-server-app.png)

### 2.3 プライベートサーバー

This option is only available when support for other servers is enabled in **Edit** > **Preferences** > **Advanced** > [Enable private version control](preferences-dialog#enable)).

![上級者向けバージョン管理を有効にする](attachments/upload-to-version-control/enable-private-version-control.png)

<a name="private-server"></a>If you select **Private server**, enter the address of the repository to which you want to upload your app in the **App repository address** field.

![上級者向けバージョン管理を有効にする](attachments/upload-to-version-control/private-server-app.png)

## 3 続きを読む

* [オンプレミスバージョン管理サーバーの操作方法](/howto8/collaboration-requirements-management/on-premises-svn-howto)
