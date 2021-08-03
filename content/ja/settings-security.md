---
title: "セキュリティ、ロール & 権限"
category: "設定"
description: "Mendix Studioのセキュリティとロールと権限について説明します。"
menu_order: 10
tags:
  - "スタジオ"
  - "セキュリティ"
  - "ロールと権限"
---

## 1つの紹介

セキュリティはアプリへのアクセスを制御する方法です。 たとえば、誰がアプリケーションにアクセスできるかを決めることができます。

[役割と権限](#roles-and-permissions) はセキュリティの重要な部分です。アプリのさまざまな部分へのアクセスを制限または許可するために使用できる機器です。 例えばページやマイクロフローなどです

## 2 セキュリティを有効にする {#enabling-security}

セキュリティがデフォルトでアプリで有効になっているかどうかは、アプリのタイプとバージョンによって異なります。 次のケースに出くわすことができます:

1. Mendix バージョン 7.23 の開発者ポータルでアプリが作成された場合。 またはそれ以上の場合は、Studio でセキュリティを有効にして、 [ロールとパーミッション](#roles-and-permissions) を表示および編集できます。 バージョンの詳細については、 [Studio Ranges & Mendix Versionsを参照してください](general-versions)

2. アプリが開発者ポータルで作成され、Mendixバージョンが7.23以下の場合。 、またはプライベートコンテンツとしてラベル付けされている、またはあなたの会社向けにチームによってカスタマイズされています セキュリティ状態は、Studio Pro:<br/> aに依存します。  Studio Pro でセキュリティがオフの場合は、Studio でセキュリティを有効にできます。 この場合、 [アプリを公開](publishing-app)しようとすると、セキュリティを有効にするように求められます。 <br/>

    {{% image_container width="400" %}}![Secure Your App Pop-up Window](attachments/settings-security/security-pop-up.png)
 {{% /image_container %}}<br/>

    B If security is set to the **Production** level in Studio Pro and settings are compatible with Studio, you can view and edit **Roles and Permissions** in Studio. (Studio と互換性のあるセキュリティ設定の詳細については、こちらをご覧ください。 [Studio でセキュリティが有効になっている場合のモデル変更](/refguide8/studio-security-enabled#studio-compatible) の *Studio互換性* セクションを参照してください。

    ![](attachments/settings-security/roles-and-permissions-screen.png)

    C If security is set to the **Prototype/demo** or **Production** level in Studio Pro and settings are not compatible with Studio, you can view (not edit) **Roles and Permissions** in Studio. (Studio と互換性のあるセキュリティ設定の詳細については、こちらをご覧ください。 [Studio でセキュリティが有効になっている場合のモデル変更](/refguide8/studio-security-enabled#studio-compatible) の *Studio互換性* セクションを参照してください。

    ![](attachments/settings-security/security-read-only.png)


セキュリティを有効にする必要がある場合は、次のいずれかを実行します。

* 上記のポップアップダイアログで **セキュリティを有効にする** をクリックすると、セキュリティが自動的に設定されます。 その後、 [ロールと権限](#roles-and-permissions) を使用してアプリへのアクセスを制限または許可できます。

*  **アプリ設定** > **ロールとアクセス許可** を開き、 **セキュリティを有効にする** をクリックします。

    ![役割と権限画面](attachments/settings-security/enabling-security.png)

{{% alert type="info" %}}
セキュリティを有効にすると、アプリ全体で有効になります Studio Proに表示されているモデルには、チェックと変更が適用されています。 これらのチェックと変更に関する技術的な情報については、 [Studio でセキュリティが有効になっている場合のモデルの変更](/refguide8/studio-security-enabled) を参照してください。
{{% /alert %}}

## 3つのロールと権限 {#roles-and-permissions}

{{% alert type="info" %}}
Studio Pro では、高度なセキュリティ設定を適用できます。 この場合、Studio でロールや権限を編集することはできません。
{{% /alert %}}

ロールとは、ユーザーに割り当てられる権限のセットです。 たとえば、 *管理者* にすべてのページとマイクロフローへのフルアクセスを与えることができます。 他のユーザに対して、特定のページへのアクセスのみを許可し、マイクロフローのアクセスを制限することを選択できます。

開発者ポータル経由で作成されたアプリには、次の2つのアプリロールがあります。

* 管理者
* ユーザー

{{% alert type="warning" %}}
セキュリティが有効になっている場合、これらの2つのアプリのロールはアプリにフルアクセスできます。 ユーザーロールの権限を確認することをお勧めします。
{{% /alert %}}

アプリユーザーの管理についての詳細は、 [App Users の管理](#managing-app-users) セクションを参照してください。

**ロールと権限** 画面は以下の3つのタブで構成されます:

* ロール
* ページアクセス
* マイクロフローアクセス

**ロール** タブにはすべてのロールが表示され、アクセスできるページ数とマイクロフロー数が表示されます。

**ページ アクセス** および **マイクロフロー アクセス** タブには、すべての pages/microflow が行に表示されるテーブルが含まれています。 すべてのロールが列に配置されます。

ページまたはマイクロフローへのアクセスを特定のロールのみ許可できます。ページまたはマイクロフローへのロールへのアクセスを許可するには、適切なボックスを選択します。

すべてのページまたはマイクロフローを選択/選択解除するには、ユーザー ロールの横にある省略記号アイコンをクリックします。

結果として、各ロールに固有の行列を取得します。

![ページアクセスタブの例](attachments/settings-security/page-access-tab.png)

### 3.1 新しいロールの作成

新しいアプリのロールを作成するには、次の操作を行います。

1. **ロールと権限** > **ロール** タブを開きます。

2.  右側の **Add Role** をクリックします。

    ![](attachments/settings-security/add-role-button.png)

3.  **Create Role** ダイアログボックスで新しいロールの名前を指定し、 **Create** をクリックします。

    ![ロールダイアログボックスを作成](attachments/settings-security/create-role-dialog.png)

新しいロールが作成されます。

### 3.2 既存の役割の編集

既存のロールを編集するには、次の操作を行います。

1.  **ロールと権限** > **ロール** タブを開きます。

2.  **その他のオプション** アイコンをクリックし、 **編集** を選択します。

    ![](attachments/settings-security/edit-role-option.png)

3.  **ロール** の編集ポップアップダイアログで変更を実行し、 **保存** をクリックします。

    ![](attachments/settings-security/edit-role-dialog.png)

ロールが編集されました。

### 3.3 ロールの削除

既存のロールを削除するには、次の操作を行います。

1.  **ロールと権限** > **ロール** タブを開きます。

2.  **その他のオプション** アイコンをクリックし、 **削除** を選択します。

    ![](attachments/settings-security/delete-role-option.png)

3.  ポップアップダイアログで削除を確認します。

    ![](attachments/settings-security/delete-role-dialog.png)

ロールが削除されました。

{{% alert type="info" %}}

管理者ロールは削除または編集できません。

{{% /alert %}}

### 3.4 特定のページ/マイクロフローへのアクセス権の設定

アプリ内の特定の pages/microflow へのアクセスを設定するには 2 つの方法があります。

1.  To set access via **Roles and Permissions**, do the following:<br/> 1.1  Open **Roles and Permissions** > **Page**/**Microflow Access** tab.<br/> 1.2 Find the user role in the column and tick the box next to a page/microflow to open access for it, or untick – to restrict access. 以下の例では、ユーザーのページアクセスが制限されています。<br/>

    ![](attachments/settings-security/page-access-example.png)

2.  このページ/マイクロフローのプロパティを介してページ/マイクロフローへのアクセスを設定するには、以下を行ってください: <br/> 2.1 ページ/マイクロフローを開きます。<br/> 2.2. **プロパティ** > **アクセス権限** セクションと tick/untick **許可されるロール** に移動してアクセスを許可/制限します。<br/>

    ![](attachments/settings-security/permissions-section.png)

## 4デモユーザー {#demo-users}

デモユーザーは、アプリケーションに存在する各ユーザーロールのデモです。 デモユーザーを使用して、各ユーザーのロールに対するアプリの見た目を確認できます。 技術的な情報については、 [Demo Users](/refguide8/demo-users) を参照してください。

### 4.1 ロールのテスト {#testing-your-roles}

アプリが異なるロールでどのように見えるかを次のようにテストできます:

1. [アプリをプレビューする](publishing-app).

2. 画面の右側にあるユーザーアイコンをクリックします。

    ![](attachments/settings-security/user-icon.png)

4. 表示されたメニューバーで、デモユーザーを選択すると、アプリが対応するロールの観点から表示されます。

    ![](attachments/settings-security/select-user.png)

## 5 アプリユーザーの管理 {#managing-app-users}

Mendixアカウントを使用してアプリのエンドユーザーにデフォルトまたはカスタマイズされたユーザーロールを割り当てることができます。 これらは **App Users** と呼ばれ、一度承認されると、公開されたアプリにアクセスして使用し、テストし、フィードバックを提供することができます。

{{% alert type="info" %}}
アプリを公開した後にのみ、アプリユーザーを管理できます。
{{% /alert %}}

アプリユーザーを管理するには、 **ロールと権限** を開き、画面右上の **ユーザーの管理** をクリックします。

![](attachments/settings-security/manage-users-button.png)

開発者ポータルの [App User Management](/developerportal/collaborate/general-settings#managing-app-users) ページに移動します。 アプリにユーザーを招待し、ユーザーロールを管理することができます。

{{% alert type="info" %}}
開発者ポータルであなたのチームに参加するために招待された人は、アプリユーザーとして自動的に追加されません。 必要に応じてチームメンバーを招待する必要がある
{{% /alert %}}

{{% alert type="info" %}}
**ロールと権限** ページで新しいユーザーロールを作成した場合。 開発者ポータルでこのロールを表示して割り当てるには、まずアプリを公開する必要があります。
{{% /alert %}}

## 6 新しいサービスへの自動アップグレード {#upgrade}

アプリを公開しようとすると、まずアプリを保護するサービスのアップグレードが必要になることが通知されます:

{{% image_container width="300" %}}
![アップグレードが必要です](attachments/settings-security/upgrade.png)
{{% /image_container %}}

特別なサービスにより、アプリユーザーを管理することができます。 **Auto-Upgrade** をクリックすると、このサービスの最新バージョンへのアップグレードは自動的に行われます。

自動アップグレードに失敗した場合は、Studio Proでサービスがカスタマイズされたことを意味します。 この場合は、Studio Pro の手動アップグレードのみが可能です。

サービスがチームメンバーによってStudio Proでカスタマイズされていることを自動アップグレードが検出した場合。 Studio Proの手動アップグレードが最初に実行されることが通知されます。

## 7 続きを読む

* [セキュリティ](/refguide8/security)
* [Studio でセキュリティが有効になっている場合のモデルの変更](/refguide8/studio-security-enabled)
