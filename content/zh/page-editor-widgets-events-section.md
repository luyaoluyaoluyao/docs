---
title: "活动部分"
parent: "页面编辑器部件"
menu_order: 70
description: "在 Mendix Studio 中描述部件属性中的事件部分。"
tags:
  - "工作室"
  - "页面编辑器"
  - "小部件"
  - "点击动作"
  - "事件"
---

## 1 导言

**事件** 部分是一个 **属性** 选项卡中常见于Mendix Studio 中的不同小部件中。 例如，静态图像、按钮、列表视图和数据视图。

在 **事件** 部分。 您可以设置 **点击动作** 小部件，并指定最终用户点击小部件时将执行什么操作。 例如，您可以指定当用户点击个人资料图片时，用户个人帐户的页面将会打开。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/events-section.png)
{{% /image_container %}}

## 2 点按动作 {#on-click-action}

您可以找到下面可能的点击操作的描述：

* [无](#do-nothing)
* [页](#show-page)
* [微流](#microflow)
* [呼叫工作流](#call-workflow)
* [显示工作流页面](#show-workflow-page)
* [显示任务页面](#show-task-page)
* [Complete Task](#complete-task)
* [保存更改](#save-changes)
* [取消更改](#cancel-changes)
* [关闭页面](#close-page)
* [登出](#sign-out)
* [打开链接](#open-link-action)
* [删除对象](#delete-object-action)

{{% alert type="info" %}}

可用的点击操作列表可能因部件而异。 例如， **删除对象** 在列表视图中不可用的点击动作。

{{% /报警 %}}

### 2.1 无 {#do-nothing}

没有采取任何行动。 此选项用于设置页面而不定义基本功能。

### 2.2 导 言 {#show-page}

**页面** 动作打开指定的页面。

以下属性是此操作的特定属性：

* **页面** - 一个 [页面应该打开](page-editor)

* **创建对象** - 创建一个新对象并传递到所选页面 (默认禁用)。 欲了解更多信息，请参阅下面 [创建对象选项](#create-object-option) 部分

#### 2.2.1 创建对象选项 {#create-object-option}

当您设置 **在点击操作** 为 **页面**时，您可以启用 **创建对象** 选项。 如果选中的页面需要上下文，您需要传递对象。

例如，您想要通过点击 **新的** 按钮来创建一个新客户。 此按钮将打开一个页面来填写新客户的详细信息并保存。 然而， *客户详细信息* 页面需要先获取数据。 换言之，它期望将对象 *客户* 传递给它。

{{% image_container width="350" %}}![数据视图期望客户对象](attachments/consistency-errors-pages/data-view-customer.png)
{{% /image_container %}}

因此，当将 **新的** 按钮的点击操作设置为 **页面**您需要启用 **创建对象** 选项并选择 **客户** 实体。

![](attachments/page-editor-widgets-events-section/create-object-example.png)

如果您启用 **创建对象** 选项，您需要设置以下选项：

* **页面** - 指定新创建对象的页面应该显示。 页面应该包含一个期望此对象的数据视图。
* **实体** - 指定哪个实体将被创建并传递到选定页面作为上下文的对象。

### 2.3 微流 {#microflow}

**微流程** 动作执行所选微流程。 **Microflow** 属性，允许您选择一个微流程，是此动作的特定属性。

### 2.4 呼叫工作流 {#call-workflow}

**调用 Workflow** 动作执行指定的工作流。

以下属性是此操作的特定属性：

* **Workflow** -- [Workflow](workflows) 应该执行。
* **关闭页面** - 指定当前页面是否应该关闭。
* **提交** - 指定在运行工作流程时是否应该提交对象。

### 2.5 显示工作流页面 {#show-workflow-page}

**显示工作流页面** 打开一个概览(管理员) 页面 此点动作的元素应该放置在连接到 **System.Workflow实例** 实体的数据容器中。

### 2.6 显示任务页面 {#show-task-page}

**Show Task Page** opens an overview page set for the [user task](workflows-user-task) in properties. 此点动作的元素应该放置在连接到 **System.WorkflowUserTask** 实体的数据容器中。

### 2.7 Complete Task {#complete-task}

**完整任务** 动作将工作流程中指定的用户任务标记为已完成。

以下属性是此操作的特定属性：

* **任务** -- [用户任务](workflows-user-task) 应该标记为已完成。

* **结果** - 列出选定的 [用户任务](workflows-user-task) 的结果并遵循选定的结果。 如果用户任务只有一个结果， **默认** 将设置为一个结果，不能编辑属性。

* **关闭页面** - 指定当前页面是否应该关闭。

* **提交** - 指定在将任务标记为完成时是否应该提交对象。

### 2.8 保存更改 {#save-changes}

**保存更改** 动作保存页面上的所有更改。

### 2.9 取消更改 {#cancel-changes}

**取消更改** 动作回滚页面上的所有更改。

### 2.10 关闭页面 {#close-page}

**关闭页面** 动作关闭一个弹出窗口(用于弹出页面)或导航到以前访问的页面。

### 2.11 注销 {#sign-out}

**退出** 动作标志当前已登录的最终用户离开应用程序。

### 2.12 打开链接操作 {#open-link-action}

**打开链接** 动作触发基于链接类型的动作：

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/open-link-action.png)
{{% /image_container %}}

以下属性是此操作的特定属性：

* **链接类型** - 指定链接执行的动作。 **链接类型** 的可能值如下：

  * **Web** — 导航到一个网站。

  * **电子邮件** — — 撰写一封电子邮件。

  * **电话呼叫** — — 开始一个电话。

  * **文本消息** - 发送文本消息。

    {{%alert type="info" %}}When you configure **Email**, **Phone Call** or **Message** options, the corresponding default app will be opened on the device when the action is triggered, for example, the default email client will be opened to compose a message.

    {{%/提醒 %}}

* **源** — — 取决于所选的链接类型，以及您是否想使用一个字数值或使用一个属性的值。 **源** 的可能值如下：

  * **使用字数值** - 您可以填写一个值 (指定 **Url** 为 **Web** **收件人** 收件人 **电子邮件**和 **电话号码** 电话号码 **电话号码**l 和 **信息**)。
  * **使用属性** - 如果您选择 **数据库**>**实体** 作为列表视图的数据源 您可以选择属于实体的字符串类型的属性，或者创建一个新的属性(当 **使用属性** 选项被配置时， 您无需手动填写任何信息，将动态更新)。

### 2.13 删除对象操作 {#delete-object-action}

**删除对象** 动作的行为取决于一个数据容器： [列表视图](page-editor-data-view-list-view#list-view-properties) 或 [数据视图](page-editor-data-view-list-view#data-view-properties)

#### 2.13.1 在清单中删去对象行动

如果您在列表视图中放置 **删除对象** 当用户点击按钮时，相应的列表视图项将被删除。

例如，您有一个显示客户名称列表视图的页面。 **删除** 按钮放在每个名称旁边的列表中。 因此，如果您单击 **删除** 行中的“Peter”，该客户和所有客户的详细信息将被删除。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/list-view-delete.png)
{{% /image_container %}}


#### 2.13.2 删除数据视图中的对象行动

放置在数据视图上后， **删除对象** 将会删除所连接的对象。 例如，您打开了一个包含客户详细信息的页面。 详细信息放在数据视图中。 您有 **保存** 和 **在页面底部删除** 按钮。 当您按 **删除**时，客户"John" 和客户的详细信息将被删除，页面将被关闭。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/data-view-delete.png)
{{% /image_container %}}

## 3 阅读更多

* [小部件](页面编辑器部件)
