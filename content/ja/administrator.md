---
title: "管理者"
parent: "project-security"
menu_order: 20
tags:
  - "studio pro"
  - "管理者"
  - "プロジェクトのセキュリティ"
  - "セキュリティ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/administrator.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**プロジェクトセキュリティ** の **管理者**タブで 管理者ユーザーのデフォルトの資格情報とユーザーロールを変更できます。

![](attachments/administrator/project-security-administrator.png)

## 2件の管理者プロパティ {#administrator-properties}

**管理者** タブでは、次のプロパティを使用できます。

* [ユーザー名](#user-name)
* [パスワード](#password)
* [ユーザーのロール](#user-role)

### 2.1 ユーザー名 {#user-name}

ユーザー名は管理者としてアプリケーションにサインインするために使用されます。

デフォルト: *MxAdmin*

{{% alert type="info" %}}
これは一般的な知識なので、カスタムユーザー名に変更する方が安全です。
{{% /alert %}}

### 2.2 パスワード {#password}

パスワードは管理者としてアプリケーションにサインインするために使用されます。 **Show password** をクリックしてパスワードを表示します。

デフォルト: *1*

{{% alert type="info" %}}
このパスワードは Mendix がローカルで実行されている場合にのみ使用されます。 開発者ポータルで [環境](/developerportal/deploy/environments-details) のパスワードを変更できます。
{{% /alert %}}

{{% alert type="info" %}}
これは一般的な知識なので、カスタムパスワードに変更する方が安全です。
{{% /alert %}}

### 2.3 ユーザーロール {#user-role}

管理者に割り当てられたユーザーロール。 詳細については、 [ユーザー ロール](user-roles) を参照してください。

Default: *Administrator*

{{% alert type="info" %}}
管理者は常に作成され、デフォルトでSystem.Administratorロールを持っています。 System.Administrator ロールを使用すると、アプリケーションのユーザーを管理できます。

無料アプリの場合 アプリケーションを自動的に作成したユーザーは、デフォルトでこの役割を持っているため、その環境でユーザーを管理するために使用できます。

この役割は、ユーザーライセンス制限を超えた場合に役立ちます。その場合は、このシステムを持つユーザーを使用できます。 あなたのユーザーを管理するためにサインインするためのdunitatorの役割。
{{% /alert %}}

{{% alert type="warning" %}}
アプリケーションがローカルにデプロイされていない場合、例えばMendix Cloudにデプロイされます。 管理者アカウントのユーザーロールへの変更は、管理者パスワードが変更されるまで適用されません。 管理者パスワードの変更方法については、 [アクション](/developerportal/deploy/environments-details#actions) *環境詳細* のセクションを参照してください。
{{% /alert %}}

## 3 続きを読む

* [プロジェクトのセキュリティ](project-security)
* [ユーザーの役割](user-roles)
* [デモユーザー](demo-users)
* [匿名ユーザー](anonymous-users)
* [パスワードポリシー](password-policy)
