---
title: "Mendix 运行时间"
tags:
  - "运行时间"
  - "运行时服务器"
  - "mendix 客户端"
  - "群组领导者"
---

## 1 导言

Mendix Runtime 实际上是一个“运行”Mendix 模型并为用户提供页面服务的解释器。

每个补丁版本的 Mendix 都有自己的运行时版本，实现Mendix 中可用的功能。 例如，Mendix 8.4.1和8.4.2的运行时间不同，只能为该版本运行Mendix 应用。

## 2 运行时概述

Mendix 运行时间由两个部分组成： [运行时服务器](runtime-server) and [Mendix 客户端](mendix-client)。 两者之间的关系见下表。

运行时服务器在云平台上启动，执行微流并连接到文件、关系数据库和任何其他所需服务。 它等待Mendix 客户端联系。 运行时服务器在 [运行时服务器](runtime-server) 中有更详细的描述。

Mendix 客户端由最终用户启动。 这可以在网页浏览器内，或在其他支持的设备上。 如果它处于在线模式，它会与 Runtime 服务器启动会话，这可能需要或不需要身份验证。 运行时服务器在数据库中记录会话的详细信息，以便Mendix 客户端能够提出请求。 Mendix 客户端在 [Mendix 客户端](mendix-client) 中有更详细的描述。

最终用户与 Mendix 客户端交互，然后向 Runtime 服务器提出处理数据或执行服务器端函数的请求（例如微流程）。 在请求结束时，所有状态(包括未提交的数据)都会被传回Mendix 客户端。 您可以在 [Mendix Runtime](communication-patterns) 中找到此通信发生方式的更多细节。

从 Runtime Server 到Mendix 客户端的状态使得运行时服务器成为无状态的。 这意味着任何运行时服务器实例都可以响应Mendix 客户端的请求。 负载均衡器决定哪些运行时服务器实例将响应请求。 当最终用户会话结束时，运行时服务器会删除对该会话的引用。

在有多个应用程序实例的情况下，其中一个实例将是 *组队长*。 此实例中的 Runtime 服务器将负责一些无法轻松分发的活动。 这些措施包括：

* 会话清理处理
* 集群节点过期处理
* 背景作业过期处理
* 解除屏蔽的用户
* 正在执行预定的事件
* 正在执行数据库同步任务
* 在新部署后清除持续会话

关于多个实例的更多信息在 [聚类Mendix 运行时](clustered-mendix-runtime) 中。

![Mendix 运行时概述](attachments/runtime/runtime-overview.png)

图表的每个组成部分说明如下：

### 2.1 外部服务

外部服务提供您Mendix 应用程序以外的数据和其他功能。 这些可以是外部数据源，如SAP，外部显示小部件，如谷歌地图，或外部数据处理，如IBM Watson机器学习。 运行时服务器通过HTTP(S)连接与这些通信。

### 2.2 基础设施

这是Mendix 应用将被部署的硬件。 它通常作为一种服务基础设施提供，在公共或私人云中提供虚拟机器。 然而，基础设施也可以是房地内运行的有形机器。 例如亚马逊网络服务（AWS）、微软Azure或Windows Server 机器。

### 2.3 文件

这是存储作为应用程序所使用数据一部分的文件的地方。 特别是它包含 *FileDocument* 对象的值，包括图像， 它是存储在数据库之外的二进制对象，以避免大小和性能限制。

### 2.4 关联数据库

这是一个数据库（或有时是一个共享数据库的图表），它存有应用中域模型所定义的对象。

### 2.5 平台

这是Mendix 应用程序正在运行的操作系统以及额外的服务。 例如，一个数据库，这个数据库已经连接到应用程序。

### 2.6 实例

也调用 **App Container**。 这将启动并暴露运行时服务器。 可能只有一个例子，但为了提供高可用性和更好的性能，可能会有许多例子。

### 2.7 运行时服务器

这是Mendix 运行时间的服务器端。 [Runtime Server](runtime-server) 描述了它。

### 2.8 负载平衡

负载均衡器接收Mendix 客户端的传入请求，并将它们转发到 Runtime Server 实例。 它平衡负荷，确保请求平均分配给不同的实例。 Mendix 客户端使用 HTTPS 与负载平衡器通信。 负载均衡器的服务器端与环境实例和 CDN之间的通信使用HTTP进行。

### 2.9 CDN 静态配置

CDN (内容交付网络) 包含客户端需要的静态配置信息。 这些包括从浏览器启动Mendix 客户端所需的文件。 定义应用程序主题的级层样式表(ss文件)和定义客户端逻辑的 JavaScript 文件。

### 2.10 Mendix Client

这是允许最终用户与应用交互的浏览器或设备。 这可以是一个 Web 浏览器，如Chrome 或移动设备，如iPhone 。 它通常有屏幕、指针设备和输入设备，允许最终用户使用应用程序。 Mendix 客户端在 [Mendix 客户端](mendix-client) 中描述。

## 3种许可证

您需要许可证才能在生产模式下运行一个应用程序。 没有许可，运行时服务器在几个小时后休眠。 关于Mendix 应用程序的许可信息可以在 [许可应用程序](/developerportal/deploy/licensing-apps-outside-mxcloud) 中找到。

## 4 个APIs

您可以写入 Java 操作来扩展运行服务器的功能。 欲了解更多信息，请参阅 *API 文档的 [运行时间API](/apidocs-mxsdk/apidocs/#runtime) 部分。*。

{{% alert type="info" %}}
如果应用程序包含已发布的服务， 链接到可用的 API 文档，例如 [OpenAPI 文档](open-api) 用于 [已发布的REST 服务](published-rest-services), 链接到 [发布的 OData 服务](published-odata-services)和 WSDL [发布的网络服务](published-web-services)可在URL路径上查阅 `/api-doc` (例如： `https://myapp. endixcloud.com/api-doc/`)。
{{% /报警 %}}

## 5 个此类别中的主要文档

* [运行时服务器](runtime-server) - 描述运行时服务器的工作
* [Mendix 客户端](mendix-client) -- 描述Mendix 客户端的工作
* [运行时部署](runtime-deployment) - 描述如何将 Mendix 运行时间部署到云端
* [聚类Mendix Runtime](clustered-mendix-runtime) -- 描述运行 Mendix Runtime 作为集群的行为和影响
* [运行时自定义](custom-settings) - 提供自定义运行时服务器设置的高级选项
* [数据存储](data-storage) - 提供数据存储配置选项的信息，例如：
* [日期 & 时间处理](datetime-handling-faq) -- 介绍如何为用户的日期和时间配置运行服务器操作的详细信息
* [日志](logging) - 讨论运行时的各种日志级别
* [Monitoring Mendix Runtime](monitoring-mendix-runtime) — — 描述支持的 Mendix Runtime 监视动作(如 [状态统计](monitoring-mendix-runtime#state) 和 [线程堆栈跟踪](monitoring-mendix-runtime#thread))。
* [对象 & 缓存](objects-and-caching) - 提供从数据库加载对象、缓存、检索、更改和提交时发生的事项的详细信息
* [Mendix Runtime & Java](runtime-java) - 解释Mendix 中Java 的一些基本概念
* [Mendix Runtime 中的通信模式](communication-patterns) - 概述Mendix runtime 使用的通信模式
