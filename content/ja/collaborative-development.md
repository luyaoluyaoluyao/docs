---
title: "共同開発"
category: "バージョン管理"
description: "Mendix Desktop ModelerとMendix Web Modelerとの共同開発のプロセスを説明します"
tags:
  - "デスクトップモデラー"
  - "共同開発は"
  - "同期"
aliases:
  - /howto/web-modeler/syncing-webmodeler-desktop.html
  - /refguide7/desktop-webmodeler.html
  - /refguide7/sync-webmodeler-desktopmodeler.html
  - /web-modeler/general-sync-webmodeler-desktopmodeler-wm.html
---

## 1つの紹介

{{% alert type="warning" %}}

共同開発は、Mendix バージョン 7.23.3 以降のプロジェクトの場合にのみ利用できます。 Mendix バージョン 7.23.2 以下のプロジェクトでは、Web Modelerとの同期はできません。

Webモデラーでプロジェクトを開くことができます(Webモデラーは自動的に7の最新バージョンにアップグレードします)。 3)  ただし、Web Modelerからの変更を同期するには、Mendix Desktop Modelerバージョン7.23.3以上を使用する必要があります。

{{% /alert %}}

コラボレーション開発とは、複数のチームがアプリに取り組んでいるときに、アプリモデルの変更を共有するプロセスです。 共同開発により、チームメンバーはデスクトップモデラーとWebモデラーの1つのプロジェクトで協力し、 [バージョンコントロール](version-control)を使用して変更を簡単に同期することができます。 Desktop Modelerは、アプリの異なるブランチで動作するために使用できます。 一方、Webモデラーはこれらのブランチのいずれかで有効にできます。

Mendix Web Modelerを使用したことがない場合は、最初に開発ラインに対して有効にする必要があることに注意してください。 開発ラインの管理に関する詳細は、Desktop Modelerの [](#managing-branches) セクションのformat@@2開発ラインの管理を参照してください。

## 2 共同開発の概要

デスクトップ モデラーのユーザーは、 [コミット](version-control) と **アップデート** 操作を介して **バージョンコントロール** を介してお互いに協力することができます。

Desktop ModelerとWeb Modelerとの共同開発プロセスは、以下の手順で構成されています。

1. Web Modelerで行われたすべての変更は、自動的に Web Modelerの作業コピーに保存されます。 複数のユーザが同時にWebモデラーでプロジェクトを表示できます: あるユーザがプロジェクトを編集でき、他のユーザが読み取り専用モードになります。

2.  Desktop Modelerユーザーがプロジェクトを開くと、この開発ラインでWebモデラーが有効になっている場合に通知されます。

    ![共同開発が有効な通知](attachments/collaborative-development/collaborative-development-enabled-notification.png)

3. Desktop Modelerは、Desktop Modelerユーザーが動作するローカル作業コピーを作成します。 Team Serverから変更を取得するには、 **Update** をクリックする必要があります(最新のリビジョンは、Team Serverから取得されます。 には、他のDesktop ModelerユーザからのコミットおよびWebモデラーからの最新の変更を含みます。

4. Desktop Modelerユーザーが **Update**をクリックした後。 Web Modelerからの最新の変更は、Desktop Modelerがそこから更新を受け取る前に、Team Serverに自動的に反映されます。 Team Serverからの最新のリビジョンは、Desktop Modelerのローカル作業コピーにマージされます。

5.  Desktop Modelerユーザーはプロジェクトで動作し、ユーザーがいくつかの機能を終了すると(例: バグを修正するか、新しい機能を作成します)、 **コミット** をクリックします。 ユーザはコミットメッセージを入力して確認します。 これは、アップデート中と同じプロセスをトリガーします（ステップ4で説明） そして、Desktop Modelerの作業コピーがチームサーバーからの最新のリビジョンで更新されます。

    このマージには2つの可能性のある結果があります:<br/>

    a   競合はありません。Desktop Modelerユーザーの変更はチームサーバーに反映されます。 その後、Webモデラーはチームサーバーから最新のリビジョンを取得し、ロック解除されます。 Desktop Modelerユーザーの変更は、WebModelerユーザーに表示されます。 他のDesktop Modelerユーザーは、アップデートを行うと変更を受け取ります。 <br/>

    B 競合があり、Desktop Modelerコミットプロセスが停止されます。 Web Modelerは、Desktop Modelerユーザーから変更を受けることなくアンロックされます。 Desktop Modelerユーザーは、コミットを再実行する前に、最初にマージの競合を解決する必要があります。

{{% alert type="info" %}}

Desktop Modelerユーザーがアプリケーションをクラウドにデプロイしたい場合は、 **Run** ボタンをクリックします。 コミットはこのプロセス中に自動的に行われ、ステップ5が実行されます。

{{% /alert %}}

## 3 ウェブモデラーの展望

Web Modelerの観点からの共同開発に関する情報 [Web Modelerガイド](/studio7/general-collaborative-development) の *Web Modelerガイド* を参照してください。

## 4 デスクトップモデラーの展望

共同開発が有効になっているプロジェクトに接続すると、 Web Modelerが有効になっている開発ライン (メインラインまたはブランチライン) が表示されます。

ドロップダウンをクリックして別の行を選択するか、 **OK** をクリックして現在選択されている行を開きます。

![アプリダイアログウィンドウを開く](attachments/collaborative-development/open-app-dialog.png)

### 4.1 最新の変更をマージする

チームサーバーに保存されている最新の変更をマージするには (Web Modelerユーザーと他のデスクトップモデラーユーザーの両方から) **Changes** を開き、 **Update** をクリックします。

![オプションを更新](attachments/collaborative-development/update-button.png)

### 4.2 最新の変更をマージ

最新のプロジェクトの変更をコミットし、他のユーザーが利用できるようにするには、 **Changes** を開き、 **Commit** をクリックします。 アプリケーションをデプロイするプロセス( **Run** ボタンをクリックすると)もコミットがトリガーされます。

{{% alert type="info" %}}

プロジェクト内の複数の競合を回避するために、プロジェクトを更新したり変更をコミットすることをお勧めします。

{{% /alert %}}

プロジェクトが競合している場合、Webモデラーは変更を受け取ることなくロック解除されます。 最初に Desktop Modelerで競合を解決し、マージを完了して再度コミットする必要があります。

競合がない場合、変更は自動的にWebモデラーに送信されます。 Web Modelerの共同開発プロセスの詳細については、 [Web Modelerガイド](/studio7/general-collaborative-development) の *Web Modelerガイド* を参照してください。

### 4.3 コミット履歴の表示

**プロジェクト** > **More Versioning** > **履歴**

![履歴ダイアログ ボックス](attachments/collaborative-development/history.png)



## 5 Desktop Modelerで開発ラインを管理する {#managing-branches}

Desktop Modelerでは、開発ライン(メインラインまたはブランチライン)に対してWebモデラーを有効にできます。 ブランチ行の作成と削除もできます。

共同開発のためには、開発ラインのいずれかで Web Modelerを有効にする必要があります。

### 5.1 開発ラインの Web モデラーの有効化 {#active-branch-for-the-wm}

Web ModelerとDesktop Modelerの間でモデルの変更を共有するには、開発ラインのいずれかでWebモデラーを有効にする必要があります。

Web Modelerがデフォルトで開発ラインで有効になっているかどうかは、プロジェクトによって異なります。

* 次の場合、Webモデラーはメインラインでデフォルトで有効になっています。
  * 開発者ポータル経由で作成された新規プロジェクトの場合
  * Web Modelerが有効になっている既存のプロジェクトの場合
* 以下の場合、Web Modelerは開発ラインで有効になっていません。
  * Desktop Modeler経由で作成された新しいプロジェクトの場合
  * Web Modelerが有効になっていない既存のプロジェクトの場合

開発ラインでWebモデラーを有効にするか、別の開発ラインに切り替えるには、次の手順を行います。

1.  Click **Project** > **More Versioning** > **Manage Branch Lines**. **分岐ライン マネージャー** ダイアログウィンドウで。 Web Modelerが有効になっている(もしあれば)開発ラインには、最初の列に地球儀アイコンが表示されていることがわかります。<br/>

    ![ブランチラインマネージャーのグローブアイコン](attachments/collaborative-development/globe-icon.png)<br/>

2.  Web Modelerを有効にする行を選択し、 **Enable for the Web Modeler** をクリックします。 <br/>

    ![ブランチラインマネージャー - 別のブランチを有効にする](attachments/collaborative-development/enable-another-branch.png)

Web Modelerの開発ラインが選択されました。

Web Modelerを別の開発ラインに切り替えると、Web Modelerはこのプロセス中に数分間ロックされます。 Desktop ModelerユーザーがWebモデラーの行を変更していることを示すポップアップダイアログがユーザに表示されます。 Web Modelerからのすべての変更は、現在の開発ラインにコミットされ、その後のみ行が変更されます。

### 5.2 新しい支線の作成

新しい分岐線を作成するには、次の操作を行います:

1. Click **Project** > **More Versioning** > **Manage Branch Lines**.

2.  **分岐ライン マネージャー** ダイアログウィンドウに、既存の開発ラインのリストが表示されます。 **New** をクリックして分岐線を作成します。 <br/>

    ![新しいブランチの作成](attachments/collaborative-development/creating-new-branch.png)<br/>

3.  **分岐線の作成** ダイアログウィンドウで、以下を設定します: <br/>

    a メインライン、ブランチライン、タグ付けされたバージョンなど、新しいラインを作成する行は何ですか。 これらの概念の詳細については、 [バージョンコントロール](version-control#concepts) のセクション *2 コンセプト* を参照してください。 <br/>

    B 必要に応じてリビジョンを選択します。 <br/>

    C 新しい行の名前を入力します。

4.  すべての設定を設定したら、 **OK をクリックします。**

    ![分岐線の作成](attachments/collaborative-development/create-branch-dialog.png)

新しいブランチラインを作成しました。

### 5.3 支線の削除

分岐線を削除するには、次の操作を行います。

1. Click **Project** > **More Versioning** > **Manage Branch Lines**.

2.  **Branch Line Manager** ダイアログウィンドウで、削除したいブランチを選択し、 **Delete** をクリックして削除を確定します。

    ![ブランチを削除中](attachments/collaborative-development/deleting-branch.png)

ブランチを削除しました。

{{% alert type="info" %}}

Web Modelerが有効になっているブランチは削除できません。 このブランチを削除する必要がある場合は、別の行の Web モデラーを有効にしてからのみ、ブランチを削除します。

{{% /alert %}}

## 6もっと読む

* [バージョン管理](version-control)
* [共同開発のトラブルシューティング](collaborative-development-troubleshooting)
* [Webモデラーにおける共同開発](/studio7/general-collaborative-development)
