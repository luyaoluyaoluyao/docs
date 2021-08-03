---
title: "支線管理"
parent: "version-control-menu"
menu_order: 80
tags:
  - "studio pro"
  - "分岐線の管理"
  - "支線マネージャー"
---

## 1つの紹介

**Branch Line Manager** は、バージョン管理サーバーに保存されているアプリの [ブランチライン](version-control#branches) を管理するために使用されます。 ダイアログボックスは、いくつかのマイナーな違いを除いて、SVN と Git の両方のバージョンコントロールで同じように見えます。

*  SVN用のダイアログボックス:

    ![SVN支店ラインマネージャー](attachments/version-control-menu/branch-line-manager.png)

*  Git用のダイアログ ボックス:

    ![Git Branch Line Manager](attachments/version-control-menu/git-branch-line-manager.png)

**ブランチラインマネージャー** ダイアログボックスを表示するには、 **バージョンコントロール** > **ブランチラインの管理** を開きます。

支線は、他の開発ラインから独立した開発を可能にします。 分岐線を作成するには主に2つの理由があります:

* 本番環境で動作しているアプリのバージョンでメンテナンス開発を行う。 ブランチラインで問題を解決しながら、メインラインで開発を続けることができます。
* 開発に一日以上かかる非常に大きな機能の開発を開始するには. これをブランチラインで行うことで、メインラインで他の開発を妨げることなく(おそらくエラーであっても)半実装された機能をコミットすることができます。

## 2つの場所

この設定を使用して、アプリが保存されている場所を選択します。 これは、 [Team Server](#team-server-app) または [private SVN または Git リポジトリ](#byo-server-app) のいずれかになります。

{{% alert type="warning" %}}
このオプションは、プライベート SVN または Git サーバーのサポートが [環境設定](preferences-dialog) で有効になっている場合にのみ使用できます。
{{% /alert %}}

### 2.1 チームサーバーアプリ {#team-server-app}

ブランチラインを管理するチームサーバーアプリを選択します。 Studio Proでアプリを開いている場合は、自動的に選択されます。 ただし、最初にアプリを開かずにブランチラインを管理することもできます。この場合、アプリは選択されません。

Mendix Team Serverの詳細については、 [Team Server](/developerportal/collaborate/team-server) を参照してください。

### 2.2 独自の(BYO)SVNまたはGitサーバーアプリを持参する {#byo-server-app}

In the **App repository address** field, enter the address of the app you want to manage and click **Connect** to load the available branches from the repository.

## 3 支線の管理

**Branch Line Manager**では、ブランチラインの作成と削除、アプリの Mendix Studio の有効化と無効化ができます。 これらのアクションの実行方法の詳細について [開発ラインの](collaborative-development#managing-studio) と [開発ラインの管理](collaborative-development#managing-branches) セクションの *Collaborative Development* を参照してください。

## 4 続きを読む

* [バージョン管理](version-control)
* [共同開発](collaborative-development)
