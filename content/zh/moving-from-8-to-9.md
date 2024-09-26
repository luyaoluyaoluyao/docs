---
title: "从 Mendix Studio Pro 移动到 9"
category: "常规信息"
menu_order: 20
description: "提供关于从Mendix 8升级到Mendix 9的应用程序的详细信息，包括关于转换您的应用程序和废弃功能的章节。"
tags:
  - "studio pro"
  - "工作室"
---

## 1 导言

Mendix Studio Pro 9 和 Mendix Studio 9为您提供了强大的新工具来增强您的应用。 关于更改的完整清单，见Studio Pro 9和Studio 9发布说明。 如果您想要将现有的Studio Pro 8或Studio 8应用升级到其各自的9个版本，请检查下面的信息：

* 如果您正在将工作室中的应用程序从 Mendix 8 升级到 9, 请参阅下面的 [从 Mendix 8 升级到 9 版本的 Studio](#studio-upgrade)。
* 如果您正在将您的应用从 Studio Pro 8 转换为 Studio Pro 9, 查看 [在升级到Studio Pro 9](#studio-pro-upgrade) 之前更改您的应用。

## 2 从 Mendix 8 升级到 9 for Studio {#studio-upgrade}

### 2.1 为MS SQL服务器打开 RCSI

为了提高业绩和减少陷入僵局的机会， Mendix 9 要求使用 **读取提交的快照隔离** (RCSI) 开启 ****

在同步阶段， Mendix 9 将对RCSI 状态进行检查，如果不是 **** 并且数据库用户缺乏自动进行检查的必要权限，可能会中止该进程。

## Studio Pro 的 Mendix 8 到 9 更新 {#studio-pro-upgrade}

以下小节解释了将您的应用程序从 Mendix 8 转换为 Mendix 9 所采取的步骤。 我们建议您首先审阅 *Studio Pro 9的 [打破更改](/releasenotes/studio-pro/9.0#breaking-changes) 部分。* 发行说明以及我们更新的 [系统要求](/refguide/system-requirements)

### 3.1 备份您的应用

请确保您已经向团队服务器提交了您的最新更改， 或在您开始转换之前创建本地应用程序的备份。

### 3.2 升级到最新版本8

{{% alert type="warning" %}}
升级到Mendix 8.12技术需要您先更新到Mendix 9。 然而，我们建议您更新到最新版本的 Mendix 8： [8.18](/releasenotes/studio-pro/8.18)
{{% /报警 %}}

要升级到 Mendix 8.18，请遵循以下步骤：

1. 下载Studio Pro 最新版补丁 [8.18](/releasenotes/studio-pro/8.18)
1. 在 Studio Pro v8.18 中打开您的应用程序。
1. 允许它在必要时升级应用程序。

### 3.3 审查您的 Mendix 8 应用程序

在升级到Mendix 9之前，请结合下面的章节审查您的应用，并评估是否需要采取进一步行动。

您应该运行您的应用，测试所有功能，并确保它正常工作。 如果你的应用使用应用服务，你应该在升级之前先删除它们，因为应用服务已经在 Mendix 9 中被废弃。

您还应该修复在Studio Pro开发中看到的任何折旧警告， 以及在运行时使用您的控制台和浏览器控制台。

### 3.4 保存你的版本 8 App

备份或提交您的应用，以便您可以在必要时返回它。

您的应用已准备好升级到 Mendix 9。 您现在可以关闭Studio Pro 8中的应用程序。

### 3.5 将您的应用程序升级到第9版

在 Studio Pro 9 中打开您的应用，并允许Studio Pro 将您的应用更新到9版。 Mendix 将自动升级您的应用程序。

审查所有错误消息和关于废弃项目的消息，并在必要时做出修改。

### 3.6 升级所有小部件和模块 {#upgrade-widgets}

为了尽量减少出现问题的可能性，您应该更新您的应用程序使用的所有小部件和其他应用市场模块到最新版本。

检查是否有更新版本的模块在应用商城。 读取市场版本发布笔记，查看升级时是否需要执行特定操作。

请务必更新这些关键部件、资源和动作：

* [原生移动资源](https://marketplace.mendix.com/link/component/109513)
* [Nanoflow Commons](https://marketplace.mendix.com/link/component/109515)
* [数据网格 2](https://marketplace.mendix.com/link/component/116540)

一般而言，您不应删除和重新导入模块，除非在发行说明中推荐这样做。 如果您确实删除并重新导入它们，您可能会丢失与模块相关的数据或配置。

### 3.7 更新Atlas模块(可选)

Mendix 9 带有一个新的Atlas主题，包括新的页面模板和构建块。 要获取此主题，您可以下载 [Atlas核心](https://marketplace.mendix.com/link/component/117187)， [Atlas Web内容](https://marketplace.mendix.com/link/component/117183) 和 [Atlas Native Content](https://marketplace.mendix.com/link/component/117175) 来自市场的模块包。

### 3.8 审核和测试您的应用

最后，查看下面的章节，并确保您已经做出了所有必要的更改。 测试任何意外的结果。

{{% alert type="success" %}}
恭喜！ 您的应用已成功升级到 Mendix 9，您可以继续正常工作。
{{% /报警 %}}

## 4 运行时 API 更改

Mendix 8中已废弃的 Java API调用已被删除。 如果您仍然在 Java 操作中使用这种方法，您必须替换或删除它们。 To check which calls were depreciated, click the **Mendix 8 Server Runtime API** link in our [Runtime API Documentation](/apidocs-mxsdk/apidocs/runtime-api).

此外，Mendix Studio Pro 9.02 发布说明以获取更多的 Runtime API 更改详情。

### 4.1 数据库统一性的变化

Mendix 9之前，Mendix 可以使用Mendix 运行时间或依靠数据库引擎本身来确保数据的唯一性。 从 Mendix 9 开始， **数据库** 将是唯一的选项。

如果您的应用仍在使用 Mendix 运行时间进行唯一性验证，那么您应该设置自定义运行时间设置 `数据存储。 线性诊断` to `true`  以检查数据库中可能存在的数据冗余问题。

如果发现任何错误，如 **在初始化运行时间时发生错误：检测到的唯一约束违反...** 将被记录。 要解决这个问题，您的应用必须先准备才能移动到Mendix 9。 您可以通过 [提交支持请求](/developerportal/support/submit-support-request) 获取您所需要的工具。

## 5 测试本地移动应用

要在 Mendix 9 中测试和预览本机移动应用，您必须下载 Mendix 9 版本的 Make it 本地应用：

* 在 [Google Play 商店下载 Android Native 9](https://play.google.com/store/apps/details?id=com.mendix.developerapp.mx9)
* 在 [苹果应用商店下载 iOS 的 Native 9](https://apps.apple.com/nl/app/make-it-native/id1542182000)

对于本机应用的最佳结果， 请确保您更新了 [中所述的 [原生移动资源](https://marketplace.mendix.com/link/component/109513) 模块。升级所有小部件和模块](#upgrade-widgets) 上面的部分。

## 6 个客户端 API 更改

在 Mendix 9 中被弃用并标记去除的客户端 API确实已被删除。 像 `一样大的书库。 s`, `response`, `react-norig-inal`, 另外几个带有客户端的货运已更新到最新版本。 这可能会影响您的自定义和可插件以及JavaScript操作。 详情请参阅 *Studio Pro 9.0* 版本说明中的 [打破更改](/releasenotes/studio-pro/9.0#breaking-changes) 部分。

## 7 本机依赖关系

Mendix 9 本地应用不再包含非必要的本地库，如 `react-native-map`， `react-native-ble-plx`, `react-native-geocoder`, 和其他默认。 相反，Mendix 9中引入了新功能，可以申报组件的本地依赖性。 每个插件或 JavaScript 操作都必须声明它使用的本地库。 这样一来，本地应用只能与他们所需要的库捆绑起来，而不包括不必要的库。

如果您的插件或 JavaScript 动作使用需要本地链接的库， 请更新您的部件和操作，以便将这些本地库定义为您组件的依赖项。 在 [声明本地依赖关系](/apidocs-mxsdk/apidocs/pluggable-widgets-native-dependencies) 中阅读更多关于本地依赖关系的信息。

## 8 XPath 查询引擎 9 {#query-engine-9}

Mendix 9 contains a new XPath query engine called *query engine 9* or QE9, replacing the current engine called *query engine 7* or QE7. 查询引擎之间的功能有一些变化：

* 如果一个关联是 [可以从两边导航](/refguide/association-properties#navigability), 两个实体都可以定义访问规则来声明该关联的可读性。 对于这类协会，QE9将始终使用当前XPath 左侧的实体来确定可访问性。 例如：在查询 `//Customer[Customer_Address/City = '鹿特丹']`, 客户 `中定义的访问规则` 将用于关联， 在 `/ Address[Customer_Address/Customer/Lastname = 'Doe']`中， `地址` 中的规则将用于同一关联。 在 QE7 中，行为定义不明确。

* QE9是为了在检索数据时严格遵循最少权限原则而写的。 这可能导致最终用户更少地看到数据。

* Studio Pro不允许，但可以在 Java 操作中使用非布尔值属性作为约束 例如 `/地址[City]` QE7 接受这种查询，但是根据数据库，可能会产生意外结果。 QE9将拒绝这种查询。

* 虽然不支持或文档，但可以在 Java 操作中使用类似 `//Customer/Customer_Address/ Address` 的查询。 If an instance of `Address` is reachable from multiple `Customer` instances, QE7 would return the instance of `Address` multiple times. QE9将只返回每个匹配的实例 `地址`。

## 9 阅读更多

* [Studio Pro 9 发布笔记](/releasenotes/studio-pro/9.0)