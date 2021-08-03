---
title: "Cloud Foundryの設定を編集"
parent: "run-menu"
tags:
  - "Cloud Foundry"
  - "デプロイ"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/edit-cloud-foundry-settings-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**Edit Cloud Foundry Settings** メニューオプションでは、アプリケーションをCloud Foundryインスタンスにデプロイするために必要な情報を指定できます。

![クラウドファウンドリー設定メニュー項目を編集](attachments/run-menu/edit-cf-settings.png)

{{% alert type="info" %}}
Cloud Foundryへのデプロイの詳細は [Cloud Foundry: Deploy](/developerportal/deploy/cloud-foundry-deploy)をご覧ください。
{{% /alert %}}

## 2 資格情報の入力

Cloud Foundryデプロイメント用にアプリを構成する最初のステップは、使用したいCloud Foundryアカウントのアカウント情報を入力することです。

![クラウドファウンドリー資格情報を入力してください](attachments/run-menu/cloud-foundry-credentials.png)

以下で説明されているように画面に詳細を入力し、 **Next** をクリックして指定された資格情報を検証し、次の構成ステップを表示します。

### 2.1 API Endpoint

デプロイに使用されるCloud Foundryプラットフォームの **APIエンドポイント** を定義するURL。

### 2.2 ユーザー名

Cloud Foundryアカウントの **ユーザー名**。

### 2.3 パスワード

Cloud Foundryアカウントの **パスワード**。

## 3クラウドファウンドリアプリの選択

2番目のステップでは、既存のアプリを選択したり、新しいアプリを作成したりすることができます。 ここでMendixアプリが展開されます。

![Cloud Foundryアプリの設定を入力](attachments/run-menu/cloud-foundry-app-settings.png)

### 3.1 組織

使用する **組織** を選択します。 利用可能な組織がない場合は、Cloud Foundryアカウントで組織を構成する必要があります。 Mendix Studio Proから新しいものを作成することはできません。

### 3.2 スペース

使用する **スペース** を選択します。 使用する領域は、Cloud Foundryアカウントに既に設定されている必要があります。 Mendix Studio Proから新しいものを作成することはできません。

### 3.3 アプリ

Either **Select existing app** if you want to use an existing app environment, or **Create new app** if you want to create a new app environment.

#### 3.3.1 既存のアプリを選択

**既存のアプリを選択** すると、ドロップダウンリストから正しいアプリを選択することができます。

#### 3.3.2 新しいアプリを作成

**新しいアプリを作成** する場合は、次の手順を実行する必要があります。

1. ドロップダウンからアプリを実行する **ドメイン** を選択します。
2. アプリの **アプリ名** を入力します。

アプリの URL は {App name}(ドメイン) になります。

### 3.4 Buildpack

Cloud Foundryアプリで使用したい **Buildpack** のURLを入力できます。 デフォルトのMendixビルドパックを使用したくない場合にのみ、これを変更してください。
