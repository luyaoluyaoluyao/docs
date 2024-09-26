---
title: "ランタイムデプロイ"
category: "Mendix Runtime"
description: "Mendix Runtimeのデプロイ方法に関する説明"
menu_order: 30
tags:
  - "ランタイム:"
  - "デプロイする"
  - "mxbuild"
  - "ランタイムサーバー"
  - "M2ee"
---

## 1つの紹介

Mendixモデルをクラウドで実行されているアプリに変換するには、デプロイする必要があります。 このドキュメントでは、プロジェクトのデプロイの背後にある概念と、クラウドで実行を開始するプロセスについて説明します。 アプリケーションのデプロイ方法についての技術的な詳細は、開発者ポータルのドキュメントの [Deployment](/developerportal/deploy/) セクションを参照してください。

このデプロイメントの説明は、クラウドで実行されているアプリケーションに基づいています。 Mendixはテスト用にローカルで実行することもできますが、これは概念的にも同じです。

## 2 Mendix ランタイムデプロイ

構造的なエラーのないMendixアプリを作成した場合は、それをデプロイして実行する必要があります。

以下は、アプリのデプロイにかかわるプロセスを示すグラフです。 各プロセスとコンポーネントは、チャートの下に記載されています。

![Mendix Runtime のデプロイ方法](attachments/runtime/runtime-deployment.png)

### 2.1 デプロイ

これは、アプリケーションのデプロイメントを管理するために、Mendix Cloud Portalによって開始されます。

### 2.2 Docker 環境

これは、Buildpackが処理するためのCloud-Foundryのような方法でdocker環境を指定するdocker環境仕様です。

### 2.3 プロジェクト MPK

これはStudio ProまたはStudioが作成したプロジェクトモデルです。 Mendix Runtime によって直接解釈することはできません。

### 2.4 MX ビルド

これは、mpk形式のアプリをMendix Runtimeで解釈できるmda形式に変換します。

### 2.5 Cloud Foundry

これは、Cloud Foundry環境を作成するためのコマンドラインインタプリタであり、実行される環境へのコードのプッシュを可能にします。

### 2.6 Buildpack

ビルドパックは、Mendixモデルのクラウド環境へのデプロイを制御するMendixスクリプトです。 次のようなタスクを行います

* ターゲット環境とデータベースやファイルストレージなどのバインドされたサービスを識別します
* mpk形式のプロジェクトを受け取った場合、Mxbuildを起動してmda形式に変換します
* Java Runtime Environment の正しいバージョンを識別し、それを環境にプッシュします。
* これは、Mendix Runtimeの正しいバージョンを識別し、m2eeを使用してRuntime Serverを環境へプッシュします。 プロジェクトを定義するプロジェクトmdaへのリンクで

### 2.7 プロジェクト MDA

Mendix は mda 形式の Mendix アプリで、Mendix ランタイムによって解釈できる方法でアプリを定義します。

### 2.8 CDN

このデータリポジトリには、Mendix RuntimeおよびMx Buildのバージョンなどのデプロイメントプロセスのコンポーネントが保存されます。

### 2.9 Java RE

これは、Runtime Serverを実行するために使用されるJava Runtime Environment (JRE)です。 JRE のバージョンは Runtime Server のバージョンによって異なります。 たとえば、Mendix 7 は JRE バージョン 8 で、Mendix 8 は JRE バージョン 11 で実行されます。

### 2.10 M2ee

M2eeは、Mendixアプリのデプロイに使用されるPythonで書かれたヘルパーツールのコレクションです。 これは、ターゲットプラットフォームに応じて、m2ee-toolsとm2ee-sidecarの2つの形式があります。 これは、Java REを起動し、Runtime Serverバイナリ(jar)ファイルの関連バージョンを指すことによってRuntime Serverを起動します。 起動後、m2eeはRuntime Serverに接続し、どのMendixアプリケーションモデルをロードするかを指定します。

### 2.11 ランタイムサーバー

これはアプリを実行するインタプリタです。 詳細については、 [Runtime Server](runtime-server) を参照してください。

