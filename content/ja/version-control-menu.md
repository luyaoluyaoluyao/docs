---
title: "バージョン管理メニュー"
parent: "menus"
description: "Studio Pro のプロジェクトメニューについて説明します。"
menu_order: 40
tags:
  - "Studio Pro"
  - "プロジェクトメニュー"
  - "トップ バー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/version-control-menu.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**バージョンコントロール** メニューでは、バージョンコントロールに接続されている設定を表示または操作できます。 たとえば、現在の開発ラインの履歴を表示できます。

{{% image_container width="300" %}}![バージョン管理メニュー](attachments/version-control-menu/version-control-menu.png)
{{% /image_container %}}

## 2件の更新

**Update** オプションは、ローカルアプリをバージョン管理サーバーにコミットされた最新のリビジョンに更新します。

## 3 コミット

**コミット** オプションは、以前のバージョン管理サーバーへのコミット以降、アプリに行われたすべてのローカル変更をコミットします。 詳細については、 [コミット](commit-dialog) を参照してください。

## 4ディスクに変更を表示する

**ディスクに変更を表示** 前回のコミット以降にディスク上のファイルが変更されたことを示すダイアログを開きます。

## 5つの履歴

**History** オプションには、アプリのコミットされたリビジョンの履歴が表示されます。 **履歴**に表示される情報については、 [履歴](history-dialog) を参照してください。

## 6 バージョン管理サーバーからダウンロード

**バージョン管理サーバーからダウンロード** オプションは、Team Serverまたは別のSVNサーバーからアプリをダウンロードします。 これにより、開発用のアプリのローカル作業コピーが作成されます。 For more information on what settings are displayed in the **Download from Version Control Server** dialog box, see [Download from Version Control Server](download-from-version-control-dialog).

## 7 バージョン管理サーバーにアップロード

**バージョン管理サーバーにアップロード** オプションは、ローカルアプリを新規または既存のTeam Serverリポジトリにアップロードします。 または別の SVN サーバーに移動します。 これは、アプリがまだバージョン管理されていない場合にのみ可能です。 For more information on what settings are displayed in the **Upload to Version Control Server** dialog box, see [Upload to Version Control Server](upload-to-version-control-dialog).

## 8 支線の管理

**Manage Branch Lines** オプションを使用すると、バージョン管理サーバーのブランチラインを管理でき、メインラインとは別に機能を開発することができます。 ブランチラインマネージャの詳細と新しいブランチラインの作成 see [Branch Line Manager](branch-line-manager-dialog) and [Create Branch Line](create-branch-line-dialog).

## 9 変更をここにマージする

**Merge Changes Here** オプションを使用すると、別の開発ラインでコミットされた変更を Studio Pro で現在開いている開発ラインにマージできます。

## 10 変更を逆マージする

**Reverse Merge Changes** オプションを使用すると、バージョン管理リポジトリにコミットされた変更をローカルでロールバックできます。 これらのローカル変更は、新しいリビジョンとして反映されます。

## 11 すべての変更を元に戻す {#revert-all}

**すべての変更を元に戻す** オプションでは、すべてのローカルの変更を元に戻すことができます。 プロジェクトとディスク上のファイルの両方で前回のコミット以来導入された

## 12 データのスナップショットを追加

**Add Snapshot of Data** オプションは、組み込みデータベースのスナップショットを作成し、バージョン管理リポジトリに追加します。 これは、テストデータをアプリに追加したり、デモ目的で使用する場合に特に便利です。

## 13 続きを読む

* [Studio Pro Overview](studio-pro-overview)
* [バージョン管理](version-control)
