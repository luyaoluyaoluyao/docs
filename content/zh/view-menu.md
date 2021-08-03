---
title: "查看菜单"
parent: "menus"
description: "在Studio Pro中描述视图菜单。"
menu_order: 20
tags:
  - "Studio Pro"
  - "查看菜单"
  - "顶栏"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/view-menu.pdf)。
{{% /报警 %}}

## 1 导言

Studio Pro 支持一些可停靠的窗口面板，例如 **更改** 和 **错误** 个窗口。 您可以关闭一些窗格来显示您目前需要的窗格。 但您总是可以通过 **视图** 菜单重新打开它们。

通过此菜单，您也可以启用或禁用 [全屏模式](#full-screen) 或 [将您的项目的布局](#reset-layout) 重置为默认。

{{% image_container width="300" %}}![查看菜单](attachments/view-menu/view-menu.png)
{{% /image_container %}}

## 2面板布局 {#layout-of-panes}

您可以更改窗格的默认布局，并在您喜欢的布局中安排它们。

{{% alert type="info" %}}

请注意，本节描述窗格的行为，而不是工作区内文件的行为。 更多关于在工作区开放的文件行为的信息， 在 *Studio Pro Overview* 中查看 [文档标签](studio-pro-overview#documents) 部分。

{{% /报警 %}}

当你拖动一个窗格时，你可以看到指向你可以放置此窗格的箭头。 您可以将窗格放置在当前窗格内(分组在一起的箭头)，也可以使它成为全窗口高度或宽度(边框上的单个箭头)。 每个职位都贴上标签，解释如下：

![](attachments/view-menu/interaction-with-panes.png)

1. Within the current *pane* you can position a pane in one of the following ways:

   1. 面板高度 - 左侧

   2. 面板高度 - 右侧

   3. 面板高度 - 顶部

   4. 面板高度 - 底部

   5. 新窗格作为一个新标签页

      {{% alert type="info" %}}If you try to position the pane as a new pane inside the working area, it will be opened as a dialog box.

      {{% /报警 %}}

2. 在当前的 *窗口* 中，您可以通过以下方式之一设置一个窗格：

   1. 全窗口高度 - 左侧

   2. 全窗口高度 - 右侧

   3. 全窗口高度 - 顶部

   4. 全窗口高度 - 底部

下面的视频展示了如何放置窗格的例子：

<video width="640" height="360" controls src="attachments/view-menu/positioning-panes.mp4">视频</video> 如果你有几个面板组合在标签中，你可以通过拖动顶栏来一次改变所有标签的位置。 要更改单独标签的位置，请拖动标签本身。

## 3 个菜单项

**视图** 菜单中的菜单项在下面的部分中描述。

### 3.1 变化

对于版本控制启用的项目 (使用 [团队服务器](/developerportal/collaborate/team-server) 或其他 SVN 服务器的项目)， [更改窗格](changes-pane) 显示自上次提交以来应用程序的本地更改。 您可以提交更改，更新到最新版本，并从这里查看历史记录。

这个窗格有两个级别，所以当你缩放到一个更改的文档中。 您可以查看该文档中的所有更改，而不会在不同级别之间退出。 窗格的缩放级别分成两个网格，左侧的元素和右侧的属性。 在左边选择一个元素表示右边的更改属性：

![](attachments/view-menu/changes.gif)

### 3.2 连接器 {#connector}

**连接器** 窗格显示可以连接到当前选中元素的元素。 例如，当一个按钮被选中时， **连接器** 会显示微流，您可以拖动到按钮来连接它们。

### 3.3 数据中心 {#data-hub}

[数据枢纽窗格](data-hub-pane) 允许您浏览 [数据枢纽目录](/data-hub/data-hub-catalog) 并整合您的组织可用的注册数据源。 您可以通过此窗格将 [个外部实体](external-entities) 添加到您的应用中，并查看您项目中已经消耗的实体和服务。

### 3.3 控制台 {#console}

**控制台** 窗格在运行应用程序时显示 [Mendix Runtime](runtime) 的输出。

### 3.4 文件

**文档** 窗格显示当前选中元素的文档(如果适用)。

### 3.5 错误列表

[错误窗格](errors-pane) 显示 [错误](consistency-errors)警告和您的应用程序中存在的弃置状态。

### 3.6 查找结果 {#find}

此窗格显示最新的搜索结果。 您可以搜索文本，使用元素(例如属性)和未使用项目。

有两个 **查找结果** 窗格。 如果您锁定了第一个窗格的结果，第二个窗格将用于在您解锁第一个窗格之前查找操作。

### 3.7 项目浏览器

[Project Explorer](project-explorer) 窗格显示您应用的完整结构，包括模块中的所有文档。 默认情况下，活动文档总是被选中的，所以您可以快速地看到您正在编辑的文档位于树上。 您可以在 **编辑** > [首选项](preferences-dialog) 中更改此行为。

### 3.8 属性

**属性** 窗格显示当前选中元素的属性。 在工作室专业版进行大量编辑。

### 3.9 故事

对于 [团队服务器](/developerportal/collaborate/team-server) 应用， **故事** 窗格会显示当前 [故事](/developerportal/collaborate/stories) [Sprint](/developerportal/collaborate/planning-development)。 关于 **故事** 窗格以及如何与它互动的更多信息，请参阅 [故事面板](stories-pane)。

### 3.10 工具箱 {#toolbox}

**工具箱** 窗格显示可用于当前编辑器的工具。 例如，在一个页面中，您可以插入所有类型的部件 (例如) [数据小部件](data-widgets)) 通过将它们从 **工具箱** 拖动到您的页面。

### 3.11 调试窗口

关于调试的更多信息，请参阅 [如何调试微流](/howto8/monitoring-troubleshooting/debug-microflows)。

#### 3.1.1 断点

**断点** 窗格显示您应用中的所有断点。 您可以在此启用并禁用断点。

#### 3.11.2 调试器 {#debugger}

**调试器** 工具可用来调试您的应用程序。

#### 3.11.3 变量

在 **变量** 窗格中，您可以在调试您的应用程序时查看当前变量、列表和对象的值。

### 3.12 全屏 {#full-screen}

**全屏** 模式隐藏标题栏，让窗口填充整个屏幕。 此版本的 **完整屏幕** 已被介绍到Studio Pro [8.3。](/releasenotes/studio-pro/8.3#830); 在以前的版本中， **全屏** 模式关闭所有可停靠窗口窗口。 快捷键： <kbd>F11</kbd>

### 3.13 分散自由模式 {#distraction-free}

**无干扰模式** 做到与以上 **全屏** 模式相同，但也关闭了所有可停泊的窗口窗口。 这被引入Studio Pro [8.3.0](/releasenotes/studio-pro/8.3#830) 中。

快捷键： <kbd>Shift</kbd> + <kbd>F11</kbd>

### 3.14 重置布局 {#reset-layout}

将可停靠窗口面板的布局重置为出厂默认值。

## 4 阅读更多

* [更改面板](changes-pane)
* [Errors Pane](errors-pane)
* [项目浏览器](project-explorer)
* [Studio Pro Overview](studio-pro-overview)
