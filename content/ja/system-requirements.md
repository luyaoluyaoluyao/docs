---
title: "システム要件"
category: "全般"
menu_order: 10
description: "Mendix プラットフォームを使用するためのシステム要件を提示します。"
---

## 1つの紹介

このドキュメントでは、Mendix プラットフォームのさまざまな部品に対するシステム要件を示します。

## 2デスクトップモデラー

Mendix [Desktop Modeler](desktop-modeler) は Windows 7、8、10 に対応しています。 32ビットと64ビットの両方のバリエーションをサポートしていますが、64ビットが推奨されます。

次のフレームワークが自動的にインストールされます(必要な場合):

* Microsoft .NET Framework 4.6.2
* Microsoft Visual C++ 2010 SP1 再頒布可能パッケージ
* Microsoft Visual C++ 2015 Redistributable Package (for [Mendix 7.23.17](/releasenotes/studio-pro/7.23#72317) and above) or Microsoft Visual C++ 2013 Redistributable Package (for [Mendix 7.23.16](/releasenotes/studio-pro/7.23#72316) and below)
* AdoptOpenJDK 8 (installed automatically as of [Mendix 7.23.3](/releasenotes/studio-pro/7.23#7233) if you do not have this or Java Development Kit 1.8 already installed) or Java Development Kit 1.8

{{% alert type="warning" %}}
Desktop Modelerの **Edit** > **Preferences** メニュー項目からローカルでのビルドと実行に使用する JDK を選択できます。
{{% /alert %}}

TortoiseSVN を Desktop Modelerと組み合わせて使用したい場合は、 [Sourceforge](http://sourceforge.net/projects/tortoisesvn/files/?source=navbar) から最新バージョン1.7.xをダウンロードしてください。

## 3チームサーバー

[Team Server](team-server) は Subversion を使用して実装され、モデラーは HTTPS プロトコルを使用してそのサーバーと通信します。 Desktop Modeler内からTeam Serverにアクセスするには、所在地にあるネットワークに以下の設定が必要です。

* HTTPS ポート (TCP 443) を開く必要があります
* HTTP ポート (TCP 80) を開く必要があります
* WebDAV (HTTP プロトコル内の動詞) をプロキシサーバー上で有効にする必要があります (存在する場合)

## 4 Web Modeler

[Mendix Web Modeler](/studio) は Google Chrome での使用に最適化されています。 Chromeは正式にサポートされているブラウザですが、 Web Modelerは、Mozilla Firefox、Apple Safari、Microsoft Edgeなどの一般的なブラウザでも使用できます。

{{% alert type="info" %}}
使用するブラウザはJavaScriptを有効にする必要があります。
{{% /alert %}}

## 5サーバー

### 5.1 オペレーティング システム

* Microsoft Windows Server 2008 SP2 以上
* Debian 8 (Jessie) 以上
* Red Hat Enterprise Linux 6, Red Hat Enterprise Linux 7
* CentOS 6, CentOS 7

### 5.2 ウェブサーバー

* Microsoft Internet Information Services 7 and above
* Nginx (Debian Jessie および Debian Jessie Backportsに含まれるバージョンでテスト)
* Apache

### 5.3 データベースサーバー

* [IBM DB2](db2) 11.1, Linux, Unix, Windows 用 11.5
* [MariaDB](mysql) 10.2, 10.3, 10.4, 10.5
* [Microsoft SQL Server](/developerportal/deploy/mendix-on-windows-microsoft-sql-server) 2017, 2019
* Azure SQL v12 (サポートは独立して検証されておらず、互換バージョンの SQL Server でのみ使用できます)
* [MySQL](mysql) 5.7, 8.0
* [Oracle Database](oracle) 12c Release 2, 19
* PostgreSQL 9.6, 10, 11, 12, 13
* [SAP HANA](saphana) 2.00.040.00.1545918182

### 5.4 Java

Mendixをサーバー上で実行する場合は、Java Runtime Environment (JRE) 8が必要です。 OpenJDK のディストリビューションを AdoptOpenJDK からダウンロードするには、 [AdoptOpenJDK のインストール](https://adoptopenjdk.net/installation.html) を参照してください。 商用Oracleディストリビューションをダウンロードするには、 [Java SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html) を参照してください。

{{% alert type="info" %}}
Java 7以降では、一定量のデータでWebサービスを使用する場合にタイムアウトが発生する問題があります。 この問題は、VM params `-Djava.net.preferIPv4Stack=true` を追加することで回避できます。 Mendixデスクトップモデラーがこれを行います。 しかし、Windows サーバー上のオンプレミスでMendixを実行している場合は、自分で行う必要があります。 この問題の詳細については、 [HotSpot (64bitサーバー) がソケット読み込み(JVM 1.7バグ?)にハングアップします。 - Java 7](http://blog.bielu.com/2011/11/hotspot-64bit-server-hangs-on-socket.html) と [のバグを更新しました](https://forums.oracle.com/forums/thread.jspa?messageID=9985748)。
{{% /alert %}}

### 5.5 アプリケーション サーバー

Jetty は [Mendix Runtime](runtime)に組み込まれているため、アプリケーションサーバは必要ありません。

## 6 Browsers

### 6.1 デスクトップブラウザ

* Google Chrome
* Mozilla Firefox
* Apple Safari
* Microsoft Edge
* Microsoft Internet Explorer 11

### 6.2 モバイルブラウザ

* iOS 9以上(Safari)
* Android 5.0 以上
* Windows Phone 8 以上

### 6.3 ハイブリッドプレビュー

ハイブリッド・プレビューの使用はエミュレータの使用と同じではありません。 ハイブリッド・プレビューでは、そのアプリがモバイルデバイスでどのように見えるかを示すために、アプリのリサイズビューのみが表示されます。 このブラウザビューでは、ハイブリッドアプリの一部の機能はサポートされません。 完全なテストは、常にデバイスまたはエミュレータで行う必要があります。 オフラインアプリはGoogle Chromeでのみプレビューできます。

## 7つのモバイルOS

Mendix アプリと [Mendix Mobile app](getting-the-mendix-app) の場合 :

* iOS 9 以上
* Android 5.0 以上

## 8 MxBuild{#mxbuild}

MxBuild は、Mendix Deployment Package のビルドに使用できる Windows および Linux のコマンドラインツールです。 詳細は [MxBuild](mxbuild) を参照してください。

### 8.1 Mendix バージョン 7.1 & 以上

* Mono v4.6.x または .NET v4.6.2
* JDK 8.

### 8.2 Mendix バージョン 7.0.2

* Mono v3.1.0 または .NET v4.5
* JDK 8
