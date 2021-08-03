---
title: "Studio でセキュリティが有効になっている場合のモデルの変更"
parent: "セキュリティ"
description: "Mendix Studio でセキュリティが有効になっている場合のプロジェクトのチェックと変更について説明します。"
tags:
  - "studio pro"
  - "セキュリティ"
  - "スタジオ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/studio-security-enabled.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、Mendix Studio でセキュリティが有効になっている場合に自動的に適用されるモデル変更のプロセスについて説明します。 For more information on security settings in Studio, see [Security, Roles & Permissions](/studio8/settings-security) in the *Studio Guide*.

ユーザーはStudioからセキュリティを有効にできます。 While the Studio user simply clicks the **Enable Security** button, as a result, security is set to **Production** for the project and a number of checks and changes (if necessary) are performed automatically.

## 2プロセスの概要

セキュリティが有効になっている場合、いくつかのレベルでチェックと変更が行われます。

1. Studio はセキュリティが有効かどうかをチェックします。 セキュリティが **プロトタイプ/デモ** または **プロダクション**に設定されている場合、プロセスは停止します。 セキュリティがオフの場合、以下の手順が実行されます。
2. The [Mendix SSO](/appstore/modules/mendix-sso) module is set up if the project does not have it yet (for more information on this process, see the [Modules Set Up](#module-set-up) section). Mendix SSO モジュールがすでにこのプロジェクトにインストールされている場合、プロセスは停止します。
3. Studio does checks and changes (if necessary) to [demo users](demo-users) , [module roles](module-security) , and [user roles](user-roles) (for more information on this process, see the [Module Roles and Demo Users Set Up](#module-roles-and-demo-users) section).
4. Studio は、エンティティ（およびその属性と関連付け）に対するアクセスルールを設定します。 エンティティがまだアクセスルールを持っていない場合(このプロセスの詳細については、 [エンティティアクセスの設定](#entity-access) セクションを参照してください)。
5. Studio checks if the *login.html* file exists, backs it up, and replaces it with a new version (for more information on this process, see the [File Set Up](#file-set-up) section).
6. Studio does checks and changes (if necessary) at the [Project Security](project-security) level (for more information on this process, see the [Project Security Level Set Up](#project-security-level) section).

{{% alert type="info" %}}

Studio Proで既に **プロトタイプ/デモ** または **プロダクション** にセキュリティが設定されている場合。 これらの設定は、Studio ロールとパーミッションの設定と互換性がありません(高度すぎます)。 この場合、Studio でロールや権限を編集することはできません。 For more information on security settings in Studio, see [Security, Roles & Permissions](/studio8/settings-security) in the *Studio Guide*.

{{% /alert %}}

## 3つのモジュール設定 {#module-set-up}

Studio でセキュリティが有効になっている場合、Mendix SSO モジュールが設定されます。 このモジュールはアプリでシングルサインオンとユーザー管理を可能にします。

シングルサインオンを有効にするには、次のチェックと変更を実行します。

1. Mendix SSO スタートアップ microflow (MendixSSO.MendixSSO_AfterStartup) が作成されます。 このプロセスの成果の可能性についての詳細は、 [Project Security Level Set Up](#project-security-level) セクションを参照してください。
2. *login.html* ファイルはチェックされ、必要に応じて変更されます。 詳細については、 [File Set Up](#file-set-up) セクションを参照してください。

Mendix SSO モジュールは、アプリケーションにユーザー管理も追加します。 ユーザー管理を使用すると、アプリユーザーを管理できます。

{{% alert type="info" %}}すでにMendix SSO モジュールがインストールされている場合、Studio からのセキュリティを有効にすることはできません。 以下の要件を満たすStudio Proでのみセキュリティを手動で設定できます。

* セキュリティは **プロダクション**に設定する必要があります <br/>
* シングルサインオンを有効にするためにMendix SSOモジュールを設定する必要があります

{{% /alert %}}

## 4モジュールの役割とデモユーザーが設定 {#module-roles-and-demo-users}

After the **After startup** microflow is set up, Studio checks if the *Administrator* role, the *User* role, and *demo users* exist and creates them when necessary:

1.  Studio は、 **プロジェクト** レベルに管理者ロールとユーザーロールが存在するかどうかを確認します。 存在しない場合は、作成されます。

    ![](attachments/studio-security-enabled/project-security-user-roles.png)

2.  その後は Studio では、管理者とユーザー ロールがプロジェクトの各モジュールに存在するかどうか、またそれらが対応するプロジェクト ロールにリンクされているかどうかを確認します。

    ![](attachments/studio-security-enabled/module-roles.png)

    このチェックで考えられる結果は以下の通りです:<br/> a. 管理プロジェクトロールまたはユーザプロジェクトロールに接続されている1つのモジュールに2つ以上のモジュールロールがある場合。 Studioと互換性がありません Studio はこれらのロールを変更しませんが、ロール や権限はStudio では編集できません。<br/> b. モデルに管理者プロジェクトロールまたはユーザプロジェクトロールに接続されているモジュールロールがある場合。 Studio は、モジュール ロールの名前がプロジェクト ロールと同じかどうかをチェックします。 名前が異なる場合、Studio はプロジェクト ロールからこのモジュール ロールを切断します。 は、プロジェクトのロール名と同じ名前を持つ新しいものを作成し、それをプロジェクトのロールにリンクします。<br/> c. モデルに管理者プロジェクトロールまたはユーザプロジェクトロールに接続されているモジュールロールがない場合、Studioはこれらのロールを作成します。 <br/> d モジュールロールが存在する場合、その名前はプロジェクト ロールと同じです。 ただし、このプロジェクト ロールにはリンクされていません。Studio は新しいモジュール ロールを作成します。 Administrator_1 ** または *User_1*という名前を付け、それを対応するプロジェクトロールにリンクします。<br/>

    {{% alert type="info" %}}Studio は、システムモジュールからプロジェクトレベルの管理者ロールに管理者ロールをリンクします。 *Studio から作成された他のすべてのプロジェクト ロール* 。 元の User プロジェクト ロールを含めると、システム モジュールの User モジュール ロールにリンクされます。
    {{% /alert %}}

3. Studioは、プロジェクトレベルのAdministratorロールをMendixSSO.AdministratorとAdministratorとリンクします(存在しない場合は、Studioはリンクしません)。 プロジェクト レベルのユーザー ロールは MendixSSO.User, Administration.User にリンクされています(存在しない場合は、Studio はリンクを行いません)。 他のMendix Marketplace モジュールはすべて変更されません。

    Studio で作成された他のすべてのユーザー ロールは、MendixSSO および Administration モジュールの MendixSSO および Administration にリンクされます。

4. Studio は、 *demo_administrator* と *demo_user* という名前のデモユーザーが存在するかどうかをチェックし、そうでなければ、Studio がそれらを作成します。

{{% alert type="warning" %}}

管理者とユーザーのロールが既に存在し、 [Studio](#studio-compatible)と互換性がある場合。 彼らはすべてのマイクロフロー、ナノフロー、ページ、エンティティ(エンティティの属性と関連性を含む)にアクセスすることができます。

新しく作成されたすべてのロールは、Studio 内にあるすべてのページ、マイクロフロー、ナノフロー、およびエンティティ(属性と関連付けを含む)にアクセスできます。 マーケットプレースのページ、マイクロフロー、エンティティ(属性と関連付け)を除きます。

また、すべての新しいページ、マイクロフロー、 そして、Studio で作成されたエンティティ(属性と関連付け)は、既存のすべてのアプリのロールに対してデフォルトでアクセスできます。

{{% /alert %}}

## 5 エンティティアクセス設定 {#entity-access}

セキュリティを有効にすると、Studio はそれらを持たないすべてのエンティティ(およびそれらの属性と関連付け)に対するアクセス ルールを作成します。 次のアクセス ルールの設定が適用されます:

*   Studio によって生成されたことを示す **アクセス ルール** の **ドキュメント** に説明が追加されます。

    ![](attachments/studio-security-enabled/start-up-microflow.png)

*  匿名ロールを除く現在のモジュールのすべてのロールは、 ** を作成し、 *エンティティの* 権限を削除します。 これらのエンティティの属性と関連性については、次のルールが作成されます。

  *  anonymous roles を除く現在のモジュールのすべてのロールには、 *read* and *write* access for attributes

     {{% alert type="info" %}}エンティティがSystem.ImageやSystem.FileDocumentから継承される場合があります。 これらの継承された属性のいくつかは、読み取り/書き込みに設定できないため、読み取り専用に設定されます。
     {{% /alert %}}

* 匿名ロールを除く現在のモジュール内のすべてのロール has *read* and *write* access for association if the entity is the association owner

{{% alert type="info" %}}

Studio でエンティティを作成する場合は、上記のルールが作成されます。

エンティティをコピー&ペーストすると、元のエンティティのアクセスルールはできるだけ多くコピーされます。 ただし、エンティティに一般化があり、それを別のプロジェクトにコピーすると、一般化は削除されます。

{{% /alert %}}

## 6 ファイル設定 {#file-set-up}

最後のステップとして、Studio はプロジェクトの *login.html* ファイルを変更します。

If the *login.html* file exist, Studio backs it up in the same folder under the name *login_backup_year-month-day_hour-minute.html*, indicating the date and time of the backup. Studio は、 *login.html という名前で新しいファイルも作成します*

*login.html* ファイルが存在しない場合、Studio は *login.html という名前で作成します*

この手順により、シングルサインオンが可能になり、既存のユーザーはMendixアカウントを使用して自動的にアプリにサインインできます。

## 7 プロジェクトのセキュリティレベルを設定 {#project-security-level}

**プロジェクト** レベルでは、Studio は次の操作を行います。

1. **Project Security** は **Production** に設定されています。

2.  Studio は、 **起動後** マイクロフローが **プロジェクト** > **設定** > **ランタイム** に存在するかどうかをチェックします。

    ![](attachments/studio-security-enabled/start-up-microflow.png)

    このチェックには2つの可能性があります:<br/> a. モデルに **起動後** マイクロフローが含まれていない場合は、 *MendixSSO.MendixSSO_AfterStartupt* マイクロフローが使用されます。<br/> b. モデルに **起動後の** マイクロフローが含まれている場合、Studioは既存のものと同じ場所に *CallBothStartupMicroflows* マイクロフローを作成します。 *CallBothStartupMicroflow* は *MendixSSO.MendixSSO_AfterStartup* マイクロフローを最初に呼び出し、次にプロジェクトに既に存在していたマイクロフローを呼び出します。

## 8スタジオ互換性 {#studio-compatible}

Studio Pro のセキュリティ設定は Studio と互換性があります (つまり、ロールや権限は Studio で編集できます)。 以下のすべての基準が満たされた場合:

* Mendix SSO モジュールがインストールされました
* セキュリティレベルは本番環境に設定されています
* デモユーザーが有効になっています
* デモユーザーは、プロジェクトのロール名と同じ名前で、 *demo_* プレフィックスを持つ必要があります (例えば、demo_user)
* デモユーザーは、ユーザーに接続されているユーザーロールを1つだけ持つ必要があります
* ユーザーロールにはデモユーザーが接続されている必要があります
* ユーザーロールはモジュールに接続されているモジュールごとに1つのロールを持つ必要があります (Studio はシステムまたはマーケットプレイスモジュールをチェックしません)
* モジュールロールには複数のユーザーロールが接続されていません

## 9 続きを読む

* [セキュリティ、ロール & 権限](/studio8/settings-security)
* [プロジェクトのセキュリティ](project-security)
* [モジュールのセキュリティ](module-security)
