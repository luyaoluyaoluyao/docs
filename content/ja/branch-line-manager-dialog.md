---
title: "支線管理"
parent: "version-control-menu"
menu_order: 80
tags:
  - "studio pro"
  - "分岐線の管理"
  - "支線マネージャー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/branch-line-manager-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**ブランチライン マネージャー** は、バージョン管理サーバーに格納されているアプリの [ブランチライン](version-control#branches) を管理するために使用されます。

![支線管理](attachments/version-control-menu/branch-line-manager.png)

**ブランチラインマネージャー** ダイアログボックスを表示するには、 **バージョンコントロール** > **ブランチラインの管理** を開きます。

支線は、他の開発ラインから独立した開発を可能にします。 分岐線を作成するには主に2つの理由があります:
1. 本番環境で動作しているアプリのバージョンでメンテナンス開発を行う。 ブランチラインで問題を解決しながら、メインラインで開発を続けることができます。
2. 開発に1日以上かかる非常に大きな機能の開発を開始している場合。 これをブランチラインで行うことで、メインラインで他の開発を妨げることなく(おそらくエラーであっても)半実装された機能をコミットすることができます。

## 2つの場所

この設定を使用して、アプリが保存されている場所を選択します。 これは、 [チーム サーバー](#team-server-app) または [別の SVN サーバー](#other-svn-server-app) のいずれかになります。

{{% alert type="warning" %}}

このオプションは、「環境設定 (Preferences)」ダイアログで他の SVN サーバーのサポートが有効な場合にのみ使用できます。

{{% /alert %}}

### 2.1 チームサーバーアプリ {#team-server-app}

ブランチラインを管理するチームサーバーアプリを選択します。 Studio Pro でアプリを開いている場合は、自動的に選択されます。 ただし、最初にアプリを開かずにブランチラインを管理することもできます。この場合、アプリは選択されません。

Mendix Team Serverの詳細については、 [Team Server](/developerportal/collaborate/team-server) を参照してください。

### 2.2 その他のSVNサーバーアプリ {#other-svn-server-app}

In the **SVN repository address field**, enter the address of the app you want to manage and click **Connect** to load the available branches from the repository.

## 3 支線の管理

**ブランチラインマネージャー**では、プロジェクトのブランチラインを作成および削除、有効化および無効化できます。 これらのアクションの実行方法の詳細について [Collaborative Development](collaborative-development#managing-branches) の *Studio Pro で開発ラインを管理する* セクションを参照してください。

## 4 続きを読む

* [バージョン管理](version-control)
* [共同開発](collaborative-development)
