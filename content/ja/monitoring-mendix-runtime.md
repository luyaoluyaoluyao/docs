---
title: "Mendix ランタイムの監視"
category: "Mendix Runtime"
description: "サポートされているMendixランタイム監視アクションの説明。"
tags:
  - "ランタイム:"
  - "json"
  - "studio pro"
  - "オンプレミス版"
  - "ローカル"
---

## 1つの紹介

オンプレミスとMendixのローカルデプロイの場合、Mendix Runtime監視アクションは、JSONリクエストを管理者ハンドラに送信することで呼び出すことができます。 これは、アプリケーション構成で指定されたアドミンポートにリクエストを送信することによって行われます (デフォルトのポートは 8090 です)。

{{% alert type="info" %}}
これは、アプリケーションのローカルおよびオンプレミス展開でのみ使用できます。

Mendix Cloud へのデプロイでは、m2ee管理者ハンドラにアクセスすることはできません。 ただし、開発者ポータルのさまざまなページから同じ情報を得ることができます。 詳細については以下をご覧ください。

* [メトリック](/developerportal/operate/metrics)
* [Mendix Cloud v4のトレンド](/developerportal/operate/trends-v4)
* [現在のメトリクスを実行しています](/developerportal/operate/troubleshooting-mxcloud-runningnow)
{{% /alert %}}

You can change the admin port from Studio Pro by navigating to **Project** > **Settings** > **Configurations** > *your configuration* > **Server** > **Admin port**.

リクエストは **POST** 型の **No Authorization** および以下のヘッダである必要があります:

* Content-Type: **application/json**
* X-M2EE認証: **yourM2EEPassword_Base64Encoded**

M2EE パスワードは、スーパー管理者パスワードではなく、別のパスワードです。 If you have the application deployed *on premises*, you can set this password in the **settings.yaml** file, which is located in the **Apps/YourProject** folder. If you are *running the application from Studio Pro*, the M2EE password is set automatically by Mendix, and you can retrieve it from the environment variables of your application process.

次のセクションでは、どの監視アクションがサポートされているかについて説明します。

## 2 現在の実行

### 2.1 リクエスト

```json
"{"action" : "get_current_runtime_requests", "params":{} })
```

### 2.2 応答例

```json
{
  "feedback":{
    "202de1e51639ae0":{
      "request_duration":106175,
      "type":"CLIENT",
      "user":"Anonymous_2ce7c971-f077-4aca-83c5-f3898443ed01",
      "action_stack":[
      {
        "xpath":"//MyFirstModule.Entity",
        "amount":1,
        "depth":0,
        "offset":-1,
        "sort":{},
        "type":"RetrieveXPathAction"
      },
      {
        "current_activity":{
          "caption":"Retrieve Entity from database",
          "type":"RetrieveByXPath"
        },
        "name":"MyFirstModule.LoopNested",
        "type":"Microflow"
      },
      {
        "current_activity":{
          "caption":"LoopNested",
          "type":"SubMicroflow"
        },
        "name":"MyFirstModule.Loop",
        "type":"Microflow"
      }
    ]},
    "bcbb5508-0293-4f12-b290-ee109962811e":{
      "request_duration":104776,
      "type":"CLIENT_ASYNC_MONITORED",
      "user":"Anonymous_2ce7c971-f077-4aca-83c5-f3898443ed01",
      "action_stack":[
      {
        "current_activity":{
          "caption":"Retrieve Entity from database",
          "type":"RetrieveByXPath"
        },
        "name":"MyFirstModule.LoopNested",
        "type":"Microflow"
      },
      {
        "current_activity":{
          "caption":"LoopNested",
          "type":"SubMicroflow"
        },
        "name":"MyFirstModule.Loop",
        "type":"Microflow"
      }
    ]}
  },
  "result":0
}
```

### 2.3 戻り値

このリクエストは、Mendix Runtime によって知られているアクションの現在の実行を返します。 アクションには、マイクロフロー、Javaアクション、Webサービス・コール、スケジュールされたイベントを含めることができます。 実行ごとに以下が報告されます:

*   ミリ秒単位の実行の「継続時間」
*   実行の"タイプ"。 使用可能なタイプは次のとおりです。
  * "CLIENT"
  * "CLIENT_ASYNC" – ウェブクライアントからトリガーされた非同期マイクロフロー呼び出し。
  * "CLIENT_ASYNC_MONITORED" – CLIENT_ASYNC とは異なるスレッドで発生する Mendix ランタイムにおける非同期マイクロフローの実際の実行
  * "CUSTOM"
  * "WEB_SERVICE"
  * "SCHEDULED_EVENT"
  * "不明"
*   アクションを実行しているセッションに関連付けられた「ユーザー」。非ユーザーセッションでは「システム」という名前が返されます。
*   この実行のための"action_stack"は、このスタック内の各アクションの詳細情報が表示されます。 例えば現在の活動とマイクロフローの名前は

## 3ランタイム統計

### 3.1 リクエスト

```json
"{"action" : "runtime_statistics", "params":{} }"
```

### 3.2 応答例

```json
{
  "feedback":
  {
    "requests":
    [
      {"name":"","value":97,"last_request_timestamp":1394785085325},
      {"name":"file","value":0,"last_request_timestamp":1394785072325},
      {"name":"ws-doc/","value":0,"last_request_timestamp":1394785072325},
      {"name":"xas/","value":8,"last_request_timestamp":1394785082325},
      {"name":"ws/","value":0,"last_request_timestamp":1394785072325}
    ],
    "cache": { "total_count":2 },
    "sessions":
    {
      "user_sessions":{
        "562949953421313":[
          "Mozilla/5.0 (Windows NT 6.3; WOW64; rv:39.0) Gecko/20100101 Firefox/39.0"
        ]
      },
      "named_users":3,
      "named_user_sessions":1,
      "anonymous_sessions":0
    },
    "connectionbus":
    {
      "update":7,
      "transaction":0,
      "select":28,
      "delete":5,
      "insert":5
    },
    "memory":
    {
      "code":0,
      "init_nonheap":2555904,
      "init_heap":268435456,
      "eden":0,
      "memorypools":[
        {
          "is_heap":false,
          "usage":11788032,
          "name":"Code Cache",
          "index":0
        },
        {
          "is_heap":false,
          "usage":49590256,
          "name":"Metaspace",
          "index":1
        },
        {
          "is_heap":false,
          "usage":6458552,
          "name":"Compressed Class Space",
          "index":2
        },
        {
          "is_heap":true,
          "usage":106799624,
          "name":"PS Eden Space",
          "index":3
        },
        {
          "is_heap":true,
          "usage":0,
          "name":"PS Survivor Space",
          "index":4
        },
        {
          "is_heap":true,
          "usage":18500976,
          "name":"PS Old Gen",
          "index":5
        }
      ],
      "committed_heap":301465600,
      "max_heap":3817865216,
      "used_nonheap":67844048,
      "max_nonheap":-1,
      "committed_nonheap":72777728,
      "used_heap":125300600
  },
  "result":0
}
```

### 3.3 戻り値

#### 3.3.1 リクエスト{#request-handlers}

ハンドラごとのリクエストに関する情報を表示します:

* 空のハンドラはリソースリクエストハンドラを表し、画像やフォームなどを処理します。 (静的コンテンツハンドリングにリバースプロキシが使用されない場合にのみ使用されます)。
* "file" はファイルのアップロードとダウンロードを処理します
* "xas/"は、Webクライアントによって発行されたCRUDアクションとマイクロフロー実行呼び出しを処理します
* "ws/" と "ws-doc/" は Web サービスのリクエストを処理し、Web サービスのドキュメントを提供します

各ハンドラーには、2つの情報が表示されます。

* value フィールドには、ハンドラあたりのリクエスト数が表示されます。
* last_request_timestamp 項目には、最後に処理されたリクエストのミリ秒単位のタイムスタンプが表示されます。 処理されたリクエストがない場合、この項目はハンドラが登録された瞬間を示します。

#### 3.3.2 キャッシュ

ランタイム状態 (すべてのセッションをまとめて) に現在参加しているオブジェクトの合計数を表示します。 ランタイム状態は、メモリ(非クラスターランタイム)またはRedisまたはデータベース(クラスターランタイム)のいずれかに存在します。 状態にあるオブジェクトが多すぎると、Mendix Runtime のパフォーマンスが低下する可能性があります。

#### 3.3.3 セッション

「user_sessions」セクションには、ユーザーエージェントとの現在のユーザーセッションが表示されます。

他のセクションには、カテゴリごとのセッション数が表示されます。 カテゴリ:

* "名前付きユーザー" (ユーザーインスタンスの数)
* "named_user_sessions" (匿名でない同時セッションの数)
* "anonymous_sessions" (匿名同時セッション数)

#### 3.3.4 接続バス

データベースリクエストの数 「select」、「update」、「insert」、「delete」コマンドとデータベーストランザクションを開始したコマンドを区別します。

#### 3.3.5 メモリ

{{% alert type="warning" %}}

メモリ統計量は専門家によってのみ解釈されるべきであり、Javaメモリモデルの詳細な知識の欠如は誤った結論につながる可能性があります。

{{% /alert %}}

指定されたメモリセクションに割り当てられたバイト数を表します。 一般的な説明については、ガベージコレクションのチューニングに関する [Oracleドキュメント](http://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/) を参照してください。 ヒープフィールドと非ヒープフィールドについては、 [メモリ使用量](https://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryUsage.html) ページを参照してください。

"memorypools" セクションには、 [MemoryPoolMxBean](http://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryPoolMXBean.html) のいくつかのフィールドを持つ JVM から受け取るのと同じように、すべてのメモリプールの順序付きリストが含まれています。

*   "usage" – このメモリプールのメモリ使用量の推定値を返します (バイト単位)
*   "is_heap" – このメモリプールはヒープの一部ですか?
*   "name" – JVM によって受信されるメモリープールの説明。 これらの名前は、JDK、メモリマネージャ、ガベージコレクションオプションなどによって異なる場合があります。
*   "index" – JSON Array内のインデックス。 プールがリストに返されるため、このフィールドは必須ではありません。 プログラムで処理している場合に備えてリストの順番に頼るべきです

{{% alert type="info" %}}

"memorypools" セクションを自動的に処理している場合、例えばグラフに表示します。 理想的には、ガベージコレクタの設定や Java バージョンなどによって、リスト内の順序や名前に基づいてメモリープールの種類を想定しないでください。

Javaバージョンに基づいて、いずれにせよこれらのプールを解釈する戦略を開発したい場合: 「about」管理アクションからJavaバージョンを取得できます。

{{% /alert %}}

## 4要塞統計 {#state}

### 4.1 リクエスト

```json
"{"action" : "cache_statistics", "params":{} }"
```

### 4.2 応答例

```json
{
  "feedback":{
    "totals":{
      "Expenses.TempUser":1,
      "System.Session":1
    },
    "user_totals":[
      {
        "user_name":"MxAdmin",
        "total_count":2,
        "amounts_per_type":{
          "Expenses.TempUser":1,
          "System.Session":1
         }
      }
    ]
  },
  "result":0
}
```

### 4.3 戻り値

この監視アクションは、Mendix Runtime の状態にあるオブジェクトに関する詳細な情報を提供します。

* 「合計」は、セッションごとのオブジェクトの合計数を表示します
* "user_totals" は、特定のセッションのエンティティごとのオブジェクト数を表示します

この情報は、どのオブジェクトが多くのメモリ使用量を引き起こすかを把握するのに役立ちます。

## 5つのサーバー統計

### 5.1 リクエスト

```json
"{"action" : "server_statistics", "params":{} }"
```

### 5.2 応答例

```json
{
  "feedback":{
    "jetty":{
      "current_connections":0,
      "max_connections":0,
      "max_idle_time_s":200
    },
    "threadpool": {
      "idle_threads":3,
      "max_threads":254,
      "threads_priority":5,
      "threads":8,
      "max_queued":-1,
      "min_threads":8,
      "max_idle_time_s":60,
      "max_stop_time_s":0
    }
  },
  "result":0
}
```

### 5.3 戻り値

サーバー統計モニタのアクションは、埋め込まれた Jetty Web サーバーに関する情報を提供します。 「jetty」セクションには、現在開いている接続の数と開いている接続の最大数が表示されます。 さらに、Jetty が通常の状況下で動作している場合は、閉鎖前の接続のアイドル時間の最大値がリストされます。

"threadpool" セクションは、ランタイムポートを通過するすべてのリクエストを処理するハンドラの threadpool に関する情報を提供します。 詳細は [Jetty QueuedThreadPool ドキュメント](https://www.eclipse.org/jetty/javadoc/9.4.11.v20180605/org/eclipse/jetty/util/thread/QueuedThreadPool.html) を参照してください。

## 6人のログインユーザー

### 6.1 リクエスト

```json
"{"action" : "get_logged_in_user_names", "params":{} }"
```

### 6.2 応答例

```json
{
  "feedback": {
    "count":1,
    "users":["MxAdmin"]
  },
  "result":0
}
```

### 6.3 戻り値

現在ログインしているユーザーを表示します。 ユーザに複数のセッションがある場合、このユーザは各セッションに一度表示されます。

## スレッドスタックトレース {#thread}

### 7.1 リクエスト

```json
"{"action" : "get_all_thread_stack_traces", "params":{} }"
```

### 7.2 応答例

```json
{
  "feedback": {
    "qtp1967003817-95":[
      "sun.misc.Unsafe.park(Native Method)",
      "java.util.concurrent.locks.LockSupport.parkNanos(LockSupport.java:215)",
      "java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject.awaitNanos(AbstractQueuedSynchronizer.java:2078)",
      "java.util.concurrent.LinkedBlockingQueue.poll(LinkedBlockingQueue.java:467)",
      "com.mendix.modules.microflowengine.debugger.internal.EventPusher.handleRequest(EventPusher.scala:18)",
      "com.mendix.modules.microflowengine.debugger.internal.DebuggerHandler.processJsonRequest(DebuggerHandler.scala:124)",
      "com.mendix.modules.microflowengine.debugger.internal.DebuggerHandler.processRequest(DebuggerHandler.scala:50)",
      "com.mendix.externalinterface.connector.MxRuntimeConnector$1.execute(MxRuntimeConnector.java:69)",
      "com.mendix.externalinterface.connector.MxRuntimeConnector$1.execute(MxRuntimeConnector.java:66)",
      "com.mendix.util.classloading.Runner.doRunUsingClassLoaderOf(Runner.java:32)",
      "com.mendix.externalinterface.connector.MxRuntimeConnector.processRequest(MxRuntimeConnector.java:72)",
      "com.mendix.core.impl.MxRuntimeImpl.processRequest(MxRuntimeImpl.java:715)",
      "com.mendix.m2ee.appcontainer.server.handler.RuntimeHandler.handle(RuntimeHandler.java:41)",
      "org.eclipse.jetty.server.handler.HandlerList.handle(HandlerList.java:52)",
      "org.eclipse.jetty.server.handler.HandlerWrapper.handle(HandlerWrapper.java:116)",
      "org.eclipse.jetty.server.Server.handle(Server.java:368)",
      "org.eclipse.jetty.server.AbstractHttpConnection.handleRequest(AbstractHttpConnection.java:489)",
      "org.eclipse.jetty.server.AbstractHttpConnection.headerComplete(AbstractHttpConnection.java:942)",
      "org.eclipse.jetty.server.AbstractHttpConnection$RequestHandler.headerComplete(AbstractHttpConnection.java:1004)",
      "org.eclipse.jetty.http.HttpParser.parseNext(HttpParser.java:647)",
      "org.eclipse.jetty.http.HttpParser.parseAvailable(HttpParser.java:235)",
      "org.eclipse.jetty.server.AsyncHttpConnection.handle(AsyncHttpConnection.java:82)",
      "org.eclipse.jetty.io.nio.SelectChannelEndPoint.handle(SelectChannelEndPoint.java:628)",
      "org.eclipse.jetty.io.nio.SelectChannelEndPoint$1.run(SelectChannelEndPoint.java:52)",
      "org.eclipse.jetty.util.thread.QueuedThreadPool.runJob(QueuedThreadPool.java:608)",
      "org.eclipse.jetty.util.thread.QueuedThreadPool$3.run(QueuedThreadPool.java:543)",
      "java.lang.Thread.run(Thread.java:745)"
    ],
    "pool-1-thread-10":[
      "sun.misc.Unsafe.park(Native Method)",
      "java.util.concurrent.locks.LockSupport.park(LockSupport.java:175)",
      "java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject.await(AbstractQueuedSynchronizer.java:2039)",
      "java.util.concurrent.ScheduledThreadPoolExecutor$DelayedWorkQueue.take(ScheduledThreadPoolExecutor.java:1088)",
      "java.util.concurrent.ScheduledThreadPoolExecutor$DelayedWorkQueue.take(ScheduledThreadPoolExecutor.java:809)",
      "java.util.concurrent.ThreadPoolExecutor.getTask(ThreadPoolExecutor.java:1067)",
      "java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1127)",
      "java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)",
      "java.lang.Thread.run(Thread.java:745)"
    ],
  },
  "result":0
}
```

### 7.3 戻り値

現在のスレッドスタックトレースをすべて名前で返します。 これは、アプリケーションで起こっていることを低レベルで分析する場合に便利です。 "get_current_runtime_executions" リクエストを使用して、より高いレベルの情報(マイクロフローやその他のアクション)を取得します。

## 8回のランタイムステータス {#runtime-status}

### 8.1 リクエスト

```json
"{"action" : "runtime_status", "params":{} }"
```

### 8.2 応答例

```json
{
  "feedback":{
    "status":"running"
  },
  "result":0
}
```

### 8.3 戻り値

現在の Mendix ランタイムステータスを返します。 利用可能なステータス値は次のとおりです。

* "created"
* "starting"
* "壊れた"
* "実行中"
* "停止"
* "停止"

この情報は、コマンドを開始または停止するときにMendix Runtimeがどの状態にあるかを追跡するために使用することができます。 またはランタイムがまだ実行されているかどうかを確認します。

## 体力を9点確認 {#check-health}

### 9.1 リクエスト

```json
"{"action" : "check_health", "params":{} }"
```

### 9.2 応答例

```json
{
  "feedback":{
    "health":"病気",
    "診断": "リモート製品のウェブサービスはオフラインです"
  },
  "result":0
}
```

### 9.3 戻り値

Mendix Studio Proでは、 [ヘルスチェックマイクロフロー](project-settings) を設定できます。 このマイクロフローは、アプリケーションの機能状況を報告することができます。 アプリケーションの一般的な機能は機能し、必要なリモートサービスは利用可能ですか?

ヘルスチェックマイクロフローが設定されている場合、このリクエストは現在のヘルスステータスを報告します。 "health" の値は "healthy"、"病気"、"unknown" のいずれかになります(ヘルスマイクロフローが設定されていない場合)。 値「病気」の場合、「診断」の値は、アプリケーションが健康でない理由を与えます。 この理由は、ヘルスチェックマイクロフローの戻り値です。

ヘルスチェック・マイクロフローは1分間に複数回呼び出されます。 そのため、軽量化と迅速な走行が推奨されます。 重い操作はアプリケーションのパフォーマンスに大きな影響を与える可能性があります。

{{% alert type="warning" %}}

このリクエストは、Mendix Runtime ステータスが "実行中" の場合にのみ実行できます (上記の [Runtime Status](#runtime-status) を参照)。

{{% /alert %}}

## 10 ランタイムについて

### 10.1 リクエスト

```json
"{"action" : "about", "params":{} }"
```

### 10.2 応答例

```json
{
   "feedback":{
      "model_version":"unversioned",
      "copyright:"Copyright © 2003-2016 Mendix bv. All rights reserved.",
      "build":"unreleased",
      "vendor":"Mendix",
      "name":"Mendix Runtime",
      "java_version":"1.8.0_77",
      "xasid":"68ece856-3771-4024-9c42-078aaa2282aa",
      "version":"unreleased"
   },
   "result":0
}
```

### 10.3 戻り値

Mendix Runtime についてのフィードバックを返します。
