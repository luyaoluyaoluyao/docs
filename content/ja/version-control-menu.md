---
title: "バージョン管理メニュー"
parent: "menus"
description: "Studio Pro のバージョン管理メニューについて説明します。"
menu_order: 40
tags:
  - "Studio Pro"
  - "バージョン管理"
  - "トップ バー"
---

## 1つの紹介

**バージョン コントロール** メニューでは、バージョン管理に接続されている設定を表示または操作できます。 たとえば、現在の開発ラインの履歴を表示できます。

![バージョン管理メニュー](attachments/version-control-menu/version-control-menu.png)

## 2件の更新

**Update** オプションは、ローカルアプリをバージョン管理サーバーにコミットされた最新のリビジョンに更新します。

## 3 コミット

**コミット** オプションは、以前のバージョン管理サーバーへのコミット以降、アプリに行われたすべてのローカル変更をコミットします。 詳細については、 [コミット](commit-dialog) を参照してください。

## 4ディスクに変更を表示する

**ディスクに変更を表示** 前回のコミット以降にディスク上のファイルが変更されたことを示すダイアログを開きます。

## 5つの履歴

**History** オプションには、アプリのコミットされたリビジョンの履歴が表示されます。 **履歴**に表示される情報については、 [履歴](history-dialog) を参照してください。

## 6 バージョン管理サーバーからダウンロード

**バージョン管理サーバーからダウンロード** オプションは、Team Serverまたは他のプライベートサーバーからアプリをダウンロードします。 これにより、開発用のアプリのローカル作業コピーが作成されます。 For more information on what settings are displayed in the **Download from Version Control Server** dialog box, see [Download from Version Control Server](download-from-version-control-dialog).

## 7 バージョン管理サーバーにアップロード

**バージョン管理サーバーにアップロード** オプションは、ローカルアプリを新規または既存のTeam Serverリポジトリにアップロードします。 または別のプライベートサーバーに これは、アプリがまだバージョン管理されていない場合にのみ可能です。 For more information on what settings are displayed in the **Upload to Version Control Server** dialog box, see [Upload to Version Control Server](upload-to-version-control-dialog).

## 8 支線の管理

**Manage Branch Lines** オプションを使用すると、バージョン管理サーバーのブランチラインを管理でき、メインラインとは別に機能を開発することができます。 ブランチラインマネージャの詳細と新しいブランチラインの作成 see [Branch Line Manager](branch-line-manager-dialog) and [Create Branch Line](create-branch-line-dialog).

## 9 変更をここにマージする

**Merge Changes Here** オプションを使用すると、別の開発ラインでコミットされた変更を Studio Pro で現在開いている開発ラインにマージできます。

## 10 変更を逆マージする

**Reverse Merge Changes** オプションを使用すると、バージョン管理リポジトリにコミットされた変更をローカルでロールバックできます。 これらのローカル変更は、新しいリビジョンとして反映されます。

## 11 すべての変更を元に戻す

**すべての変更を元に戻す** オプションでは、すべてのローカルの変更を元に戻すことができます。 前回のコミット以降に導入されたアプリとディスク上のファイルの両方。

## 12 データのスナップショットを追加

**Add Snapshot of Data** オプションは、組み込みデータベースのスナップショットを作成し、バージョン管理リポジトリに追加します。 これは、テストデータをアプリに追加したり、デモ目的で使用する場合に特に便利です。

## 13 続きを読む

* [Studio Pro Overview](studio-pro-overview)
* [バージョン管理](version-control)
