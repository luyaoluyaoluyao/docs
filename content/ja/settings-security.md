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

## 2 セキュリティの概要 {#overview}

デフォルトでアプリでセキュリティが有効になっているかどうか セキュリティがStudio Proで有効になっているかどうかと、そこでの設定方法によって異なります。 次のケースに出くわすことができます:

1. Studio Proのアプリのセキュリティーは **オフ** です。 In this case, you can either enable it via **App Settings**>**Roles and Permissions** >the **Enable Security** button, or you will be prompted to enable security, when you try to [publish the app](publishing-app).

    {{% image_container width="300" %}}![Secure Your App Pop-up Window](attachments/settings-security/security-pop-up.png) {{% /image_container %}}

    {{% alert type="info" %}}セキュリティを有効にすると、アプリ全体で有効になります。 Studio Proに表示されているモデルには、チェックと変更が適用されています。 これらのチェックと変更に関する技術的な情報については、 [Studio でセキュリティが有効になっている場合のモデルの変更](/refguide/studio-security-enabled).{{% /alert %}}

2. セキュリティはStudio Proで **プロダクション** レベルに設定され、設定はStudioと互換性があります。 この場合、Studio で **ロールと権限** を表示および編集できます。 (Studio と互換性のあるセキュリティ設定の詳細については、こちらをご覧ください。 [Studio でセキュリティが有効になっている場合のモデル変更](/refguide/studio-security-enabled#studio-compatible) の *Studio互換性* セクションを参照してください。

    ![](attachments/settings-security/roles-and-permissions-screen.png)

3. セキュリティはStudio Proで **プロトタイプ/デモ** または **プロダクション** レベルに設定されており、設定はStudioと互換性がありません。 この場合、Studio で **ロールと権限** のみ表示できますが、編集できません。 (Studio と互換性のあるセキュリティ設定の詳細については、こちらをご覧ください。 [Studio でセキュリティが有効になっている場合のモデル変更](/refguide/studio-security-enabled#studio-compatible) の *Studio互換性* セクションを参照してください。

    ![](attachments/settings-security/security-read-only.png)



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

新しいページ/microflow/workflow が作成されると、Studio のデフォルトのパーミッションが設定されます。 つまり、アプリ内の既存のロールはすべて、新しく作成されたドキュメントにアクセスできます。

{{% alert type="warning" %}}
ページ/microflow/workflow がコピー&ペーストされている場合、新しいドキュメントに対して Studio のデフォルトのパーミッションが設定されます。 その文書の権限を確認することをお勧めします。
{{% /alert %}}

**ロールと権限** 画面は以下のタブで構成されます。

* ロール
* ページアクセス
* マイクロフローアクセス
* ワークフローアクセス

**ロール** タブにはすべてのロールが表示され、アクセスできるページ数とマイクロフロー数が表示されます。

The **Page Access**,  **Microflow Access**, and **Workflow Access** tabs contain a table where all pages/microflows/workflows are listed in rows, and all roles are placed in columns.

特定のロールのみがページ、マイクロフロー、またはワークフローにアクセスできます。ロールへのアクセスを許可する適切なボックスを選択します。

すべてのページ、マイクロフロー、またはワークフローを選択/選択解除するには、ユーザー ロールの横にある **その他のオプション** (楕円形) アイコンをクリックします。

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

2.  **その他のオプション** (楕円形) アイコンをクリックし、 **編集** を選択します。

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

### 3.4 特定のページ/マイクロフロー/ワークフローへのアクセスを設定する

アプリ内の特定の pages/microflows/workflow のアクセスを変更するには 2 つの方法があります。

1.  **ロールと権限**でアクセスを設定するには、以下を行います。
    2.  **ロールと権限を開く** > **ページ**/**Microflow/Workflow Access** タブ。
    3.   列内のユーザーロールを見つけて、ページ/microflow/workflow の横のボックスにチェックを入れ、アクセスを開きます。 またはチェックを外すとアクセスが制限されます。 たとえば、ユーザーロールのページアクセスを制限できます。

    ![](attachments/settings-security/page-access-example.png)

2.  このページ/マイクロフロー/ワークフローのプロパティを介してページ/マイクロフローへのアクセスを設定するには、次の手順を実行します。
    3.  ページ/マイクロフロー/ワークフローを開きます。
    4.  **プロパティ** > **アクセス権限** セクションと tick/untick **許可されるロール** に移動してアクセスを許可/制限します。

        {{% image_container width="300" %}}![](attachments/settings-security/permissions-section.png){{% /image_container %}}

## 4デモユーザー {#demo-users}

デモユーザーは、アプリケーションに存在する各ユーザーロールのデモです。 デモユーザーを使用して、各ユーザーのロールに対するアプリの見た目を確認できます。 技術的な情報については、 [Demo Users](/refguide/demo-users) を参照してください。

### 4.1 ロールのテスト {#testing-your-roles}

アプリが異なるロールでどのように見えるかを次のようにテストできます:

1. [アプリをプレビューする](publishing-app).

2. 画面の右側にあるユーザーアイコンをクリックします。

    {{% image_container width="400" %}}![](attachments/settings-security/user-icon.png){{% /image_container %}}

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

特別なサービスにより、アプリユーザーを管理することができます。 2020年4月1日現在のサービスを改善しました。 **自動アップグレード** をクリックすると、このアップグレードは自動的に行われます。

自動アップグレードしない場合は心配する必要はありません。アプリはセキュリティ保護され実行されます。 ただし、アップグレードするまで、新しいバージョンのアプリを公開することはできません。

自動アップグレードに失敗した場合は、Studio Proでサービスがカスタマイズされたことを意味します。 この場合は、Studio Pro の手動アップグレードのみが可能です。

サービスがチームメンバーによってStudio Proでカスタマイズされていることを自動アップグレードが検出した場合。 Studio Proの手動アップグレードが最初に実行されることが通知されます。 Studio Pro でサービスをアップグレードする方法についての詳細は、 [AppCloudServices から Mendix SSO へのアップグレード](/developerportal/deploy/upgrading-to-mendix-sso-from-acs) を参照してください。

## 7 続きを読む

* [セキュリティ](/refguide/security)
* [Studio でセキュリティが有効になっている場合のモデルの変更](/refguide/studio-security-enabled)
