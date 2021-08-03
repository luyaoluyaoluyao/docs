---
title: "系统要求"
category: "A. 概况"
menu_order: 10
description: "显示使用 Mendix 平台的系统要求。"
---

## 1 导言

本文件介绍Mendix Platform各部分的系统要求。

## 2 台式机模型

Mendix [桌面模组](desktop-modeler) 支持 Windows 7、8和10。 它支持32位和64位变量，但推荐64位变量。

以下框架已自动安装(如果需要的话)：

* Microsoft .NET Framework 4.6.2
* Microsoft Visual C++ 2010 SP1 可Redistributable 软件包
* Microsoft Visual C++ 2015 Redistributable 软件包( [Mendix 7.23)。 7](/releasenotes/studio-pro/7.23#72317) and above or Microsoft Visual C++ 2013 Redistributable Package (for [Mendix 7.23.16](/releasenotes/studio-pro/7.23#72316) and 下文)
* AdoptOpenJDK 8 (自动安装为 [Mendix 7.23).](/releasenotes/studio-pro/7.23#7233) 如果您没有安装这个或 Java Development Kit 1.8或Java Development Kit 1.8

{{% alert type="warning" %}}
您可以选择 JDK 通过 **编辑** > **首选项** 桌面模型中的菜单项来构建和在本地运行。
{{% /报警 %}}

如果您想要使用 TortoiseSVN 与桌面模式相结合，请从 [Sourceforge](http://sourceforge.net/projects/tortoisesvn/files/?source=navbar) 下载最新版本1.7.x。

## 3 个团队服务器

[团队服务器](team-server) 正在使用 Subversion, Moderr 使用HTTPS 协议与该服务器进行通信。 要从桌面模式中访问团队服务器，您所在位置的网络需要以下设置：

* HTTPS 端口 (TCP 443) 需要打开
* HTTP 端口 (TCP 80) 需要打开
* 需要在代理服务器上启用 WebDAV (HTTP 协议中的动词)

## 4 Web Modeler

[Mendix Web Moderr](/studio) 被优化用于谷歌Chrome。 虽然Chrome是官方支持的浏览器， 您也可以使用 Web Moderr 和其他受欢迎的浏览器，如Mozilla Firefox、Apple Safari和Microsoft Edge。

{{% alert type="info" %}}
您使用的浏览器需要打开 JavaScript 。
{{% /报警 %}}

## 5 个服务器

### 5.1 操作系统

* Microsoft Windows Server 2008 SP2 及以上
* Debian 8 (Jessie) 及以上
* Red Hat Enterprise Linux 6, Red Hat Enterprise Linux 7
* CentOS 6, CentOS 7

### 5.2 Web 服务器

* Microsoft Internet Information Services 7及以上
* Nginx (Debian Jessie 和 Debian Jessie Backports) 版本测试
* Apache

### 5.3 数据库服务器

* [IBM DB2](db2) 11.1, 11.5 for Linux, Unix, and Windows
* [MariaDB](mysql) 10.2, 10.3, 10.4, 10.5
* [Microsoft SQL Server](/developerportal/deploy/mendix-on-windows-microsoft-sql-server) 2017, 2019
* Azure SQL v12 (支持不是独立验证的，只能通过 SQL 服务器的兼容版本提供)
* [MySQL](mysql) 5.7, 8.0
* [Oracle 数据库](oracle) 12c Release 2, 19
* PostgreSQL 9.6, 10, 11, 12, 13
* [SAP HANA](saphana) 2.00.040.00.1545918182

### 5.4 Java

当在服务器上运行 Mendix 时，您将需要 Java Runtime 环境 (JRE) 8。 要从 AdoptOpenJDK 下载OpenJDK 分布，请参阅 [AdoptOpenJDK installation](https://adoptopenjdk.net/installation.html)。 若要下载商用Oracle分发，请参阅 [Java SE 下载](http://www.oracle.com/technetwork/java/javase/downloads/index.html)。

{{% alert type="info" %}}
从 Java 7 开始出现了一个问题，在使用一定数量的数据的 web 服务时导致超时。 您可以通过添加 VM 参数 `-Djava.net。首选IPv4Stack=true` 来绕开这个问题。 Mendix 桌面模组将为您做这件事。 但如果您在 Windows 服务器上的前提下运行 Mendix ，您将需要自己这样做。 关于此问题的更多信息，请参阅 [HotSpot (64位 server) 套接字挂卡(JVM 1.7 bug?) - 更新](http://blog.bielu.com/2011/11/hotspot-64bit-server-hangs-on-socket.html) 和 [Java 7 中可能出现的漏洞](https://forums.oracle.com/forums/thread.jspa?messageID=9985748)
{{% /报警 %}}

### 5.5 应用程序服务器

Jetty 被嵌入到 [Mendix Runtime](runtime)中，所以不需要应用程序服务器。

## 6 Browsers

### 6.1 桌面浏览器

* Google Chrome
* Mozilla Firefox
* 苹果 Safari
* Microsoft Edge
* Microsoft Internet Explorer 11

### 6.2 移动浏览器

* iOS 9及以上(Safari)
* Android 5.0 及以上版本
* Windows Phone 8 及以上版本

### 6.3 混合预览

使用混合预览与使用仿真器不同。 混合预览只显示一个应用的缩放视图，让人对该应用在移动设备上可能是什么样子。 此浏览器视图不支持一些混合应用功能。 完全测试总是需要在设备或仿真器上进行。 离线应用只能在 Google Chrome 中预览。

## 7 移动操作系统

对于Mendix 应用程序和 [Mendix 移动应用程序](getting-the-mendix-app)：

* iOS 9及以上
* Android 5.0 及以上版本

## 8 MxBuilding{#mxbuild}

MxBuild是一个 Windows 和 Linux 命令行工具，可用来构建Mendix 部署包。 查看 [MxBuild](mxbuild) 获取更多信息。

### 8.1 Mendix 版本 7.1 & 上

* Mono v4.6.x 或 .NET v4.6.2
* 8. JDK

### 8.2 Mendix 版本 7.0.2

* Mono v3.1.0 或 .NET v4.5
* JDK 8
