---
title: "MxAssist性能机器人"
parent: "视图菜单"
menu_order: 50
description: "描述Mendix Studio Pro中的MxAssist性能箱。"
tags:
  - "studio pro"
  - "性能机器人"
  - mendix assistance”、“AI”、“assist”、“mx assist”
---

## 1 导言

MxAssist性能机器人是一个智能的虚拟合作开发者机器人，它通过在Mendix Studio Pro中检查您的应用模型来帮助您提高您应用的性能。 它在设计和开发过程中检测到反模式，将您指向这些反模式。 建议你如何解决它，并且在许多情况下可以自动解决这些问题。

MxAssist性能箱是利用对数千个匿名Mendix 应用软件的统计分析来建立的，目的是学习共同的反模式，并利用Mendix Expert Services 的最佳做法来发展微流量。 域模型、 页面、 安全等

它包括三级援助：

1. **检测** - 机器人检查模型，识别问题，并将您指向导致问题的文档/元素。
2. **建议** - 机器人解释了已确定的问题、潜在影响以及如何修复它。 还有一份详细的最佳做法指南，其中有一个关于如何解决这个问题的专门的逐步指南。
3. **自动修复** — 机器人可以自动实现最佳做法并解决问题。

## 2 MxAssist性能机器人面板

要访问 MxAssist性能箱的设置， 打开 **编辑** > **首选项** >一般 **标签页** 标签 >the **MxAssist性能箱** 标签。 欲了解更多信息，请参阅 [首选项](preferences-dialog)。

MxAssist性能箱默认启用，设计成一个窗格。 要访问 **MxAssist性能箱** 面板，点击 **查看** > **MxAssist性能箱。**

窗格提供了每个反模式的信息，包含MxAssist性能箱和配置：

![性能机器人面板](attachments/mx-assist-performance-bot/performance-bot-pane.png)

### 2.1 备选方案和配置

在 **MxAssist性能箱顶部** 窗格，您可以看到以下选项：

* **现在查看** — — 检查您的应用模型关于性能问题。

* **限于当前标签** - 将窗格中显示的消息限制为当前文档。

* **配置** — 定义MxAssist性能箱将分析的模块和文档。 点击 **配置** 按钮打开 **MxAssist性能箱配置** 包含 **项目模型的对话框** 和 **最佳做法** 选项卡。

    * **Project Model** 标签列出了您应用中所有相关的文档。 您可以选择要检查或离开的特定模块或文档。

        ![项目模型](attachments/mx-assist-performance-bot/project-model.jpg)

    * **最佳做法** 标签列出了可用的最佳做法。 您可以选择您喜欢的最佳做法，并查看您的模型：

        ![最佳做法](attachments/mx-assist-performance-bot/best-practice.jpg)

您可以同时使用应用模型和最佳做法配置。

### 2.2 反模式概览

窗格中的每条反模式线都为您提供了以下信息：

* **图标** -- 表示是否能自动修复反图案；如果图标有“A”字母，问题可以自动修复

* **代码** - 一个唯一专门针对反模式类型的代码

* **蓝圆** - 表示一个新检测到的反图案

* **消息** - 反图案描述/解释

* **元素** - 造成问题的元素

* **文档** - 包含元素的文档

* **模块** — — 包含文档的模块

    ![反模式概述](attachments/mx-assist-performance-bot/anti-pattern-overview.jpg)

右键点击窗格中反模式的消息行打开下拉菜单：

![下拉菜单](attachments/mx-assist-performance-bot/drop-down-menu.jpg)

下拉菜单中有以下操作：

* **转到原因** — — 带你到导致问题的元素。
* **转到使用** - 打开使用反模式的相应位置。
* **查看 MxAssist性能建议** - 打开弹出窗口并提供建议 (类似于双击消息)。
* **标记为已读** - 将问题标记为已读。 这将使蓝色圆消失了。
* **禁止此推荐** — — 抑制此问题。 这将使问题灰心，并将其发送到列表底部。 编辑中的相关指标将消失。

## 3 在应用程序开发中使用 MxAssist性能机器人

### 3.1 检测反模式 {#detecting}

第一级援助是 **检测** , 其中包括检查应用模型。 识别反模式，并指向您的文档。

要查看您的应用模型，请点击 **现在查看** 在 **MxAssist性能箱** 窗格。

{{% alert type="info" %}}

如果应用程序中出现一致性错误， **现在检查** 选项将被禁用。 在这种情况下，您需要先解决一致性错误。

{{% /报警 %}}

机器人将侦测性能反模式，并将其列在窗格中相关的反模式类型。 要了解更多关于每种反模式类型的信息，请单击反模式代码链接。 点击反模式类型旁边的加号图标来查看检测到的此类型的实例：

![查看反图案](attachments/mx-assist-performance-bot/viewing-anti-pattern.jpg)

要查看反模式所在的元素或文档， 双击消息行或右键单击消息行，并选择 **转到原因** 或 **转到下拉菜单中的用法**

### 3.2 建议修复 {#recommending}

第二级援助是 **建议** - 给您一个问题概述并建议如何解决它。

有两种观点看待这些建议：

1.  右键点击窗格上的反模式消息，并在下拉菜单中选择 **查看MxAssist性能建议**。

2. 在视觉编辑器中点击一个指示器来查看检测到的问题：

   ![编辑器中的指示器](attachments/mx-assist-performance-bot/indicator-in-editor.jpg)

该建议描述了已查明的问题、可能产生的影响。 解决该问题的方法，以及与解决问题的更详细指南的链接：

![业绩建议](attachments/mx-assist-performance-bot/performance-recommendation.jpg)

### 3.3. 自动修复反模式 {#auto-fixing}

第三级援助是 **自动修复** ，机器人可以自动执行最佳做法，只需点击一次即可解决这个问题。 避免不受欢迎的更改， 只有当机器人可以安全地重新计算代码，而不会在模型中造成错误或其他不受欢迎的更改时，自动修复才是可用的。 每个性能问题都有一个图标，表明它是否是自动修复的。 如果图标有“A”字母，问题可以自动解决：

{{% image_container width="45" %}}![自动固定图标](attachments/mx-assist-performance-bot/auto-fixable.png)
{{% /image_container %}}

要自动修复此问题，请按下面的步骤：

1. 右键单击窗格中的消息行，并在下拉菜单中选择 **查看MxAssist性能建议** 或点击编辑器中的相应指示器来打开建议。

2. 在 **MxAssist性能推荐** 弹出窗口中，单击可用的动作按钮。例如， **修复提交**：

    ![修复性能问题](attachments/mx-assist-performance-bot/fix-performance-issue.jpg)

在问题自动修复后，出现了一个弹出窗口，列出了变更。 您可以点击 **显示修复** 查看更改的文档和元素。

## 4 阅读更多

* [Mendix 助手](mx-assist-studio-pro)
* [MxAssist逻辑箱](mx-assist-logic-bot)
* [如何落实Mendix 最佳发展做法](/howto/general/dev-best-practices)
