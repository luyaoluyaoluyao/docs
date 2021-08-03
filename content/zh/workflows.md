---
title: "工作流"
description: "描述Mendix Studio中的工作流。"
menu_order: 15
tags:
  - "工作流"
  - "工作流"
  - "工作室"
---

{{% alert type="warning" %}}
此功能在 Beta 中。 关于测试版产品的更多信息，请参阅 [Mendix Beta 功能](/releasenotes/beta-features/)。
{{% /报警 %}}

## 1 导言

Workflow 是 Mendix Studio 和 Mendix Studio Pro 中的一种视觉语言，它允许您解决涉及流程的业务问题。 它完全与其他视觉语言集成，如微流程编辑器和页面编辑器。

工作流和 [微流](microflows) 之间的主要区别是一个等候面——工作流被暂停，直到从最终用户获得输入。 例如， 员工发送旅行请求(触发工作流程的启动)，然后工作流程暂停，直到管理员点击按钮批准请求。

要在 Studio 中查看您的应用程序的工作流，请点击左侧菜单栏中的 **工作流** 图标：

![Workflow 图标](attachments/workflows/workflow-icon.jpg)

Workflow是你应用程序中处理逻辑的一种视觉方式。 工作流看起来像一个流程图。 在新的工作流中，默认情况下创建了 *起始事件* (工作流的起点) 和 *终结事件* (工作流的终点)。 You can add various activities to a flow of a workflow that is called a *path*.

![Workflow 示例](attachments/workflows/workflow-example.jpg)

## 2 个工作流应用模板

您可以使用 Workflow专用应用程序模板作为使用 Workflow的起点。 例如，您可以配置最终用户的审批请求表单，在此基础上创建应用程序。 它包含预配置的元素，例如仪表板、管理页面、仪表板和您此后可以自定义的工作流。 您可以在创建新应用时发现这些模板。

## 3 执行基本功能

您可以在工作流程中执行以下基本功能：

* [打开工作流](#open)
* [创建工作流](#create)
* [复制工作流](#duplicate)
* [复制并粘贴一个工作流程](#copy-paste)
* [删除工作流](#delete)
* [将元素添加到工作流](#add-elements)

### 3.1 开启工作流程 {#open}

若要在 Studio 中打开 Workflow ，请执行以下操作：

1. 点击左侧菜单栏中的工作流图标。

2. 在显示的工作流列表中，选择要打开的工作流，然后单击它：


已打开所选工作流。

### 3.2 添加工作流 {#create}

若要在 Studio 中添加一个 Workflow 到您的应用，请执行以下操作：

1. 点击左侧菜单栏中的工作流图标。

2. 选择您想要添加新工作流的模块，然后点击此模块旁边的加号图标：

    ![新建工作流](attachments/workflows/new-workflow.jpg)

    关于哪些模块的更多信息，见 [域模型](domain-models)。

3. 在 **中创建新的工作流** 对话框， 填写工作流名称并选择 Workflow 实体 (关于实体类型的更多信息) 查看 [实体及其类型](domain-models#entity-types) 章节在 *域模型* 中：

    ![创建新工作流](attachments/workflows/create-new-workflow.jpg)

4. 点击 **创建**。

工作流已创建。

### 3.3 复制工作流 {#duplicate}

要复制工作流，请执行以下操作：

1. 点击左侧菜单栏中的 **工作流** 图标。

2. 在侧面板中，单击椭圆图标并在下拉菜单中选择 **重复**

    ![复制工作流](attachments/workflows/duplicate.jpg)

工作流已重复。

### 3.4 复制并粘贴工作流 {#copy-paste}

若要复制和粘贴一个工作流，请执行以下操作：

1. 点击左侧菜单栏中的 **工作流** 图标。

2. 在侧面板中，单击椭圆图标并在下拉菜单中选择 **复制到剪贴板**：

    ![复制工作流](attachments/workflows/copy.jpg)

3. 打开工作室应用程序以粘贴工作流程并按 <kbd>Ctrl</kbd> +<kbd>V</kbd> 或 <kbd>Cmd</kbd> +<kbd>V</kbd>。

您的 Workflow 已粘贴。 欲了解工作室中复制/粘贴函数的更多信息，请参阅 [复制/粘贴工作流、页面、微流和枚举](general#copy-paste-documents) *常规信息* 中的部分内容。

### 3.5 删除工作流 {#delete}

若要删除工作室中的工作流，请执行以下操作之一：

1. 打开您想要删除的工作流，并按下面的步骤：
    1. 打开 **属性** 选项卡。
    2. 点击 **在 **属性底部删除**** 标签。
2. 点击左侧菜单栏中的工作流图标并执行以下操作：
    1. 在侧面板中，单击椭圆图标并在下拉菜单中选择 **删除**

所选工作流已删除。

### 3.6 在工作流中添加元素 {#add-elements}

若要在工作流中添加元素，请执行以下操作：

1. 打开 **工具箱** 标签页。
2. 选择要添加和拖放此元素到工作流路径。

已添加选中的元素。

## 4 工具箱元素

**工具箱** 标签包含您可以拖放到路径上的元素。 下面是所有要素的分类概述。 使用了下列章节：

* [A. 概况](#general)
* [用户操作](#user-actions)
* [系统操作](#system)

### 4.1 概况 {#general}

**常规** 部分中的元素帮助您控制工作流路径，例如添加并行路径或结束它们：

![一般部分](attachments/workflows/general.jpg)

本节的内容见下表：

| 元素                                                  | 描述                                                                                                                                                                                                        |
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 开始活动                                                | 工作流程的起始点。 工作流是由 [调用工作流](page-editor-widgets-events-section#call-workflow) 页面上的点击事件或 [工作流调用](microflows#microflow-workflow-activities) 微流中的动作触发的。 <br />点击开始事件打开 [Workflow 属性](workflow-properties)。 |
| [决 定](workflows-general-activities#decision)        | 根据一个条件做出选择，并且沿着一个唯一的一条出路。                                                                                                                                                                                 |
| [跳转活动](workflows-general-activities#jump)           | 允许您跳转到工作流中的其他活动。                                                                                                                                                                                          |
| [并联拆分](workflows-general-activities#parallel-split) | 添加两个或更多并行路径到您的工作流。                                                                                                                                                                                        |
| [结束活动](workflows-general-activities#end)            | 结束工作流的路径                                                                                                                                                                                                  |

### 4.2 用户动作 {#user-actions}

[用户任务](workflows-user-task) -- 工作流中的一个核心元素，允许您使用过滤器或微流将任务分配给某个用户或一组用户。

![用户动作](attachments/workflows/user-actions.jpg)

### 4.3 系统操作 {#system}

[调用微流](workflow-system-actions) 活动调用选定的微流。 您可以使用此活动将应用程序逻辑添加到不需要用户交互的工作流路径。

![系统操作](attachments/workflows/system-actions.jpg)

## 5 阅读更多

* [工作流属性](workflow-properties)