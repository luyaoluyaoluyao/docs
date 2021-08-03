---
title: "Mendix 运行时间"
---

## 1 导言

Mendix Runtime 执行在模型中创建的应用程序模型。 它为Mendix 客户端提供网页服务，执行微流，呼叫网络服务，生成文件，与数据库通讯，等等。

## 2 个许可证

您需要许可证才能在生产模式下运行一个应用程序。 没有许可证，Mendix Runtime 会在几个小时后停止操作。 许可证可以通过Mendix的帐户管理器获得。 然后，您可以按照 [中的指示激活您的 Mendix 许可证](/developerportal/deploy/activate-a-mendix-license-on-microsoft-windows) 来激活您的许可证。

## 3 个APIs

您可以写入 Java 操作来扩展运行时的功能。 欲了解更多信息，请参阅 *API 文档的 [运行时间API](/apidocs-mxsdk/apidocs/#runtime) 部分。*。

{{% alert type="info" %}}
Links to available API documentation such as WSDLs for published web services are available on the URL path `/api-doc` (for example: `http://localhost:8080/api-doc/`).
{{% /报警 %}}

## 此类别中的4个主要文档

* [集群的 Mendix 运行时间](clustered-mendix-runtime)
* [自定义](自定义设置)
* [数据存储](数据存储)
* [日期 & 时间处理](datetime-handling-faq)
* [日志记录](logging)
* [监控Mendix 运行时间](monitoring-mendix-runtime)
* [对象 & 缓存中](objects-and-caching)
* [短暂对象 & 垃圾收集](transient-objects-garbage-collecting)
