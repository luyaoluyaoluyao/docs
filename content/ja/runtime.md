---
title: "Mendix Runtime"
tags:
  - "ランタイム:"
  - "ランタイムサーバー"
  - "mendixクライアント"
  - "クラスターリーダー"
---

## 1つの紹介

Mendix Runtimeは、実質的にMendixモデルを実行し、ユーザーにページを提供するインタプリタです。

Mendixの各パッチバージョンには、Mendixのバージョンで利用可能な機能を実装したランタイムの独自のバージョンが付属しています。 たとえば、Mendix 8.4.1 と 8.4.2 のランタイムは異なり、そのバージョン用にビルドされた Mendix アプリのみを実行できます。

## 2ランタイムの概要

Mendix ランタイムは、 [Runtime Server](runtime-server) と [Mendix Client](mendix-client) の2つの部分で構成されています。 両者の関係は下図に示されています。

Runtime Serverはクラウドプラットフォーム上で起動され、マイクロフローを実行し、ファイル、リレーショナルデータベース、およびその他の必要なサービスに接続します。 Mendixクライアントから連絡を受けるのを待ちます。 Runtime Server については、 [Runtime Server](runtime-server) の詳細を参照してください。

Mendix クライアントはエンドユーザーによって開始されます。 これは、Webブラウザまたは他のサポートされているデバイス内にすることができます。 オンラインモードの場合は、認証を必要としない場合がありますが、Runtime Serverでセッションを開始します。 Runtime Serverは、Mendixクライアントがリクエストできるように、データベース内のセッションの詳細を記録します。 Mendix Client は、 [Mendix Client](mendix-client) で詳細に説明されています。

エンドユーザーはMendixクライアントとやりとりし、次にRuntime Serverにデータを処理したり、サーバー側の機能(例えばマイクロフロー)を実行したりするように要求を行います。 リクエストが終わると、すべての状態 (コミットされていないデータを含む) が Mendix クライアントに戻されます。 この通信がどのように行われるかの詳細については、Mendix Runtime [のコミュニケーションパターン](communication-patterns) を参照してください。

Runtime ServerからMendixクライアントに状態を渡すと、Runtime Serverはステートレスになります。 これは、Runtime ServerインスタンスがMendixクライアントからのリクエストに応答できることを意味します。 ロードバランサがリクエストに応答するランタイムサーバーインスタンスを決定します。 エンドユーザーセッションが終了すると、Runtime Serverはそのセッションへの参照を削除します。

1つのアプリに複数のインスタンスがある場合、1つのインスタンスは *クラスタリーダー* になります。 そのインスタンス内のRuntime Serverは、簡単に配布できない多くのアクティビティに対して責任を負います。 これらには以下が含まれます:

* セッションのクリーンアップ処理
* クラスターノードの有効期限の処理
* バックグラウンドジョブの有効期限の処理
* ブロックを解除したユーザー
* スケジュールされたイベントの実行
* データベース同期タスクの実行
* 新しいデプロイ後に永続的なセッションをクリアする

複数のインスタンスに関する詳細は、 [Clustered Mendix Runtime](clustered-mendix-runtime) にあります。

![Mendix ランタイムの概要](attachments/runtime/runtime-overview.png)

チャートの各構成要素は以下の通りです。

### 2.1 外部サービス

外部サービスは、Mendixアプリの外部からデータやその他の機能を提供します。 これらはSAPのような外部データソース、Googleマップのような外部表示ウィジェット、またはIBMワトソンの機械学習のような外部データ処理である可能性があります。 Runtime Server はこれらの HTTP(S) 接続経由で通信します。

### 2.2 インフラストラクチャ

これは、Mendixアプリが展開されるハードウェアです。 通常、サービスとしてInfrastructure as a Service(IaaS)として提供され、パブリックまたはプライベートクラウドで仮想マシンを提供します。 しかし、インフラストラクチャは、オンプレミスで動作する物理的なマシンでもかまいません。 インフラストラクチャの例としては、Amazon Web Services (AWS)、Microsoft Azure、Windows Server マシンなどがあります。

### 2.3 ファイル

これは、アプリで使用されるデータの一部であるファイルが格納される場所です。 特に画像を含む *FileDocument* オブジェクトの値が含まれています。 サイズやパフォーマンスの制限を避けるためにデータベース外に保存されるバイナリオブジェクトです

### 2.4 リレーショナルデータベース

これは、アプリケーション内のドメインモデルで定義されているオブジェクトを保持するデータベース(または共有データベースのスキーマ)です。

### 2.5 プラットフォーム

これは、Mendixアプリが実行されているオペレーティングシステムと、追加のサービスです。 例えばアプリと紐づけられているデータベースなどです

### 2.6 インスタンス

**App Container** とも呼ばれる。 これはランタイムサーバーを起動して公開します。 唯一の例があるかもしれませんが、高可用性とパフォーマンスを向上させるには、多くのインスタンスが存在する可能性があります。

### 2.7 ランタイムサーバー

これが Mendix ランタイムのサーバー側です。 これは、 [Runtime Server](runtime-server) で説明されています。

### 2.8 ロードバランサー

ロードバランサはMendixクライアントからの受信リクエストを受け取り、Runtime Serverインスタンスに転送します。 これは、要求が異なるインスタンスに均等に分散されることを確認することによって負荷をバランスさせます。 Mendix Client は、HTTPS を使用してロードバランサーと通信します。 ロードバランサのサーバ側、環境インスタンス、CDNへの通信はHTTPを使用して行われます。

### 2.9 CDN 静的設定

CDN (Content Delivery Network)には、クライアントが必要とする静的構成情報が含まれています。 これらには、Mendix クライアントをブラウザから起動するために必要なファイルが含まれます。 アプリのテーマを定義するカスケーディングスタイルシート (css ファイル) とクライアント側のロジックを定義する JavaScript ファイル。

### 2.10 Mendix Client

これは、エンドユーザーがアプリとやり取りできるようにするブラウザまたはデバイスです。 これは、ChromeなどのWebブラウザ、またはiPhoneなどのモバイルデバイスである可能性があります。 通常、エンドユーザーがアプリを使用できるように、画面、ポインタデバイス、および入力デバイスを備えています。 Mendix Client は [Mendix Client](mendix-client) で説明されています。

## 3 ライセンス

本番モードでアプリケーションを実行するにはライセンスが必要です。 ライセンスがなければ、Runtime Serverは数時間後にスリープ状態になります。 Mendix アプリのライセンスに関する情報は、 [Licensing Apps](/developerportal/deploy/licensing-apps-outside-mxcloud) にあります。

## 4 API

Javaアクションを書くことで、Runtime Serverの機能を拡張できます。 詳細については、 [API ドキュメント](/apidocs-mxsdk/apidocs/#runtime) の *Runtime API* セクションを参照してください。

{{% alert type="info" %}}
公開された Web サービスの WSDL のような API ドキュメントへのリンクは、URL パス `/api-doc` で利用できます (例: `http://localhost:8080/api-doc/`)。
{{% /alert %}}

## このカテゴリ内の5つのメインドキュメント

* [Runtime Server](runtime-server) – Runtime Server の仕組みを説明する
* [Mendix Client](mendix-client) – Mendix Client の動作を説明
* [ランタイムデプロイ](runtime-deployment) - Mendix ランタイムがクラウドにどのようにデプロイされるかを説明します
* [クラスター付きMendix Runtime](clustered-mendix-runtime) – クラスターとしてのMendix Runtimeの動作と影響を説明する
* [Runtime Customization](custom-settings) - Runtime Serverの設定をカスタマイズするための高度なオプションを提示する
* [Data Storage](data-storage) - 以下のようなデータストレージ設定オプションに関する情報を表示します:
* [Date & Time Handling](datetime-handling-faq) - ユーザーの日付と時刻にRuntime Server操作を構成する方法の詳細を提示する
* [ログ](logging) – ランタイムの様々なログレベルについて説明します。
* [Monitoring Mendix Runtime](monitoring-mendix-runtime) – サポートされているMendix Runtime Monitoring actions ( [state statistics](monitoring-mendix-runtime#state) や [thread stack trace](monitoring-mendix-runtime#thread) など) を説明します。
* [オブジェクト & キャッシュ](objects-and-caching) - オブジェクトがデータベースから読み込まれたときに何が起こるかの詳細を提示します。
* [Mendix Runtime & Java](runtime-java) - Mendix の Java の基本概念のいくつかを説明する
* [Mendix Runtime の通信パターン](communication-patterns) - Mendix Runtime で使用される通信パターンの概要を示す。
