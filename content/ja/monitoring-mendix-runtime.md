---
title: "Mendix ランタイムの監視"
category: "Mendix Runtime"
description: "サポートされているMendixランタイム監視アクションの説明。"
tags:
  - "ランタイムjson"
---

## 1つの紹介

Mendix Runtime 監視アクションは、管理者ハンドラに JSON リクエストを送信することで呼び出すことができます。 これは、アプリケーションの構成設定で指定されたアドミンポートにリクエストを送信することで実現します(デフォルトは 8090 です)。

You can change the admin port from the Desktop Modeler by navigating to **Project** > **Settings** > **Configurations** > *your configuration* > **Server** > **Admin port**.

リクエストは **POST** 型の **No Authorization** および以下のヘッダである必要があります:

* Content-Type: **application/json**
* X-M2EE認証: **yourM2EEPassword_Base64Encoded**

M2EE パスワードは、スーパー管理者パスワードではなく、別のパスワードです。 If you have the application deployed on premises, you can set this password in the **settings.yaml** file, which is located in the **Apps/YourProject** folder. Desktop Modelerからアプリケーションを実行している場合、M2EEパスワードはMendixによって自動的に設定されます。 アプリケーションプロセスの環境変数から取得することができます

次のセクションを読んで、どのモニタリングアクションがサポートされているかを確認してください。

## 2 現在の実行

**リクエスト**

```java
"{"action" : "get_current_runtime_requests", "params":{} })

```

**回答**

```java
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

このリクエストは、Mendix Runtime によって知られているアクションの現在の実行を返します。 アクションは、マイクロフロー、Javaアクション、Webサービス呼び出し、スケジュールされたイベントなどがあります。 実行ごとに以下が報告されます:

*   ミリ秒単位の実行の「継続時間」。
*   実行の"タイプ"。 利用可能なタイプは「CLIENT」、「CLIENT_ASYNC」、「CLIENT_ASYNC_MONITORED」、「CUSTOM」、「WEB_SERVICE」、「SCHEDULED_EVENT」、「UNKNOWN」です。 CLIENT_ASYNCは、ウェブクライアントからトリガーされた非同期マイクロフロー呼び出しです。 「CLIENT_ASYNC_MONITORED」は、異なるスレッドで発生するMendix Runtime内の非同期マイクロフローの実際の実行です。
*   「user」は、アクションを実行しているセッションに関連付けられたユーザーの名前です。 ユーザ以外のセッションの場合は、"System" という名前が表示されます。
*   "action_stack" は、この実行のためのアクションのスタックを示します。 例えば、このスタック内の各アクションの詳細情報が表示されます。 マイクロフローの場合、現在の活動とマイクロフローの名前が表示されます。

## 3ランタイム統計

**リクエスト**

```java
"{"action" : "runtime_statistics", "params":{} }"

```

**回答**

```java
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
      "tenured":0,
      "committed_heap":301465600,
      "max_heap":3817865216,
      "survivor":0,
      "used_nonheap":67844048,
      "max_nonheap":-1,
      "committed_nonheap":72777728,
      "permanent":0,
      "used_heap":125300600
    },
     "result":0
  }
}
```

<u>リクエスト</u> ハンドラごとのリクエストに関する情報を表示します。 value フィールドには、ハンドラあたりのリクエスト数が表示されます。 Mendix 5.3 以降、last_request_timestamp 項目には、最後に処理されたリクエストのミリ秒単位のタイムスタンプが表示されます。 処理されたリクエストがない場合、この項目はハンドラが登録された瞬間を示します。 空のハンドラはリソースリクエストハンドラを表し、画像やフォームなどを処理します。 (静的コンテンツハンドリングにリバースプロキシが使用されない場合にのみ使用されます)。 "file" はファイルのアップロードとダウンロードを処理します "xas/"は、Webクライアントによって発行されたCRUDアクションとマイクロフロー実行呼び出しを処理し、"ws/"と"ws-doc/"は、Webサービス要求を処理し、Webサービス文書を提供します。

<u>キャッシュ</u>

ランタイム状態 (すべてのセッションをまとめて) に現在参加しているオブジェクトの合計数を表示します。 ランタイム状態は、メモリ(非クラスターランタイム)またはRedisまたはデータベース(クラスターランタイム)のいずれかに存在します。 状態にあるオブジェクトが多すぎると、Mendix Runtime のパフォーマンスが低下する可能性があります。

<u>セッション</u> 「user_sessions」セクションには、ユーザエージェントを使用している現在のユーザセッションが表示されます。 他のセクションには、カテゴリごとのセッション数が表示されます。 カテゴリは「名前付きユーザー」(ユーザーインスタンス数)、「named_user_sessions」(非匿名の同時セッション数)、「anonymous_sessions」(匿名の同時セッション数)です。

<u>Connectionbus</u> データベースのリクエスト数。 "select", "update", "insert", "delete" コマンドとデータベーストランザクションを開始したものを区別します。

<u>メモリ</u>

{{% alert type="warning" %}}

メモリ統計量は専門家によってのみ解釈されるべきであり、Javaメモリモデルの詳細な知識の欠如は誤った結論につながる可能性があります。

{{% /alert %}}{{% alert type="warning" %}}

後方互換性の理由として、フィールド "code", "eden", "tened", "survivor" と "permanent" はまだ存在しますが、それらはもはや依存すべきではありません。 彼らはMendix 7以降から削除されます。

{{% /alert %}}

指定されたメモリセクションに割り当てられたバイト数を表します。 一般的な説明については、ガベージコレクションのチューニングに関する [Oracleドキュメント](http://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/) を参照してください。 ヒープフィールドと非ヒープフィールドについては、 [メモリ使用量](https://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryUsage.html) ページを参照してください。 「memorypools」セクションには、JVMから受信するのとまったく同じようにすべてのメモリプールの順序付きリストがあります。 [MemoryPoolMxBean](http://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryPoolMXBean.html) のいくつかのフィールドと同じ順序で :

*   "usage": このメモリ プールのメモリ使用量の推定値(バイト単位)を返します。
*   "is_heap": このメモリプールはヒープの一部ですか?
*   "name": JVM によって受信されるメモリープールの説明。 これらの名前は、JDK、メモリマネージャ、またはガベージコレクションオプションなどによって異なる場合があります。
*   "index": JSON Array内のインデックス。 プールがリストに返されるため、このフィールドは必須ではありません。 プログラムで処理する場合に備えてリストの順番に頼るべきです

{{% alert type="info" %}}

"memorypools" セクションを自動的に処理する場合は、例えばグラフに表示します。 理想的には、ガベージコレクタの設定や Java バージョンなどによって、リスト内の順序や名前に基づいてメモリープールの種類を想定しないでください。

Javaバージョンに基づいて、とにかくこれらのプールを解釈するための戦略を開発したい場合: 「about」管理アクションからJavaバージョンを取得できます。

{{% /alert %}}

## 4要塞統計

**リクエスト**

```java
"{"action" : "cache_statistics", "params":{} }"

```

**回答**

```java
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

この監視アクションは、Mendix Runtime の状態にあるオブジェクトに関する詳細な情報を提供します。 「合計」では、セッションごとのオブジェクト数の合計が表示されます。「user_totals」では、特定のセッションごとのエンティティごとのオブジェクト数が表示されます。 この情報は、どのオブジェクトが多くのメモリ使用量を引き起こすかを把握するのに役立ちます。

## 5つのサーバー統計 {#server-statistics}

**リクエスト**

```java
"{"action" : "server_statistics", "params":{} }"

```

**回答**

```java
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

サーバー統計モニタのアクションは、埋め込まれた Jetty Web サーバーに関する情報を提供します。 「jetty」セクションには、現在開いている接続の数と開いている接続の最大数が表示されます。 さらに、Jetty が通常の状況下にある場合は、接続が閉じられる前のアイドル時間の最大値がリストされます。 Mendix 7に注意してください。 そしてその上に Jetty がリソースが低い時("max_idle_time_s_low_resources")に接続がクローズされる前のアイドル時間に関する情報は、Jetty のアップグレードの一部として削除されます。 ジェッティによって提供されなくなったからです

"threadpool" セクションは、ランタイムポートを通過するすべてのリクエストを処理するハンドラの threadpool に関する情報を提供します。 詳細は [Jetty QueuedThreadPool ドキュメント](https://www.eclipse.org/jetty/javadoc/9.4.11.v20180605/org/eclipse/jetty/util/thread/QueuedThreadPool.html) を参照してください。

## 6人のログインユーザー

**リクエスト**

```java
"{"action" : "get_logged_in_user_names", "params":{} }"

```

**回答**

```java
{
  "feedback": {
    "count":1,
    "users":["MxAdmin"]
  },
  "result":0
}
```

現在ログインしているユーザーを表示します。 ユーザに複数のセッションがある場合、このユーザは各セッションに一度だけ表示されます。

## スレッドスタックトレース

**リクエスト**

```java
"{"action" : "get_all_thread_stack_traces", "params":{} }"

```

**回答**

```java
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
    ]
  },
  "result":0
}
```

現在のスレッドスタックトレースをすべて名前で返します。 これは、アプリケーションで起こっていることを低レベルで分析する場合に便利です。 "get_current_runtime_executions" リクエストを使用して、より高いレベルの情報(マイクロフローやその他のアクション)を取得します。
{#check-health}
## 8回のランタイムステータス {#runtime-status}

**リクエスト**

```java
"{"action" : "runtime_status", "params":{} }"

```

**回答**

```java
{
  "feedback":{
    "status":"running"
  },
  "result":0
}
```

現在の Mendix ランタイムステータスを返します。 状態値は次のとおりです: "created", "starting", "broken", "running", "stopped" and "stopped". この情報は、Mendix Runtime がどのような状態で開始または停止されたかを追跡したり、ランタイムがまだ実行されているかどうかを確認したりするために使用できます。

## 体力を9点確認 {#check-health}

**リクエスト**

```java
"{"action" : "check_health", "params":{} }"

```

**回答**

```java
{
  "feedback":{
    "health":"病気",
    "診断": "リモート製品のウェブサービスはオフラインです"
  },
  "result":0
}
```

Mendix Desktop Modelerでは、 [ヘルスチェックマイクロフロー](project-settings) を設定できます。 このマイクロフローは、アプリケーションの機能状態を報告することができます: アプリケーションの一般的な機能を実行します。 必要な遠隔サービスは利用できるのか?

ヘルスチェックマイクロフローが設定されている場合、このリクエストは現在のヘルスステータスを報告します。 "health" の値は "healthy"、"病気"、または "unknown" のいずれかになります(ヘルスマイクロフローが設定されていない場合)。 値「病気」の場合、「診断」の値は、アプリケーションが健康でない理由を与えます。 この理由は、ヘルスチェックマイクロフローの戻り値です。

ヘルスチェック・マイクロフローは1分間に複数回呼び出されます。 そのため、軽量化と迅速な走行が推奨されます。 重い操作はアプリケーションのパフォーマンスに大きな影響を与える可能性があります。

{{% alert type="warning" %}}

このリクエストは、Mendix Runtime ステータスが "実行中" の場合にのみ実行できます (上記の [Runtime Status](#runtime-status) を参照)。

{{% /alert %}}

## 10 ランタイムについて

**リクエスト**

```java
"{"action" : "about", "params":{} }"

```

**回答**

```java
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

Mendix Runtime についてのフィードバックを返します。
