---
title: "システム要件"
category: "一般情報"
menu_order: 10
description: "Mendix プラットフォームを使用するためのシステム要件を提示します。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/system-requirements.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、Mendix プラットフォームのさまざまな部品に対するシステム要件を示します。

## 2 Mendix Studio Pro {#sp}

Mendix [Studio Pro](modeling) は Windows 7、8、10 の 64 ビットバージョンをサポートしています。 Windows 7は少なくともサービスパック1でなければなりません。

次のフレームワークが自動的にインストールされます(必要な場合):

* Microsoft .NET Framework 4.7.2 および該当するすべての Windows セキュリティパッチ
* Microsoft Visual C++ 2010 SP1 再頒布可能パッケージ
* Microsoft Visual C++ 2015 再配布可能パッケージ
* AdoptOpenJDK 11またはOracle JDK 11(前者は

Mendix 8の時点で自動的にインストールされます。 .0 [](/releasenotes/studio-pro/8.0#800) JDK 11がインストールされていない場合)</li> </ul> 
  
  {{% alert type="info" %}}
  
  Studio Proの **Edit** > **Preferences** メニュー項目からローカルでのビルドと実行に使用するJDKを選択できます。 
  
  {{% /alert %}}
  
  {{% alert type="warning" %}}
  
  Studio Proに組み込まれたデータベースビューアは( [開発データベースの共有方法](/howto8/collaboration-requirements-management/sharing-the-development-database)で説明されているように)JDK 11では動作しないことに注意してください。 6または11.07。 
  
  {{% /alert %}}
  
  

### 2.1 ファイアウォールの設定

Studio Pro は以下の URL にアクセスする必要があります。 ファイアウォールが現在これらをブロックしている場合は、ホワイトリストに登録する必要があります。

* `*.mendix.com`
* `*.mendixcloud.com`
* `*.teamserver.sprintr.com`



### 2.2 TortoiseSVN

Studio Pro と組み合わせて TortoiseSVN を使用したい場合は、 [TortoiseSVN](https://tortoisesvn.net/) のウェブサイトから最新バージョンをダウンロードしてください。

{{% alert type="warning" %}}

Mendix Studio Pro は Subversion 1.9 の作業コピーを使用します。 Mendix Desktop Modelerの以前のバージョンでは、Subversion 1.7 の作業コピーが使用されていました。 これらの作業コピーのバージョン **は互換性がありません**。

常にアプリモデルと一致する TortoiseSVN のバージョンを使用してください。 Mendixバージョン7.xまたは6からローカルモデルを開く場合。 最新バージョンの TortoiseSVN **では、Mendix** では開くことができなくなります。 

{{% /alert %}}



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
* Redhat Openshift v3.11 と v4.2 以上



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



### 7.3 Java

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

それぞれのアプリには独自のデータベースが必要です。 Mendix アプリは同じデータベースを共有することでデータを共有することはできません。 

{{% /alert %}}



## 9個のファイルストレージ



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
* Microsoft Internet Explorer 11



## 11 ハイブリッドプレビュー

ハイブリッド・プレビューの使用はエミュレータの使用と同じではありません。 ハイブリッド・プレビューでは、そのアプリがモバイルデバイスでどのように見えるかを示すために、アプリのリサイズビューのみが表示されます。 このブラウザビューでは、ハイブリッドアプリの一部の機能はサポートされません。 完全なテストは、常にデバイスまたはエミュレータで行う必要があります。 オフラインアプリはGoogle Chromeでのみプレビューできます。



## 12 モバイルOS {#mobileos}

Mendix アプリと [Mendix Mobile app](getting-the-mendix-app) の場合 :

* iOS 12 以上
* Android 5.0 以上



## 13 MxBuild {#mxbuild}

MxBuild は、Mendix Deployment Package のビルドに使用できる Windows および Linux のコマンドラインツールです。 詳細については、 [MxBuild](mxbuild) を参照してください。

* Mono v5.20.x または .NET v4.7.2
* JDK 11



## 14 mx コマンドラインツール {#mxtool}

**mx** コマンドラインツールは、WindowsおよびLinuxのコマンドラインツールで、Mendixアプリで役に立つことを行うことができます。 詳細については、 [mx コマンドラインツール](mx-command-line-tool) を参照してください。

* Mono v5.20.x または .NET v4.7.2
