---
title: "共同開発"
category: "バージョン管理"
description: "Mendix Studio Pro と Mendix Studio の共同開発のプロセスについて説明します。"
tags:
  - "studio pro"
  - "スタジオ"
  - "共同開発は"
  - "同期"
---

## 1つの紹介

コラボレーション開発とは、複数のチームがアプリに取り組んでいるときに、アプリモデルの変更を共有するプロセスです。 共同開発により、チームメンバーはMendix Studio ProとMendix Studioの1つのプロジェクトで協力することができます。 [バージョンコントロール](version-control) を使用して簡単に変更を同期します。 Studio Pro を使用すると、アプリのさまざまなブランチで作業できます。一方、Studio はこれらのブランチの 1 つで有効にできます。

{{% alert type="info" %}}

Studio でアプリを開くと、 **開発ラインが選択されていない** というメッセージが表示された場合。 開発ラインを有効にしてください 詳細については、 [開発ライン用の Studio の有効化](#active-branch) を参照してください。

{{% /alert %}}

{{% alert type="warning" %}}

共同開発は、開発者ポータル経由で作成された新規アプリではデフォルトで有効になります。 Mendix 7から8にプロジェクトをアップグレードする場合 [Desktop Modelerバージョン7からStudio Pro 8への移動](moving-from-7-to-8).

{{% /alert %}}

## 2 共同開発の概要

Studio Pro のユーザーは、 [バージョンコントロール](version-control) を介して **コミット** と **アップデート** 操作を介してお互いにコラボレーションすることができます。

Studio Pro と Studio の共同開発プロセスは、以下の手順で構成されています。

1. Studio で行った変更はすべて、自動的に Studio 作業コピーに保存されます。 複数のユーザーが同時にプロジェクトを表示できます: あるユーザーがプロジェクトを編集でき、他のユーザーが読み取り専用モードになります。

2.  Studio Pro ユーザーがプロジェクトを開くと、この開発ラインで Studio が有効になっている場合に通知されます。

    ![共同開発が有効な通知](attachments/collaborative-development/collaborative-development-enabled-notification.png)

3. Studio Pro は、Studio Pro ユーザーが動作するローカル作業コピーを作成します。

4. Team Serverから変更を取得するには、 **Update** をクリックする必要があります。 When the Studio Pro user clicks **Update**, the latest changes from *Studio* are committed automatically to the Team Server before Studio Pro receives the update from it. 最新の *Studio* の変更を含むチームサーバーの最新版は、Studio Pro のローカル作業コピーにマージされます。

5. Studio Pro のユーザーはプロジェクトで動作し、ユーザーがいくつかの機能を終了するとします(例: バグを修正するか、新しい機能を作成します)、 **コミット** をクリックします。 ユーザはコミットメッセージを入力して確認します。 これは、アップデート中と同じプロセスをトリガーします（ステップ4で説明） そして、Studio Pro の作業コピーが、Team Server の最新のリビジョンとともに更新されます。

   このマージには2つの可能性のある結果があります:<br/>

   a   競合はありません。Studio Pro のユーザー変更は Team Server に反映されます。 その後、Studio は Team Server から最新のリビジョンを取得し、ロック解除されます。Studio Pro ユーザーの変更は、Studio ユーザーに表示されます。 他のStudio Proユーザーは、アップデートを行うと変更を受け取ります。 <br/>

   B 競合があり、Studio Pro のコミットプロセスが停止されます。 Studio は、Studio Pro ユーザーから変更を受けることなくロック解除されます。 Studio Pro のユーザーは、コミットを再実行する前に、最初にマージの競合を解決する必要があります。

{{% alert type="info" %}}

Studio Pro のユーザーがアプリケーションをクラウドにデプロイしたい場合は、 **Run** ボタンをクリックします。 コミットはこのプロセス中に自動的に行われ、ステップ5が実行されます。

{{% /alert %}}

## 3 Studio Perspective

Studio の観点からの共同開発については、 [Studio での共同開発](/studio8/collaborative-development) を参照してください。

## 4 Studio Pro Perspective

共同開発が有効になっているプロジェクトに接続すると、 Studio が有効になっている開発ライン (メインラインまたはブランチライン) が表示されます。

ドロップダウンをクリックして別の行を選択するか、 **OK** をクリックして現在選択されている行を開きます。

![アプリダイアログウィンドウを開く](attachments/collaborative-development/open-app-dialog.png)

### 4.1 最新の変更をマージする

チーム サーバーに保存されている最新の変更をマージするには (Studio ユーザーと他の Studio Pro ユーザーの両方から) **Changes** を開き、 **Update** をクリックします。

![オプションを更新](attachments/collaborative-development/update-button.png)

### 4.2 最新の変更をコミットする

最新のプロジェクトの変更をコミットし、他のユーザーが利用できるようにするには、 **Changes** を開き、 **Commit** をクリックします。 アプリケーションをデプロイするプロセス( **Run** ボタンをクリックすると)もコミットがトリガーされます。

{{% alert type="info" %}}

プロジェクト内の複数の競合を回避するために、プロジェクトを更新したり変更をコミットすることをお勧めします。

{{% /alert %}}

プロジェクトが競合している場合は、変更を受け取らずにStudioがロック解除されます。 Studio Pro で競合を解決する必要がありますが、マージを完了して再度コミットすることができます。

競合がない場合、変更は Studio に自動的に送信されます。 Studio での共同開発プロセスの詳細については、 [Studio での共同開発](/studio8/collaborative-development) を参照してください。

### 4.3 コミット履歴の表示

**バージョンコントロール** > **履歴** を使用して、現在の開発ラインに反映されているすべての変更を確認できます。

![履歴ダイアログ ボックス](attachments/history-dialog/history-dialog.png)

## 5 Studio Pro で開発ラインを管理する {#managing-branches}

Studio Pro では、開発ライン (メインラインまたはブランチライン) の Studio を有効または無効にできます。 ブランチ行の作成と削除もできます。

共同開発を行うには、開発ラインの 1 つで Studio を有効にする必要があります。

### 5.1 開発ラインで Studio を有効にする {#active-branch}

Studio と Studio Pro 間でモデルの変更を共有するには、1 つの開発ラインで Studio を有効にする必要があります。

Studio がデフォルトで開発ラインで有効になっているかどうかは、プロジェクトによって異なります。

* 以下の場合、Studio はメインラインでデフォルトで有効になっています。
  * 開発者ポータル経由で作成された新規プロジェクトの場合
  * Studio が有効になっている既存のプロジェクトの場合
* 以下の場合、どの開発ラインでもStudioが有効になっていません。
  * Studio Pro 経由で作成された新しいプロジェクトの場合。
  * スタジオが有効になっていない既存のプロジェクトの場合

Studio で開発ラインを有効にしたり、別の開発ラインに切り替えたりするには、次の手順を実行します。

1.  **Version Control** > **Manage Branch Lines** をクリックしてください。 **分岐ライン マネージャー** ダイアログボックスで。 Studio が有効になっている開発ラインには、最初の列に地球儀アイコンが表示されていることがわかります。<br/>

    ![ブランチラインマネージャーのグローブアイコン](attachments/collaborative-development/globe-icon.png)<br/>

2.  Studio を有効にする行を選択し、 **Enable for Studio** をクリックします。 <br/>

    ![ブランチラインマネージャー - 別のブランチを有効にする](attachments/collaborative-development/enable-another-branch.png)

Studio の開発ラインが選択されました。

Studio を別の開発ラインに切り替えると、このプロセスの間、Studio はしばらくロックされます。 Studio Pro ユーザーが Studio の行を変更しているポップアップダイアログがユーザーに表示されます。 Studio からのすべての変更は、現在の開発ラインに反映され、その後にのみ行が変更されます。

### 5.2 開発ラインのスタジオを無効にする

Studio が開発ラインで有効になっている場合、無効にできます。

 {{% alert type="info" %}}

開発ラインでStudioを無効にすると、それが有効になり、他の開発ラインでは有効になりません。 共同開発は利用できなくなります。

{{% /alert %}}

Studio を無効にするには、次の手順を実行します。

1. Studio で有効になっているブランチを選択します。

2. Mendix Studioの **無効化** ボタンをクリックします。

   ![Mendix Studioで無効化](attachments/collaborative-development/disable-for-studio.png)

プロジェクトではスタジオが無効になっています。

### 5.2 新しい支線の作成

新しい分岐線を作成するには、次の操作を行います:

1. **Version Control** > **Manage Branch Lines** をクリックしてください。

2.  **分岐ライン マネージャー** ダイアログボックスに、既存の開発ラインのリストが表示されます。 **New** をクリックして分岐線を作成します。 <br/>

    ![新しいブランチの作成](attachments/collaborative-development/creating-new-branch.png)<br/>

3.  **ブランチラインの作成** ダイアログボックスで、以下を設定します: <br/>

    a メインライン、ブランチライン、タグ付けされたバージョンなど、新しいラインを作成する行は何ですか。 これらの概念の詳細については、 [バージョン管理](version-control#concepts) の *コンセプト*セクションを参照してください。 <br/> b. 必要に応じてリビジョンを選択します。 <br/>

    C 新しい行の名前を入力します。

4.  すべての設定が完了したら、 **OK** をクリックします。

    ![分岐線の作成](attachments/collaborative-development/create-branch-dialog.png)

新しいブランチラインを作成しました。

### 5.3 支線の削除

分岐線を削除するには、次の操作を行います。

1. **Version Control** > **Manage Branch Lines** をクリックしてください。

2.  **Branch Line Manager** ダイアログボックスで、削除したいブランチを選択し、 **Delete** をクリックして削除を確定します。

    ![ブランチを削除中](attachments/collaborative-development/deleting-branch.png)

ブランチを削除しました。

{{% alert type="info" %}}

Studio が有効になっているブランチは削除できません。 このブランチを削除する必要がある場合は、Studio で別の行を有効にし、そのブランチのみを削除します。

{{% /alert %}}

## 6もっと読む

* [バージョン管理](version-control)
* [共同開発のトラブルシューティング](collaborative-development-troubleshooting)
* [Studio での共同開発](/studio8/collaborative-development)

