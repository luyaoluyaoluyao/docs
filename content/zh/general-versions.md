---
title: "工作室范围 & Mendix 版本"
category: "常规信息"
description: "描述工作室范围与Mendix 版本的关系。"
tags:
  - "工作室"
  - "studio pro"
  - "版本"
  - "版本"
  - "range"
---

## 1 导言

在 Mendix Studio中，每当有新的 Mendix 版本时，您将被提示升级到最新的 **Mendix 版本**。 接着，Studio有自己的版本，将自动升级(例如每天升级)。 本文档解释了这两个版本如何相互关联，以及你可以做些什么来使用Mendix Platform 以及Studio的最新功能。

**Mendix Studio 版本** 是工作室用户界面的构建数量。

**Mendix 版本** 是您正在编辑的应用程序的版本。 **Mendix 版本** 与 **Mendix Studio Pro 版本**相关，但更广泛， Mendix 版本是 Mendix Studio Pro 和 Mendix Runtime等整个平台的版本。

**Mendix Studio 版本** and **Mendix 版本** 可以通过点击工作室最上角的信息图标 > **** 查看。

{{% image_container width="500" %}}![](attachments/general-versions/about-dialog.png)
{{% /image_container %}}

## 2 工作室范围和Mendix 版本之间的关系

工作室支持 **Mendix 版本**。 例如，Studio支持Mendix 版本 7.15 - 7.22（包括所有次要版本和路径版本）为一个范围。 这意味着如果一个 *Studio Pro* 用户有一个 Mendix 7 应用程序。 5.3 版本，另一个版本为 Mendix 7。 2.0版本的用户工作室接口和功能看起来相同，因为它是一个工作室范围。

演播室引入了一个新的范围，因为模型中出现了突然的变化，使您的应用无法正常运行而无需升级。  出现突破性变化的一个例子是引入了新的功能。

## 3 升级到下一版本

*Studio 版本* 持续更新(甚至每天)，这将为您提供最新的用户界面功能来编辑您的应用程序。 您不需要任何操作，这些更新是自动完成的。 然而，当有新的 *Mendix 版本*显示橙色的顶栏，通知您您可以将您的应用程序升级到下一版本。

![](attachments/general-versions/top-bar-upgrade.png)

{{% alert type="info" %}}

从Mendix 7移动到Mendix 8时，工作室将不会提供自动升级。 Mendix 8包含的更改不能通过常规工作室升级机制自动升级。 欲了解更多信息，请参阅下面的 [升级到 Mendix 版本 8](#upgrade-to-8) 部分。

{{% /报警 %}}

这意味着当你升级时，你将整个应用程序升级到新的 Mendix 版本。 Mendix 版本包含 Mendix Studio Pro 版本， 这也意味着您或您的团队成员需要安装和使用Studio Pro 的新版本。

当你看到升级通知时， 您可以继续使用当前版本并继续工作 (尽管您可能没有最新的 Mendix 平台功能和改进) 或者您可以升级到最新版本。 当你升级时，你将自动升级到可能的最新版本，即使它处于新的工作室范围。

{{% alert type="info" %}}

Studio 有一个最小支持的 Mendix Studio 版本。 这意味着，如果您的应用程序版本低于支持的最低版本，那么升级是强制性的； 否则，您将无法在工作室中使用您的应用程序。

{{% /报警 %}}

下表举例说明Mendix 版本如何与Studio范围相关联。 如果您选择升级，您的应用程序将升级到哪个版本：

| Mendix 版本示例 | 工作室范围     | Mendix 版本将在点击升级时升级到:                                                 |
| ----------- | --------- | -------------------------------------------------------------------- |
| 7.11.0      | 7.11–7.14 | 7.23.14                                                              |
| 7.15.1      | 7.15–7.22 | 7.23.14                                                              |
| 7.22.2      | 7.15–7.22 | 7.23.14                                                              |
| 7.23.0      | 7.23      | 7.23.14                                                              |
| 7.23.7      | 7.23      | 没有自动升级，只有手动升级到 Mendix 8。 详情见下面的 [升级到 Mendix 版本 8](#upgrade-to-8) 部分。 |
| 8.0.0       | 8.0–8.6   | 8.6.4                                                                |
| 8.7.0       | 8.7 & 上   | 最新可用版本的 Mendix 8。                                                    |

{{% alert type="warning" %}}

升级到最新版本后，您不能恢复升级。 此外，任何使用Studio Pro 在应用上工作的人都必须从那时起使用Studio Pro 的新版本。

{{% /报警 %}}

### 3.1 升级到Mendix 8版 {#upgrade-to-8}

Mendix 版本 8 为平台带来了许多改进，并为Mendix 开发者打开了新的应用程序构建能力。 然而，这个版本包含的更改不能通过正常的工作室升级机制自动升级。

这意味着：

* 在 Studio 中构建的现有应用将保留在最新版本的 Mendix 版本 7.23 上。
* 在Studio中新创建的应用程序将从一开始就有 Mendix 版本 8

从Mendix 7移动到Mendix 8时，工作室将不会提供自动升级。 因此，想要将他们的 Studio 应用程序升级到 Mendix 版本 8 的开发者只能在 Studio Pro 中这样做，或者让熟悉Studio Pro的开发者参与进来。 关于使用 Studio Pro的升级应用的更多信息，请参阅 [从桌面Moderr 版本 7 移动到 Studio Pro 8](/refguide8/moving-from-7-to-8)。

### 3.2 推迟升级到下一版

商业方面和信息技术方面想要同时利用Studio 和Studio Pro 在同一应用程序上进行合作的用户可能不想立即升级(例如) 因为升级Studio Pro 可能需要稍后才能实现)。 此外，可能还制定了批准软件升级的具体公司政策。

我们鼓励用户尽快升级到 Mendix Studio Pro 新版本， 在许多情况下，可以推迟升级。 即使您正在编辑一个未升级到最新Mendix 版本的应用， 当您在Studio中打开此应用程序时，将自动加载旧版本的Studio。

## 4 阅读更多

* [Studio 发布笔记](/releasenotes/studio)
* [Studio Pro 发布笔记](/releasenotes/studio-pro)
