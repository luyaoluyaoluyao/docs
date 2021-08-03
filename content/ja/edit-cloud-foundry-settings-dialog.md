---
title: "クラウドファウンドリー設定ダイアログを編集"
parent: "ダイアログ"
tags:
  - "Cloud Foundry"
  - "デプロイ"
---

## 1つの紹介

このダイアログでは、アプリケーションをCloud Foundryインスタンスにデプロイするために必要な情報を指定します。

{{% alert type="info" %}}

Cloud Foundryへのデプロイの詳細については、 [Developer Portal Guide](/developerportal/deploy/cloud-foundry-deploy) の *Cloud Foundry: Deploy* を参照してください。

{{% /alert %}}

## 2 資格情報の入力

Cloud Foundryデプロイメント用のアプリケーションの構成の最初のステップは、使用したいCloud Foundryインスタンスのアカウント情報を入力することです。

以下で説明されているように画面に詳細を入力し、 **Next** をクリックして指定された資格情報を検証し、次の構成ステップを表示します。

### 2.1 API endpoint

これは、デプロイに使用されるCloud Foundryプラットフォームの **APIエンドポイント** を定義するURLです。

### 2.2 ユーザー名

これはCloud Foundryアカウントの **ユーザー名** です。

### 2.3 パスワード

これは Cloud Foundry アカウントの **パスワード** です。

「次へ」ボタンを押すと、指定した資格情報が検証され、次の設定ステップが表示されます。

## 3クラウドファウンドリーアプリの選択

2番目のステップでは、MendixアプリがデプロイされるCloud Foundryインスタンス内のアプリを選択できます。

### 3.1 組織

使用する **組織** を選択します。 利用可能な組織がない場合は、Cloud Foundryアカウントで組織を構成する必要があります。 Desktop Modelerから新しいものを作成することはできません。

### 3.2 スペース

使用する **スペース** を選択します。  利用可能なスペースがない場合は、Cloud Foundryアカウントで設定する必要があります。 Desktop Modelerから新しいものを作成することはできません。

### 3.3 アプリ

Either **Select existing app** if you want to use an existing app environment, or **Create new app** if you want to create a new app environment.

#### 3.3.1 既存のアプリを選択

**既存のアプリを選択** すると、ドロップダウンリストから正しいアプリを選択できます。

#### 3.3.2 新しいアプリを作成

If you **Create new app**, you need to select the **Domain** in which the app will run in the drop-down list, and then enter the **App name** for the app.

アプリの URL は {App name}(ドメイン) になります

### 3.4 Buildpack

Cloud Foundryアプリで使用したい **Buildpack** のURLを入力できます。 デフォルトのMendixビルドパックを使用したくない場合にのみ、これを変更してください。
