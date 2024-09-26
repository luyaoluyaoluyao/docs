---
title: "系统要求"
category: "常规信息"
menu_order: 10
description: "显示使用 Mendix 平台的系统要求。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/system-requirements.pdf)。
{{% /报警 %}}

## 1 导言

本文件介绍Mendix Platform各部分的系统要求。

## 2 Mendix Studio Pro {#sp}

Mendix [Studio Pro](modeling) 支持 Windows 7、8和10的64位版本。 Windows 7 必须至少是服务包 1。

以下框架已自动安装(如果需要的话)：

* Microsoft .NET Framework 4.7.2和所有适用的 Windows 安全补丁
* Microsoft Visual C++ 2010 SP1 可Redistributable 软件包
* Microsoft Visual C++ 2015 Redistributable 软件包
* AdoptOpenJDK 11 或 Oracle JDK 11 (前者自动安装在 [Mendix 8。 .0](/releasenotes/studio-pro/8.0#800) 如果您没有安装任何 JDK 11 )

{{% alert type="info" %}}
您可以选择 JDK 通过 **编辑** > **在 Studio Pro中使用** 菜单项来构建和在本地运行。
{{% /报警 %}}

{{% alert type="warning" %}}
请注意数据库查看器嵌入Studio Pro 中的限制(如 [如何共享开发数据库](/howto8/collaboration-requirements-management/sharing-the-development-database)) 与 JDK 11不兼容。 6 或 11.07。
{{% /报警 %}}

### 2.1 防火墙设置

Studio Pro 需要访问以下URL才能工作。 如果您的防火墙目前正在屏蔽它们，您需要将它们加入白名单。

* `*.mendix.com`
* `*.mendixcloud.com`
* `*.teamserver.sprintr.com`

### 2.2 TortoiseSVN

如果您想要使用 TortoiseSVN 与 Studio Pro，请从 [TortoiseSVN](https://tortoisesvn.net/) 网站下载最新版本。

{{% alert type="warning" %}}
Mendix Studio Pro 使用 Subversion 1.9 的工作副本。 Mendix 桌面Modeler使用了一个 Subversion 1.7 工作副本。 这些工作副本版本 **不兼容**。

总是使用 TortoiseSVN 版本来匹配您的应用模型。 如果您从 Mendix 版本 7.x 或6 打开本地模型。 使用最新版本的 TortoiseSVN **您将无法在 Mendix** 中打开它。
{{% /报警 %}}

## 3 个团队服务器 {#ts}

[团队服务器](/developerportal/collaborate/team-server) 正在使用 Subversion, Studio Pro 使用HTTPS 协议与该服务器通信。 要从 Studio Pro内部访问团队服务器，您所在位置的网络需要以下设置：

* HTTPS 端口 (TCP 443) 需要打开
* HTTP 端口 (TCP 80) 需要打开
* 需要在代理服务器上启用 WebDAV (HTTP 协议中的动词)

## 4 Mendix Studio

[Mendix Studio](/studio) 被优化用于谷歌Chrome。 虽然Chrome是官方支持的浏览器，但您也可以使用Mendix Studio和其他受欢迎的浏览器，如Mozilla Firefox、Apple Safari和Microsoft Edge。

{{% alert type="info" %}}
您使用的浏览器需要打开 JavaScript 。
{{% /报警 %}}

## 5个云层基金会
[Mendix Cloud Foundry buildpack](https://github.com/mendix/cf-mendix-buildpack) 支持 Cloud Foundry 版本 v9 及以上版本。

## 6 停靠栏
[Mendix Docker buildpack](https://github.com/mendix/docker-mendix-buildpack) 支持Docker版本18.09.0 及以上版本。

### 6.1 Kubernetes
Mendix Docker Buildack支持以下版本：

* Kubernetes 版本 v1.12 及以上
* Redhat Openshift v3.11 和 v4.2及以上

## 7 个服务器

### 7.1 操作系统

* Microsoft Windows Server 2008 SP2 及以上
* Debian 8 (Jessie) 及以上
* Red Hat Enterprise Linux 6, Red Hat Enterprise Linux 7
* CentOS 6, CentOS 7

### 7.2 Web 服务器

* Microsoft Internet Information Services 7及以上
* Nginx (Debian Jessie 和 Debian Jessie Backports) 版本测试
* Apache

### 7.3 Java

当在服务器上运行 Mendix 时，您将需要 Java Runtime 环境 (JRE) 11。 要从 AdoptOpenJDK 下载OpenJDK 分布，请参阅 [AdoptOpenJDK installation](https://adoptopenjdk.net/installation.html)。 若要下载商用Oracle分发，请参阅 [Java SE 下载](http://www.oracle.com/technetwork/java/javase/downloads/index.html)。

{{% alert type="info" %}}
从 Java 7 开始出现了一个问题，在使用一定数量的数据的 web 服务时导致超时。 您可以通过添加 VM 参数 `-Djava.net。首选IPv4Stack=true` 来绕开这个问题。 Mendix Studio Pro 将为您做这件事。 但如果您在 Windows 服务器上的前提下运行 Mendix ，您将需要自己这样做。 关于此问题的更多信息，请参阅 [HotSpot (64位 server) 套接字挂卡(JVM 1.7 bug?) - 更新](http://blog.bielu.com/2011/11/hotspot-64bit-server-hangs-on-socket.html) 和 [Java 7 中可能出现的漏洞](https://forums.oracle.com/forums/thread.jspa?messageID=9985748)
{{% /报警 %}}

## 8 数据库 {#databases}

Mendix 试图支持数据库供应商最新和修补过的数据库服务器版本。 我们打算在供应商发布后再支持新的供应商版本两个小版本的Mendix。 将在供应商放弃支持之日的发行说明中宣布放弃对数据库的支持。 稍后我们会投放两个次要的 Mendix 版本。

当前支持：

* [IBM DB2](db2) 11.1和11.5 for Linux、Unix和Windows
* [MariaDB](mysql) 10.2, 10.3, 10.4, 10.5
* [Microsoft SQL Server](/developerportal/deploy/mendix-on-windows-microsoft-sql-server) 2017, 2019
* [Azure SQL](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-2017) v12 兼容模式 140 或以上
* [MySQL](mysql) 8.0
* [Oracle 数据库](oracle) 19
* PostgreSQL 9.6, 10, 11, 12, 13
* [SAP HANA](saphana) 2.00.040.00.1545918182

{{% alert type="warning" %}}
每个应用都应该有自己的数据库。 Mendix 应用无法通过共享相同的数据库共享数据。
{{% /报警 %}}

## 9 个文件存储

### 9.1 集装箱储存服务

对于使用 Docker, Kubernetes, 或 Cloud Foundy, 基于容器的部署，支持以下存储服务：

* AWS S3
* Azure Blob 存储
* IBM 云对象存储
* SAP AWS S3 对象存储
* SAP Azure Blob 存储

关于由外部存储类提供的Kubernetes容器装载的存储器，另见 [在 Kubernetes 上运行Mendix](/developerportal/deploy/run-mendix-on-kubernetes)。

### 9.2 服务器的存储类型

对于基于服务器的安装，支持以下由操作系统挂载的存储类型：

* NAS
* 萨恩文
* GFS
* 本地存储

## 10 Browsers {#browsers}

* Google Chrome (最新稳定的桌面版和 Android 版本)
* Mozilla Firefox (最新稳定的桌面版本)
* 苹果 Safari (最新稳定的桌面版本和每支持 [的 iOS](#mobileos) 版本的最新版本)
* Microsoft Edge (最新稳定桌面版本)
* Microsoft Internet Explorer 11

## 11 混合预览

使用混合预览与使用仿真器不同。 混合预览只显示一个应用的缩放视图，让人对该应用在移动设备上可能是什么样子。 此浏览器视图不支持一些混合应用功能。 完全测试总是需要在设备或仿真器上进行。 离线应用只能在 Google Chrome 中预览。

## 12 移动操作系统 {#mobileos}

对于Mendix 应用程序和 [Mendix 移动应用程序](getting-the-mendix-app)：

* iOS 12及以上
* Android 5.0 及以上版本

## 13 MxBuilding {#mxbuild}

MxBuild是一个 Windows 和 Linux 命令行工具，可用来构建Mendix 部署包。 欲了解更多信息，请参阅 [MxBuild](mxbuild)。

* Mono v5.20.x 或 .NET v4.7.2
* JDK 11

## 14 mx 命令行工具 {#mxtool}

**mx** command-line 工具是一个 Windows 和 Linux 命令行工具，可用来在您的 Mendix 应用程序中做有用的事情。 欲了解更多信息，请参阅 [mx 命令行工具](mx-command-line-tool)。

* Mono v5.20.x 或 .NET v4.7.2
