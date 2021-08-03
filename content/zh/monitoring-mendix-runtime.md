---
title: "监控Mendix 运行时间"
category: "Mendix 运行时间"
description: "描述支持的 Mendix 运行时监测操作。"
tags:
  - "运行时间，json"
---

## 1 导言

Mendix Runtime 监视动作可以通过向管理员发送JSON请求来调用。 这是通过向应用程序配置中指定的管理端口发送请求(默认为8090)。

您可以通过导航到 **项目** > **设置** > **配置** > *您的配置* > **服务器** > **管理端口**

请求必须是 **POST** 类型，带有 **无授权** 和下列文件头：

* Content-Type: **application/json**
* X-M2EE-身份验证： **yourM2EPassword_Base64Encoded**

M2EE 密码不是超级管理员密码，而是一个单独的密码。 如果应用程序部署在房地，您可以在 **设置中设置此密码。 aml** 文件，位于 **Apps/YourProject** 文件夹中。 如果您正在从桌面模式运行应用程序，M2EE 密码将自动由 Mendix 设置。 并且您可以从应用程序的环境变量中获取它。

阅读下面的章节以了解支持哪些监测行动。

## 2 当前执行

**请求**

```java
"{"action" : "get_current_runtime_requests", "params":{} }"

```

**答复**

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

此请求返回Mendix Runtime已知的当前执行操作。 除其他外，行动可以是微流、Java 行动、网络服务通话和预定活动。 每次执行报告如下：

*   以毫秒为单位执行的“持续时间”。
*   执行的“类型”。 可能的类型有："CLIENT"、"CLIENT_ASYNC"、"CLIENT_ASYNC_MONITORED"、"CUSTOM"、"WEB_SERVICE"、"SCHEDULED_EVENT"和"UNKNOWN"。 "CLIENT_ASYNC"是从网页客户端触发的异步微流通话， "CLIENT_ASYNC_MONITORED"是Mendix Runtime中异步微流的实际执行，在不同的线程中发生。
*   "用户"是与执行该动作的会话相关的用户名。 如果是非用户会话，则显示“系统”的名称。
*   "action_stack"显示此执行的动作堆栈。 此堆栈中的每个动作都会显示详细信息，例如： 微流显示当前活动和微流的名称。

## 3 运行时统计

**请求**

```java
"{"action" : "runtime_statistics", "params":{} }"

```

**答复**

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

<u>请求</u> 显示每个处理器请求的信息。 值字段显示每个处理器的请求数量。 自从Mendix 5.3以来，最后一次处理的请求中的时间戳字段以毫秒为单位显示时间戳。 如果没有处理请求，此字段显示处理程序注册的时间。 空处理程序代表资源请求处理器，处理图像、表单等。 (仅在没有反向代理用于静态内容处理时使用)。 "file"处理文件上传和下载， “xas/”处理Web客户端发出的 CRUD 动作和微流程执行呼叫和“ws/”和“ws-doc/”处理网络服务请求并提供网络服务文档。

<u>缓存</u>

显示当前为运行状态一部分的对象总数(所有会话一起)。 运行状态要么位于内存(非集群运行时间)，要么位于Redis或数据库(集群运行时间)。 状态下太多的对象可能会减慢Mendix Runtime的性能。

<u>会话</u> "user_sessions" 部分显示当前用户会话与他们的用户代理人。 其他章节显示每个类别的会议次数。 类别是“命名用户”（用户实例）、“named_user_sessions”（非匿名并行会话的数目）和“匿名会话”（匿名并行会话的数目）。

<u>Connectionbus</u> 数据库请求数量。 区分"选择"、"更新"、"插入"、"删除"命令和开始数据库交易。

<u>内存</u>

{{% alert type="warning" %}}

只有专家才能解释记忆统计数字，缺乏对Java 记忆模型的详细了解，可能导致错误的结论。

{{% /警示%}}!{% alert type="warning" %}}

出于背后兼容的原因，仍然存在“代码”、“编辑”、“保有权”、“幸存者”和“永久”等字段，但不应再依赖这些字段。 他们将从Mendix 7以后被除名。

{{% /报警 %}}

代表分配给指定内存部分的字节数。 欲了解一般性解释，请参阅 [Oracle文档关于调整垃圾收集](http://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/)。 关于堆和非堆域，请参阅 [内存使用率](https://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryUsage.html) 页。 “内存池”部分包含一个从JVM接收的所有内存池的顺序列表。 在 [MemoryPoolMxBean](http://docs.oracle.com/javase/8/docs/api/java/lang/management/MemoryPoolMXBean.html) 的相同顺序和一些字段中：

*   "usage": 返回此内存池内存使用量的估计(字节)。
*   "is_heap"：这个内存池是否为堆的一部分？
*   "name"：JVM收到的内存池描述。 这些名称可以根据例如JDK、内存管理器或垃圾收集选项而有所不同。
*   "索引"：JSON 数组中的索引。 这个字段并不是严格需要的，因为集合将在列表中返回，所以你可以。 并且应该依靠列表的顺序，以备您在程序中处理它们。

{{% alert type="info" %}}

如果您正在自动处理要在图表中显示的“内存池”部分， 您最好不要根据列表中的顺序或名称对内存池类型做任何假设，因为这些假设可能会根据垃圾收集器设置或Java 版本而改变。

如果你确实想要制定基于Java 版本的解释这些池的策略：你可以从 'about' 管理员操作中得到Java 版本。

{{% /报警 %}}

## 4 国家统计

**请求**

```java
"{"action" : "cache_statistics", "params":{} }"

```

**答复**

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

这个监视行动提供更详细的信息，介绍当前Mendix Runtime状态的对象。 在“总计”中，显示每个会话的对象总数，在“user_totals”中显示每个实体特定会话的对象数目。 这种信息可以帮助查出哪些对象会造成大量内存消耗。

## 5 服务器统计 {#server-statistics}

**请求**

```java
"{"action" : "server_statistics", "params":{} }"

```

**答复**

```java
主席:
  "反馈":□
    "jetty":
      "current_connections":0,
      "max_connections":0,
      "max_idle_time_s":200
    },
    "threadpoor": P,
      "idle_threads":3,
      "max_threads":254,
      "threads_priority":5,
      "threads":8,
      "max_队列":-1,
      "min_threads":8,
      "max_idle_time_s":60,
      "max_stop_time_s":0
    }
  },
  "result":0
}
```

服务器统计监视行动提供嵌入的 Jetty 网络服务器的信息。 “jetty”部分列出当前开放连接的数量和开放连接的最大数量。 此外，连接关闭前的最大空闲时间列出，如果Jetty在正常情况下。 请注意Mendix 7中的内容。 及以上， 当Jetty资源低时关闭连接前最大空闲时间的信息("max_idle_time_s_low_resources") 已被移除，作为Jetty升级的一部分， 因为它不再由犹太人提供。

“线程池”部分提供了处理器的线程池的信息，处理所有通过运行时端口的请求。 查看 [Jetty 队列ThreadPool 文档](https://www.eclipse.org/jetty/javadoc/9.4.11.v20180605/org/eclipse/jetty/util/thread/QueuedThreadPool.html) 获取更多信息。

## 6 名登录用户

**请求**

```java
"{"action" : "get_logged_in_user_names", "params":{} }"

```

**答复**

```java
主席:
  "feedback": format@@
    "count":1,
    "users":["MxAdmin"]
  },
  "result":0
}
```

显示当前登录的用户。 如果一个用户有多个会话，此用户将成为每个会话的一次列表。

## 7 个线程堆栈跟踪

**请求**

```java
"{"action" : "get_all_thread_stack_traces", "params":{} "

```

**答复**

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

按名称返回所有当前线程堆栈跟踪。 这有助于低级别分析应用程序中正在发生的情况。 使用“get_current_runtime_executions”请求获取更高级别的信息(microflow和其他动作)。
{#check-health}
## 8 运行状态 {#runtime-status}

**请求**

```java
"{"action" : "runtime_status", "params":{} }"

```

**答复**

```java
主席:
  "feedback":□
    "status":"running"
  },
  "result":0
}
```

返回当前 Mendix 运行时状态。 可能的状态值为："创建", "启动", "损坏", "运行", "停止"和"停止"。 此信息可以用于跟踪Mendix Runtime在给定命令开始或停止时的状态或检查运行时间是否仍在运行。

## 9 检查健康 {#check-health}

**请求**

```java
"{"action" : "check_health", "params":{} }"

```

**答复**

```java
{
  "feedback":{
    "health":"sick",
    "diagnosis": "Remote product web service is offline"
  },
  "result":0
}
```

在 Mendix 桌面模式中，可以配置 [健康检查微流程](project-settings)。 这个微流可以报告应用程序的功能状态：应用程序的一般功能是否正常。 是否有必要的远程服务？

如果配置了健康检查微流，此请求将报告当前的健康状况。 “健康”值可以是“健康”、“疾病”或“未知”(当没有配置健康微流时)。 关于“病”值，“诊断”值会给出应用不健康的原因。 这个原因是健康检查微流的返回值。

健康检查微流每分钟被多次调用。 因此，建议轻量和快速运行。 重型操作可能会对您的应用程序的性能产生重大影响。

{{% alert type="warning" %}}

此请求只能在Mendix Runtime 状态“正在运行”时执行(见上文 [运行状态](#runtime-status))。

{{% /报警 %}}

## 10 关于运行时间

**请求**

```java
"{"action" : "about", "params":{} }"

```

**答复**

```java
主席:
   "feed":~
      "model_version":"unversioned",
      "copyright":"Copyright © 2003-2016 Mendix bv. 保留所有的权利。”、
      "build":"unreleased",
      "vendor":"Mendix",
      "name":"Mendix Runtime",
      "java_version":"1.8.0_77",
      "xasid":"68ece856-3771-4024-9c42-078aaaaa2282a",
      "version":"unreleased"
   },
   "result":0

```

返回关于 Mendix Runtime的反馈。
