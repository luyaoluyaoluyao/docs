---
title: "Mendix Studio Pro 8 から9へ移動"
category: "一般情報"
menu_order: 20
description: "Mendix 8からMendix 9へのアプリケーションの更新に関する詳細を提供します。これには、アプリの変換と非推奨機能に関するセクションが含まれます。"
tags:
  - "studio pro"
  - "スタジオ"
---

## 1つの紹介

Mendix Studio Pro 9とMendix Studio 9は、アプリを強化する強力な新しいツールを提供します。 変更の完全なリストについては、Studio Pro 9 および Studio 9 のリリースノートを参照してください。 既存の Studio Pro 8 または Studio 8 アプリをそれぞれの 9 バージョンにアップグレードする場合は、以下の情報を確認してください。

* Studio を Mendix 8 から 9 にアップグレードする場合は、以下の [Mendix 8 から 9 へのアップグレード](#studio-upgrade) を参照してください。
* Studio Pro 8 から Studio Pro 9 にアプリを変換する場合 Studio Pro 9 にアップグレードする前に、 [アプリを変更する](#studio-pro-upgrade) を参照してください。

## 2 Mendix 8 から 9 へのアップグレード {#studio-upgrade}

### 2.1 MS SQL Server の RCSI をオンにする

パフォーマンスを向上させ、デッドロックの可能性を減らすために。 Mendix 9では、MS SQL Serverを **Read Committed Snapshot Isolation** (RCSI) を **ON** にする必要があります。

同期段階中に Mendix 9はRCSIステータスのチェックを行い、それが **ON** ではなく、データベースユーザに自動的に行うための必要な権限がない場合、プロセスを中止する可能性があります。

## Studio Pro の Mendix 8 から 9 へのアップデート {#studio-pro-upgrade}

次のサブセクションでは、Mendix 8 から Mendix 9 へのアプリケーションの変換手順について説明します。 We recommend you first review the [Breaking Changes](/releasenotes/studio-pro/9.0#breaking-changes) section of the *Studio Pro 9.0* release notes as well as our updated [System Requirements](/refguide/system-requirements).

### 3.1 アプリのバックアップ

チームサーバーに最新の変更をコミットしていることを確認してください。 または、変換を開始する前にローカルアプリのバックアップを作成しました。

### 3.2 バージョン 8 の最新リリースにアップグレード

{{% alert type="warning" %}}
最初にMendix 8.12にアプリをアップグレードすると、Mendix 9にアップグレードすることが技術的に必要です。 ただし、Mendix 8: [8.18](/releasenotes/studio-pro/8.18) の最新バージョンにアップデートすることをお勧めします。
{{% /alert %}}

Mendix 8.18 にアップグレードするには、以下の手順に従ってください:

1. Studio Pro [8.18](/releasenotes/studio-pro/8.18) の最新パッチリリースをダウンロードします。
1. Studio Pro v8.18 でアプリを開きます。
1. 必要に応じてアプリのアップグレードを許可します。

### 3.3 Mendix 8アプリをレビューする

以下のセクションと組み合わせてアプリを確認し、Mendix 9にアップグレードする前にさらにアクションを取る必要があるかどうかを評価します。

アプリを実行し、すべての機能をテストし、エラーなしで動作するようにしてください。 アプリがアプリサービスを使用している場合は、Mendix 9でアプリサービスが非推奨となっているため、アプリをアップグレードする前にそれらを削除する必要があります。

Studio Proで開発中に表示される減価償却警告も修正してください。 コンソールとブラウザコンソールを使用してランタイムにも。

### 3.4 バージョン8のアプリを保存

必要に応じてアプリに戻ることができるように、アプリをバックアップまたはコミットします。

これで、アプリを Mendix 9 にアップグレードする準備ができました。 Studio Pro 8 でアプリを閉じることができます。

### 3.5 アプリをバージョン9にアップグレード

Studio Pro 9 でアプリを開き、Studio Pro がアプリをバージョン 9 にアップデートできるようにします。 Mendixは自動的にアプリをアップグレードします。

廃止された項目についてのすべてのエラーメッセージとメッセージを確認し、必要に応じて変更を行います。

### 3.6 すべてのウィジェットとモジュールをアップグレード {#upgrade-widgets}

問題の可能性を最小限に抑えるために、アプリケーションで使用されているすべてのウィジェットやその他のMarketplaceモジュールを最新バージョンに更新する必要があります。

マーケットプレイスで利用可能な新しいバージョンのモジュールがあるか確認してください。 アップグレード時に特定のアクションを実行する必要があるかどうかを確認するには、Marketplace のバージョンリリースノートを参照してください。

これらのキーウィジェット、リソース、アクションを更新してください。

* [ネイティブ モバイル リソース](https://marketplace.mendix.com/link/component/109513)
* [Nanoflow Commons](https://marketplace.mendix.com/link/component/109515)
* [データグリッド2](https://marketplace.mendix.com/link/component/116540)

一般的には、リリースノートで推奨されていない限り、モジュールを削除したり再インポートしたりしないでください。 削除して再インポートすると、モジュールに関連するデータや構成が失われる可能性があります。

### 3.7 アトラスモジュールの更新（任意）

Mendix 9には、新しいページテンプレートとビルディングブロックを含む新しいAtlasテーマが付属しています。 To get this theme, you can download the [Atlas Core](https://marketplace.mendix.com/link/component/117187), [Atlas Web Content](https://marketplace.mendix.com/link/component/117183) and [Atlas Native Content](https://marketplace.mendix.com/link/component/117175) module packages from the Marketplace.

### 3.8 アプリのレビューとテスト

最後に、以下のセクションを確認し、必要なすべての変更を行ったことを確認してください。 予期しない結果をアプリでテストします。

{{% alert type="success" %}}
おめでとうございます アプリは正常にMendix 9にアップグレードされ、通常通り作業を続けることができます。
{{% /alert %}}

## 4回のランタイムAPIの変更

Mendix 8 で廃止された Java API 呼び出しのほとんどは削除されました。 それでもJavaアクションでそのようなメソッドを使用している場合は、それらを交換または削除する必要があります。 減価償却されたコールを確認するには、 **Runtime API ドキュメント** 内の [Mendix 8 Server Runtime API](/apidocs-mxsdk/apidocs/runtime-api) リンクをクリックしてください。

さらに、Runtime API の変更の詳細については、Mendix Studio Pro 9.02 リリースノートを参照してください。

### 4.1 データベース固有の変更

Mendix 9より前に、MendixはMendixランタイムまたはデータベースエンジン自体に依存することで、データの一意性を確保することができました。 Mendix 9以降、 **Database** が唯一のオプションとなります。

アプリケーションがまだ一意性検証に Mendix ランタイムを使用している場合は、カスタムランタイム設定 `DataStorage を設定する必要があります。 nableDiagnostics <code> を` に `true`  して、データベースに存在する可能性のあるデータ冗長性の問題をチェックします。

見つかった場合は、 **Runtime の初期化中にエラーが発生しました。検出された固有の結合違反...** がログに記録されます。 これを解決するには、Mendix 9に移動する前にアプリを準備する必要があります。 [サポート リクエスト](/developerportal/support/submit-support-request) を送信することで、必要なツールを入手できます。

## 5ネイティブモバイルアプリのテスト

Mendix 9でネイティブモバイルアプリをテストしてプレビューするには、Make It Native AppのMendix 9バージョンをダウンロードする必要があります。

* [Google Play ストア](https://play.google.com/store/apps/details?id=com.mendix.developerapp.mx9) で Android Native 9 をダウンロード
* [Apple App Store](https://apps.apple.com/nl/app/make-it-native/id1542182000) で iOS 向け Native 9 をダウンロード

ネイティブアプリで最高の結果を得るために 上記の [すべてのウィジェットとモジュールのアップグレード](https://marketplace.mendix.com/link/component/109513) セクションに記載されている [ネイティブモバイルリソース](#upgrade-widgets) モジュールを更新したことを確認してください。

## 6 クライアント API の変更

Mendix 9で非推奨で削除されたクライアントAPIは実際に削除されました。 `のような大きなライブラリ。 s <code> ,`react `,`, `react-native`, そして、クライアントに同梱されている他のいくつかは、最新バージョンに更新されました。 これは、カスタムウィジェットやプラグイン可能なウィジェットや JavaScript アクションに影響を与える可能性があります。 詳細については、 [Studio Pro 9.0](/releasenotes/studio-pro/9.0#breaking-changes) リリースノートの *Breaking Changes* セクションを参照してください。

## 7つのネイティブ依存関係

Mendix 9 native apps no longer include non-essential native libraries like `react-native-maps`, `react-native-ble-plx`, `react-native-geocoder`, and others by default. 代わりに、コンポーネントのネイティブ依存性を宣言する新しい機能が Mendix 9 に導入されました。 すべてのプラグイン可能ウィジェットまたは JavaScript アクションは、使用するネイティブライブラリを宣言する必要があります。 これにより、不要なライブラリが含まれていない場合に必要なライブラリのみにネイティブアプリをバンドルできます。

pluggable ウィジェットまたは JavaScript アクションがネイティブリンクを必要とするライブラリを使用している場合。 それらのネイティブライブラリをコンポーネントの依存関係として定義するには、ウィジェットとアクションを更新してください。 ネイティブ依存関係の詳細については、 [ネイティブ依存関係の宣言](/apidocs-mxsdk/apidocs/pluggable-widgets-native-dependencies) を参照してください。

## 8 XPath クエリエンジン 9 {#query-engine-9}

Mendix 9 contains a new XPath query engine called *query engine 9* or QE9, replacing the current engine called *query engine 7* or QE7. クエリエンジン間で機能にいくつかの変更があります:

* 関連付けが [両側からナビゲート可能な](/refguide/association-properties#navigability)の場合、両方のエンティティは、関連付けの可読性を宣言するアクセスルールを定義することができます。 このような関連付けの場合、QE9 は常に現在の XPath の左側にあるエンティティを使用してアクセシビリティを決定します。 For example: in the query `//Customer[Customer_Address/Address/City = 'Rotterdam']`, the access rules defined in `Customer` will be used for the association, whereas in `//Address[Customer_Address/Customer/Lastname = 'Doe']`, the rules in `Address` will be used for that same association. QE7では、動作がよく定義されていませんでした。

* QE9は、データを取得する際に厳密に最小特権原則に従うように書かれています。 これにより、エンドユーザーに見えるデータが少なくなる可能性があります。

* Studio Pro では許可されていませんが、Java アクションの制約として boolean ではない属性を使用することができました。 例: `//Address[City]`. QE7はこのような問い合わせを受け付けますが、データベースによっては予期せぬ結果が得られることがあります。 QE9はそのようなクエリを拒否します。

* サポートされていない、またはドキュメントされていないが、Java アクションで `//Customer/Customer/Customer_Address/Address` のようなクエリを使用することができます。 If an instance of `Address` is reachable from multiple `Customer` instances, QE7 would return the instance of `Address` multiple times. QE9は、 `Address` の一致する各インスタンスを一度だけ返します。

## 9 続きを読む

* [Studio Pro 9 リリースノート](/releasenotes/studio-pro/9.0)