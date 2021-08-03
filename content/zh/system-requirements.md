---
title: "系统要求"
category: "常规信息"
menu_order: 10
description: "显示使用 Mendix 平台的系统要求。"
tags:
  - "studio pro"
---

## 1 导言

本文件介绍Mendix Platform各部分的系统要求。

## 2 Mendix Studio Pro {#sp}

Mendix [Studio Pro](modeling) 版本 9 在 Windows 10 版本1809 及以上的 64 位版本上支持。 Studio Pro 不在 Apple Silicon Mac(例如M1)上运行Windows仿真器，或任何其他基于ARM的机器。

以下框架已自动安装(如果需要的话)：

* Microsoft .NET Framework 4.7.2和所有适用的 Windows 安全补丁
* Microsoft Visual C++ 2010 SP1 可Redistributable 软件包
* Microsoft Visual C++ 2015 Redistributable 软件包
* 采用OpenJDK 11 或 Oracle JDK 11 (自动安装前者) 如果您没有安装任何JDK 11

{{% alert type="info" %}}
您可以选择 JDK 通过 **编辑** > **在 Studio Pro中使用** 菜单项来构建和在本地运行。
{{% /报警 %}}

{{% alert type="warning" %}}
请注意数据库查看器嵌入Studio Pro 中的限制(如 [如何共享开发数据库](/howto/collaboration-requirements-management/sharing-the-development-database)) 与 JDK 11不兼容。 6 或 11.07。
{{% /报警 %}}

### 2.1 防火墙设置

Studio Pro 需要访问以下URL才能工作。 如果您的防火墙目前正在屏蔽它们，您需要将它们加入白名单。

* `*.mendix.com`
* `*.mendixcloud.com`
* `*.teamserver.sprintr.com`

### 2.2 TortoiseSVN

如果您想要使用 TortoiseSVN 与 Studio Pro，请从 [TortoiseSVN](https://tortoisesvn.net/) 网站下载最新版本。

{{% alert type="warning" %}}
Mendix Studio Pro 使用 Subversion 1.9 的工作副本。 Mendix 桌面Modeler使用了一个 Subversion 1.7 工作副本。 这些工作副本版本 **不兼容**。<br />
<br />
总是使用 TortoiseSVN 版本来匹配您的应用模型。 如果您从 Mendix 版本 7.x 或6 打开本地模型。 使用最新版本的 TortoiseSVN **您将无法在 Mendix** 中打开它。
{{% /报警 %}}

### 2.3 文件位置

对于活跃的开发和本地运行您的应用程序， 您的应用文件夹应该在本地驱动器 (例如C:) 上或已映射到 [Windows 驱动器](https://support.microsoft.com/en-us/windows/map-a-network-drive-in-windows-10-29ce55d1-34e3-a7e2-4801-131475f9557d) 的网络文件夹上。

### 2.4 支持的 Git 服务商 {#supported-providers}

#### 2.4.1 Azure仓库和Azure DevOps 服务器

我们支持Microsoft的 [Azure 仓库](https://azure.microsoft.com/en-us/services/devops/repos/) 托管Git 服务。 和 Azure DevOps 服务器 (原团队基金会服务器) 是托管您关于私人基础设施的Git仓库的房间解决方案。

To get a PAT for your user account, see the [Use personal access tokens](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page) instructions in the Microsoft documentation.

您需要 `代码 (满)` 权限才能获取您的令牌。

##### 2.4.2 GitHub

我们支持GitHub 的托管解决方案，包括免费的GitHub .com云托管服务和GitHub 企业，两者都是托管的(Enterprise Cloud)和房间(Enterprise Server)。

若要为您的用户帐户获取PAT，请在 GitHub 文档中查看 [创建个人访问令牌](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token) 说明。

你需要 `repo` 权限来获取你的令牌。

##### 2.4.3 GitLab

我们支持GitLab的所有层级服务，包括GitLab.com、GitLab 社区版和GitLab 企业版。

若要为您的用户帐户获取PAT ，请在 GitLab 文档中查看 [个人访问令牌](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) 说明。

您需要 `写入仓库` 权限来获取令牌。

##### 2.4.4 BitBucket

我们支持Atlassian所有等级的 BitBucket 服务，包括BitBucket.org、BitBucket Server 和 BitBucket 数据中心的房产解决方案。

在 BitBucket.org 上，个人访问令牌叫做应用密码。

为您的 BitBucket.org 账户设置应用密码，请参阅 [应用密码](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/) 说明。

另一方面，BitBucket 服务器和 BitBucket 数据中心仍然使用个人访问令牌这一术语。 要设置个人访问令牌，请参阅 [个人访问令牌](https://confluence.atlassian.com/bitbucketserver/personal-access-tokens-939515499.html) 说明。

在这两种情况下，您都需要 `存储库写入` 权限。

##### 2.4.5 AWS CodeCommit限制

我们在 Git Technology Preview for Studio Pro中具有与 AWS CodeCommit 兼容性限制。

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
* Red Hat OpenShift v3.11 和 v4.2及以上

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

### 7.3 Java {#java}

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
每个应用必须有自己的数据库。 Mendix 应用无法通过共享相同的数据库共享数据。

如果你想要两个应用共享同一个数据库，你需要使用API分享一个应用到另一个应用的数据。 在 Mendix 中，这些都由 [Data Hub](/data-hub/share-data/) 或 [集成中描述的REST 和 OData 服务](integration) *Studio Pro Guide* 的章节提供支持。 这被称为 *微服务* 架构。

关于为什么不能在应用之间共享数据的更多信息，请参阅 [数据存储](data-storage#databases)。 如果您需要将数据从一个应用复制到另一个应用，请使用 [数据库复制](/appstore/modules/database-replication) 模块。
{{% /报警 %}}

## 9 个文件存储 {#file-storage}

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

{{% alert type="warning" %}}
Studio Pro 9不再支持 Internet Explorer。 由于市场正在脱离互联网资源管理器和Mendix 继续与现代网络生态系统的最佳做法相一致， 我们已经放弃了对 Internet Explorer 11 的支持。 这使我们能够符合用户的期望。 删除支持已经改善了应用加载时间和性能，它将使我们能够继续改进和使用现代Web功能进行创新。<br />
<br />
Studio Pro 9, 仍在使用IE的应用最终用户将会显示一个 **不支持的浏览器** 信息，指出需要升级到现代浏览器。 You can [customize this message](/howto/front-end/customize-styling-new#customize-unsupported-browsers) to meet your needs.<br />
<br />
如果您仍然需要支持 IE11，注意Studio Pro [8](/releasenotes/studio-pro/8.18) and [7](/releasenotes/studio-pro/7.23) 将继续支持 IE11。 Mendix 推荐使用 Studio Pro 8 或 7 直到您的应用程序最终用户升级了他们的浏览器。
{{% /报警 %}}

## 11 移动操作系统 {#mobileos}

对于Mendix 本地应用，混合应用和 Mendix 移动应用，支持以下操作系统：

* 最新两个主要版本的 iOS
* Android 5.0 及以上版本

### 11.1 混合应用预览

使用混合预览功能与在手机或模拟器上测试应用程序不同。 混合预览只显示一个应用的缩放视图，让人对该应用在移动设备上可能是什么样子。 此浏览器视图不支持一些混合应用功能。 完全测试总是需要在设备或仿真器上进行。 离线应用只能在 Google Chrome 中预览。

混合应用不能仅在真正设备上在 Android Emulator 上测试。

## 12 MxBuilding {#mxbuild}

MxBuild是一个 Windows 和 Linux 命令行工具，可用来构建Mendix 部署包。 欲了解更多信息，请参阅 [MxBuild](mxbuild)。

* Mono v5.20.x 或 .NET v4.7.2
* JDK 11

## 13 mx 命令行工具 {#mxtool}

**mx** command-line 工具是一个 Windows 和 Linux 命令行工具，可用来在您的 Mendix 应用程序中做有用的事情。 欲了解更多信息，请参阅 [mx 命令行工具](mx-command-line-tool)。

* Mono v5.20.x 或 .NET v4.7.2
