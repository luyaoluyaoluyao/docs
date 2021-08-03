---
title: "工作流"
parent: "应用逻辑："
menu_order: 20
tags:
  - "工作流"
  - "工作流"
  - "Studio Pro"
---

{{% alert type="warning" %}}
此功能在 Beta 中。 关于测试版产品的更多信息，请参阅 [Mendix Beta 功能](/releasenotes/beta-features/)。
{{% /报警 %}}

## 1 导言

Workflow 是 Mendix Studio 和 Studio Pro 中的一种视觉语言，它允许您构建可扩展的流程。 它完全与其他视觉语言集成，如微流程编辑器和页面编辑器。

## 2 工作流元素

一个工作流由你可以拖放到路径上的元素组成。 下面是所有要素的分类概述。 使用了以下类别：

* [A. 概况](#general)
* [用户任务](#user-tasks)
* [系统操作](#system)

### 2.1 概况 {#general}

一般类别中的元素帮助您控制工作流路径，例如添加并行路径或结束它们。

下表说明了这一类别的各项要素：

| 图形                                                | 元素                           | 描述                                                                                                                                                         |
| ------------------------------------------------- | ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![开始事件](attachments/workflows/start-event.png)    | 开始活动                         | 工作流程的起始点。 工作流是由 [调用工作流](on-click-event#call-workflow) 页面上的点击事件或 [工作流调用](workflow-call) 微流中的动作触发的。 <br />点击开始事件打开 [Workflow 属性](workflow-properties)。 |
| ![决 定](attachments/workflows/decision.png)        | [决 定](decision-in-workflows) | 根据一个条件做出选择，并且沿着一个唯一的一条出路。                                                                                                                                  |
| ![并联拆分](attachments/workflows/parallel-split.png) | [并联拆分](parallel-split)       | 添加两个并联路径到您的工作流。                                                                                                                                            |
| ![跳转活动](attachments/workflows/jump.png)           | [跳转](jump-activity)          | 允许您跳转到工作流中的其他活动。                                                                                                                                           |
| ![结束事件](attachments/workflows/end-event.png)      | 结束事件                         | 结束工作流的路径                                                                                                                                                   |

{{% alert type="info" %}}
如果您在微流中使用 **作为工作流操作** 设置，您可以添加自定义的活动到这个部分。 欲了解更多信息，请参阅 *Microflow Properties* 中的 [显示为 Workflow 操作](microflow#expose-as-workflow-action) 部分。
{{% /报警 %}}

### 2.2 用户任务 {#user-tasks}

[用户任务](user-task) -- 工作流中的一个核心元素，允许您使用过滤器或微流将任务分配给某个用户或一组用户。

![用户任务](attachments/workflows/user-task.png)

### 2.3 系统操作 {#system}

[调用微流](call-microflow) 活动调用选定的微流。

![调用微流](attachments/workflows/call-microflow.png)

## 3 执行基本功能

您可以在工作流程中执行以下基本功能：

* 打开工作流
* 创建工作流
* 删除工作流
* 将元素添加到工作流
* 查看元素属性

### 3.1 开启工作流程

若要在 Studio Pro中打开工作流，请执行以下操作：

1. 在 [Project Explorer](project-explorer)中，打开此工作流所在的模块。
2. 浏览到模块内的工作流位置，双击工作流。

已打开所选工作流。

### 3.2 添加工作流

若要将工作流添加到您的应用，请执行以下操作：

1. 在 [工程资源管理器](project-explorer)， 右键单击模块或您想要创建页面的文件夹，并选择 **添加工作流**：

    ![添加工作流](attachments/workflows/add-workflow.jpg)

2. 在 **添加 Workflow** 对话框，填写名字并点击 **确定**：

    ![添加工作流](attachments/workflows/add-workflow-dialog.jpg)

工作流已创建。

### 3.3 删除工作流

若要删除工作流，请执行以下操作：

1. 在 [工程资源管理器](project-explorer)中，选择一个您想要删除的工作流并右键单击它。
2. 在显示的列表中，点击 **删除** 并通过点击 **删除弹出对话框中的** 来确认您的选择。

所选工作流已删除。

### 3.4 将元素添加到工作流

若要在工作流中添加元素，请执行以下操作：

1. 打开 **工具箱**。
2. 选择一个要添加和拖放此元素的元素到工作区域。

已添加选中的元素。

### 3.5 视图元素属性

要查看某个元素的特性，请执行以下之一：

1. 选择一个元素并打开 **属性** 窗格以查看其属性。
2. Right-click an element and select **Properties** from the list of options that opens.
3. 双击一个元素。

## 4 系统模块中的工作流实体 {#workflow-entities}

您的应用系统模块中有几个与工作流程相关的实体，其中一些可以在 XPath 和表达式中使用。 有些实体仅仅是内部实体（例如，Runtime）。

您可以在系统模块中找到以下与工作流程相关的实体：

* **工作流程定义** -- 表示您的工作流程在数据库中。 它包含两个属性， **名称** and **标题** 是 **名称** 和 **标题** workflow 的属性 **过时的** 是一个布尔值，当您删除您的工作流时标记为 true。 在这种情况下，工作流仍然停留在数据库中(您仍然能够与它一起创建报告), 但Mendix 标记不再存在。 欲了解更多关于属性的信息，请参阅 [Workflow 属性](workflow-properties)。
* **WorkflowTaskDefine** — 表示您 [的用户任务](user-task) 和 [系统活动](call-microflow) 在数据库中。 它包含两个属性， 其中 **name** 是一个 **名称** 用户任务或系统活动的属性， 和 **过时的** 是一个布尔值，当您从工作流中删除用户任务/系统活动时标记为 true。 他们仍然留在数据库中(您仍然能够与他们一起创建报告), 但Mendix 标记不再存在。
* **Workflow实例** - 一个运行中的工作流程的代表，因此每次开始新的工作流程时，Runtime 就会创建一个新的实例。
* **WorkflowTaskInstance** — — 表示正在运行的用户任务或系统活动 每当新用户任务/系统活动开始时，运行时间创建一个新的实例。
* **WorkflowUserTask** - 专业化 **WorkflowTaskInstance** 此实体是在运行时执行用户任务和最终用户选择一个动作时创建的(例如) 点击 **批准** 按钮来批准请求)。 此实体可以用于工作流程概览页面和应用程序逻辑。
* **WorkflowSystemTaskExtask** - 专业化 **WorkflowTaskInstance** 此实体是在 Runtime 执行系统活动 (**调用 microflow**)时创建的，用于显示微流程已被执行。
* **WorkflowContext** — — 将被用作工作流程上下文的对象的基本实体。 这个实体的专业化被用作属性中的 **工作流实体**。 欲了解更多关于属性的信息，请参阅 [Workflow 属性](workflow-properties)。
* **Workflow版本** — 这个系统实体用于版本控制和运行时的内部管理。 当您添加活动并运行您的工作流时，将创建一个新版本。

## 5 工作流变量

工作流具有专用变量，可以在 Workflow 编辑器内使用 XPath 和表达式。

以下是变量清单：

* `$workflowData` - 一个为特定工作流配置的工作流实体实例(通常是 **System.WorkflowContext**)
* `$workflow` — 一个当前正在运行工作流程的实例(**System.Workflow实例**)

欲了解系统模块中与工作流相关的实体的更多信息，请参阅上面系统模块</a> 部分中的
工作流实体。 </p> 

例如，您可以在 **任务名称** 和 **任务描述** 中使用这些变量作为参数。 欲了解更多信息，请参阅 [用户任务](user-task)。 



## 6 微流中针对具体工作流程的活动

您可以将与工作流程相关的活动添加到您的微流中。 关于这些活动的更多信息，请参阅 [工作流活动](workflow-activities)。 



## 7 页面上的工作流程特定单击事件

您可以通过在小部件上配置的特定点击事件，从页面触发工作流或用户任务。 For more details, see [On Click Event & Events Section](on-click-event).



## 8 工作流共用模块

**工作流共享** 模块是一个针对工作流的模块，它具有预先配置的页面模板、页面、仪表板等。 在开发过程中，它可以节省很多时间。 您可以从应用市场下载，也可以在开发者门户创建新应用时使用一个应用模板。 这些模板已经包含 **工作流共享** 模块。

关于如何在现有应用中配置 **工作流共享** 的更多信息， 参见 [将工作流程添加到现有应用程序：设置基础版](/refguide/workflow-setting-up-app)。



## 9 阅读更多

* [如何配置工作室专业版员工上岗流程的工作流](/howto/logic-business-rules/workflow-how-to-configure)
* [将工作流添加到现有应用程序：设置基础知识](/refguide/workflow-setting-up-app)