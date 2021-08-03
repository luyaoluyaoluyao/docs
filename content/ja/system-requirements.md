---
title: "システム要件"
category: "一般情報"
menu_order: 10
description: "Mendix プラットフォームを使用するためのシステム要件を提示します。"
tags:
  - "studio pro"
---

## 1つの紹介

このドキュメントでは、Mendix プラットフォームのさまざまな部品に対するシステム要件を示します。

## 2 Mendix Studio Pro {#sp}

Mendix [Studio Pro](modeling) は、64 ビット版の Windows 10 リリース 1809 以降でサポートされています。 Studio Proは、M1などのApple Silicon Mac上のWindowsエミュレータや、他のARMベースのマシン上では実行されません。

次のフレームワークが自動的にインストールされます(必要な場合):

* Microsoft .NET Framework 4.7.2 および該当するすべての Windows セキュリティパッチ
* Microsoft Visual C++ 2010 SP1 再頒布可能パッケージ
* Microsoft Visual C++ 2015 再配布可能パッケージ
* JDK 11がインストールされていない場合は、AdoptOpenJDK 11またはOracle JDK 11(前者は自動的にインストールされます)

{{% alert type="info" %}}
Studio Proの **Edit** > **Preferences** メニュー項目からローカルでのビルドと実行に使用するJDKを選択できます。
{{% /alert %}}

{{% alert type="warning" %}}
Studio Proに組み込まれたデータベースビューアは( [開発データベースの共有方法](/howto/collaboration-requirements-management/sharing-the-development-database)で説明されているように)JDK 11では動作しないことに注意してください。 6または11.07。
{{% /alert %}}

### 2.1 ファイアウォールの設定

Studio Pro は以下の URL にアクセスする必要があります。 ファイアウォールが現在これらをブロックしている場合は、ホワイトリストに登録する必要があります。

* `*.mendix.com`
* `*.mendixcloud.com`
* `*.teamserver.sprintr.com`

### 2.2 TortoiseSVN

Studio Pro と組み合わせて TortoiseSVN を使用したい場合は、 [TortoiseSVN](https://tortoisesvn.net/) のウェブサイトから最新バージョンをダウンロードしてください。

{{% alert type="warning" %}}
Mendix Studio Pro は Subversion 1.9 の作業コピーを使用します。 Mendix Desktop Modelerの以前のバージョンでは、Subversion 1.7 の作業コピーが使用されていました。 これらの作業コピーのバージョン **は互換性がありません**。<br />
<br />
常にアプリモデルと一致する TortoiseSVN のバージョンを使用してください。 Mendixバージョン7.xまたは6からローカルモデルを開く場合。 最新バージョンの TortoiseSVN **では、Mendix** では開くことができなくなります。
{{% /alert %}}

### 2.3 ファイルの場所

アプリケーションをローカルでアクティブに開発および実行するためのツールです。 アプリフォルダはローカルドライブ(C:など)または [Windowsドライブ文字](https://support.microsoft.com/en-us/windows/map-a-network-drive-in-windows-10-29ce55d1-34e3-a7e2-4801-131475f9557d)にマッピングされているネットワークフォルダにある必要があります。

### 2.4 サポートされている Git サービス プロバイダー {#supported-providers}

#### 2.4.1 Azure ReposとAzure DevOps Server

Microsoft の [Azure Repos](https://azure.microsoft.com/en-us/services/devops/repos/) ホストの Git サービスを両方サポートしています。 および Git リポジトリをプライベートインフラストラクチャにホスティングするためのオンプレミスソリューションである Azure DevOps Server (旧Team Foundation Server)。

ユーザーアカウントのPATを取得するには、Microsoftドキュメントの [パーソナルアクセストークンを使用する](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page) の手順を参照してください。

トークンの `コード (完全)` 権限が必要です。

##### 2.4.2 GitHub

私たちは、ホストされている(エンタープライズクラウド)とオンプレミス(エンタープライズサーバー)の両方で、無料のGitHub.comクラウドホスティングサービスとGitHubエンタープライズを含む、GitHubのホスティングソリューションをサポートしています。

ユーザアカウントのPATを取得するには、GitHubドキュメントの [パーソナルアクセストークンの作成](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token) 手順を参照してください。

トークンの `リポジトリ` 権限が必要です。

##### 2.4.3 GitLab

GitLab.com、GitLab Community Edition、GitLab Enterprise Editionなど、GitLab サービスのすべての階層をサポートしています。

ユーザーアカウントのPATを取得するには、GitLabドキュメントの [パーソナルアクセストークン](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) の手順を参照してください。

トークンに `write_repository` 権限が必要です。

##### 2.4.4 BitBucket

私たちは、BitBucket.org、BitBucketサーバー、BitBucketデータセンターのオンプレミスソリューションを含む、Atlassian のBitBucketサービスのすべての層をサポートしています。

BitBucket.orgでは、パーソナルアクセストークンはアプリパスワードと呼ばれます。

BitBucket.orgアカウントのアプリパスワードを設定するには、 [アプリパスワード](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/) の手順を参照してください。

一方、BitBucketサーバーとBitBucketデータセンターは、個人用アクセストークンという用語を使用しています。 個人アクセストークンを設定するには、 [個人アクセストークン](https://confluence.atlassian.com/bitbucketserver/personal-access-tokens-939515499.html) の説明を参照してください。

どちらの場合も、 `リポジトリの書き込み権限` が必要です。

##### 2.4.5 AWS コードコミット制限

Studio Pro の Git 技術プレビューでAWS CodeCommit との互換性制限があります。

## 3チームサーバー {#ts}

[Team Server](/developerportal/collaborate/team-server) は Subversion を使用して実装され、Studio Pro は HTTPS プロトコルを使用してそのサーバーと通信します。 Studio Pro内からTeam Serverにアクセスするには、所在地にあるネットワークに以下の設定が必要です。

* HTTPS ポート (TCP 443) を開く必要があります
* HTTP ポート (TCP 80) を開く必要があります
* WebDAV (HTTP プロトコル内の動詞) をプロキシサーバー上で有効にする必要があります (存在する場合)

## 4 Mendix Studio

[Mendix Studio](/studio) は Google Chrome での使用に最適化されています。 Chromeは正式にサポートされているブラウザですが、Mendix StudioをMozilla Firefox、Apple Safari、Microsoft Edgeなどの一般的なブラウザで使用することもできます。

{{% alert type="info" %}}
使用するブラウザはJavaScriptを有効にする必要があります。
{{% /alert %}}

## 5 Cloud Foundry

[Mendix Cloud Foundry buildpack](https://github.com/mendix/cf-mendix-buildpack) は Cloud Foundry バージョン v9 以上をサポートしています。

## 6 Docker

[Mendix Docker buildpack](https://github.com/mendix/docker-mendix-buildpack) は Docker バージョン 18.09.0 以降をサポートしています。

### 6.1 Kubernetes

Mendix Dockerビルドパックは以下のKubernetesバージョンをサポートしています。

* Kubernetes バージョン v1.12 以上
* Red Hat OpenShift v3.11 と v4.2 以上

## 7サーバー

### 7.1 オペレーティング システム

* Microsoft Windows Server 2008 SP2 以上
* Debian 8 (Jessie) 以上
* Red Hat Enterprise Linux 6, Red Hat Enterprise Linux 7
* CentOS 6, CentOS 7

### 7.2 ウェブサーバー

* Microsoft Internet Information Services 7 and above
* Nginx (Debian Jessie および Debian Jessie Backportsに含まれるバージョンでテスト)
* Apache

### 7.3 Java {#java}

Mendixをサーバー上で実行する場合は、Java Runtime Environment (JRE) 11が必要です。 OpenJDK のディストリビューションを AdoptOpenJDK からダウンロードするには、 [AdoptOpenJDK のインストール](https://adoptopenjdk.net/installation.html) を参照してください。 商用Oracleディストリビューションをダウンロードするには、 [Java SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html) を参照してください。

{{% alert type="info" %}}
Java 7以降では、一定量のデータでWebサービスを使用する場合にタイムアウトが発生する問題があります。 この問題は、VM params `-Djava.net.preferIPv4Stack=true` を追加することで回避できます。 Mendix Studio Proはあなたのためにこれを行います。 しかし、Windows サーバー上のオンプレミスでMendixを実行している場合は、自分で行う必要があります。 この問題の詳細については、 [HotSpot (64bitサーバー) がソケット読み込み(JVM 1.7バグ?)にハングアップします。 - Java 7](http://blog.bielu.com/2011/11/hotspot-64bit-server-hangs-on-socket.html) と [のバグを更新しました](https://forums.oracle.com/forums/thread.jspa?messageID=9985748)。
{{% /alert %}}

## 8つのデータベース {#databases}

Mendixは、データベースベンダーから最新のパッチを適用したデータベースサーバーバージョンをサポートしようとします。 ベンダーがリリースされた後、新しいベンダーバージョンのサポートを追加することを目指しています。 データベースのドロップサポートは、ベンダーがサポートをドロップした日にリリースノートで発表されます。 後で2つのマイナーMendixバージョンをサポートします。

現在のサポート:

* [IBM DB2](db2) 11.1 and 11.5 for Linux, Unix, および Windows
* [MariaDB](mysql) 10.2, 10.3, 10.4, 10.5
* [Microsoft SQL Server](/developerportal/deploy/mendix-on-windows-microsoft-sql-server) 2017, 2019
* [Azure SQL](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-2017) v12 互換モード 140 以上
* [MySQL](mysql) 8.0
* [Oracle Database](oracle) 19
* PostgreSQL 9.6, 10, 11, 12, 13
* [SAP HANA](saphana) 2.00.040.00.1545918182

{{% alert type="warning" %}}
各アプリにはそれぞれのデータベースが必要です。 Mendix アプリは同じデータベースを共有することでデータを共有することはできません。

2つのアプリで同じデータベースを共有したい場合は、APIを使用して1つのアプリから他のアプリにデータを共有する必要があります。 Mendixでは、これらは [Data Hub](/data-hub/share-data/) または、 [Studio Pro Guide](integration) の *統合* セクションで説明されている REST および OData サービスでサポートされています。 これは *マイクロサービス* アーキテクチャと呼ばれます。

アプリ間でデータを共有できない理由の詳細については、 [Data Storage](data-storage#databases) を参照してください。 あるアプリから別のアプリにデータをコピーする必要がある場合は、 [Database Replication](/appstore/modules/database-replication) モジュールを使用します。
{{% /alert %}}

## 9個のファイルストレージ {#file-storage}

### 9.1 コンテナのストレージサービス

Docker、Kubernetes、Cloud Foundryを使用したコンテナベースのデプロイメントでは、以下のストレージサービスがサポートされています。

* AWS S3
* Azure Blob Storage
* IBM Cloud Object Storage
* SAP AWS S3 Object Storage
* SAP Azure Blob ストレージ

外部ストレージクラスによって提供されるKubernetes内のコンテナマウントストレージについては、 [Kubernetes](/developerportal/deploy/run-mendix-on-kubernetes) 上でMendixを実行するを参照してください。

### 9.2 サーバーのストレージタイプ

サーバーベースのインストールでは、OS によってマウントされた次のストレージタイプがサポートされます。

* NAS
* SAN
* GFS
* ローカルストレージ

## 10 Browsers {#browsers}

* Google Chrome (最新安定版デスクトップ版とAndroid版)
* Mozilla Firefox (最新安定版デスクトップ版)
* Apple Safari (latest stable desktop version and latest version for each [supported iOS](#mobileos) version)
* Microsoft Edge (最新の安定したデスクトップ版)

{{% alert type="warning" %}}
Internet Explorer は、Studio Pro 9 ではサポートされなくなりました。 市場がInternet Explorerから離れ、Mendixは現代のWebエコシステムのベストプラクティスと整合し続けているように。 Internet Explorer 11のサポートを終了しました。 これにより、ユーザーの期待に沿うことができます。 サポートを削除すると、すでにアプリの読み込み時間とパフォーマンスが改善され、最新のWeb機能を使用して改善と革新を続けることができます。<br />
<br />
Studio Pro 9 を使用しています IE をまだ使用しているアプリのエンドユーザーは、最新のブラウザーへのアップグレードが必要であることを示す **サポートされていないブラウザー** メッセージが表示されます。 必要に応じて [このメッセージ](/howto/front-end/customize-styling-new#customize-unsupported-browsers) をカスタマイズできます。<br />
<br />
IE11 をサポートする必要がある場合は、Studio Pro [8](/releasenotes/studio-pro/8.18) と [7](/releasenotes/studio-pro/7.23) は IE11 のサポートを継続することに注意してください。 Mendixは、アプリのエンドユーザーがブラウザをアップグレードするまで、Studio Pro 8または7を使用することを推奨しています。
{{% /alert %}}

## 11 モバイルOS {#mobileos}

Mendixネイティブアプリ、ハイブリッドアプリ、およびMendix Mobileアプリでは、以下のオペレーティングシステムがサポートされています。

* iOSの最新2つのメジャーバージョン
* Android 5.0 以上

### 11.1 ハイブリッドアプリプレビュー

ハイブリッドプレビュー機能を使用することは、電話またはシミュレータでアプリをテストすることとは異なります。 ハイブリッド・プレビューでは、そのアプリがモバイルデバイスでどのように見えるかを示すために、アプリのリサイズビューのみが表示されます。 このブラウザビューでは、ハイブリッドアプリの一部の機能はサポートされません。 完全なテストは、常にデバイスまたはエミュレータで行う必要があります。 オフラインアプリはGoogle Chromeでのみプレビューできます。

ハイブリッドアプリは、実際のデバイス上でのみ、Android エミュレータでテストすることはできません。

## 12 MxBuild {#mxbuild}

MxBuild は、Mendix Deployment Package のビルドに使用できる Windows および Linux のコマンドラインツールです。 詳細については、 [MxBuild](mxbuild) を参照してください。

* Mono v5.20.x または .NET v4.7.2
* JDK 11

## 13 mx コマンドラインツール {#mxtool}

**mx** コマンドラインツールは、WindowsおよびLinuxのコマンドラインツールで、Mendixアプリで役に立つことを行うことができます。 詳細については、 [mx コマンドラインツール](mx-command-line-tool) を参照してください。

* Mono v5.20.x または .NET v4.7.2
