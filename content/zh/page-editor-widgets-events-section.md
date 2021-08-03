---
title: "小部件中的事件部分"
parent: "页面编辑器部件"
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

在 **事件** 部分。 您可以设置 **点击操作** 小部件，并指定用户点击小部件时将执行哪些操作。 例如，您可以指定当用户点击个人资料图片时，用户个人帐户的页面将会打开。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/events-section.png)
{{% /image_container %}}

## 2 点按动作 {#on-click-action}

您可以在下面点击操作时找到可能的描述：

* **没有** - 用户点击小部件时不会采取任何行动
* **页面** - 指定的页面已打开
  * **创建对象** - 创建一个新对象并传递到所选页面 (默认禁用)。 欲了解更多信息，请参阅 [2.1 创建对象选项](#create-object-option)
* **微流** — — 所选微流已执行
* **更多** — — 包含以下类型的动作：
  * **保存更改** - 保存(提交) 页面上的所有更改
  * **取消更改** - 回滚页面上的所有更改
  * **关闭页面** - 关闭弹出窗口 (用于弹出页面) 或导航到先前访问的页面
  * **登出** - 当前用户已经退出应用程序
  * **打开链接** - 触发基于链接类型的动作(详情请参阅 [2.2 打开链接动作](#open-link-action)
  * **删除对象** - 删除对象(详细信息，见 [2.3 删除对象行动](#delete-object-action))

{{% alert type="info" %}}

点击操作可用列表可能因部件而异。 例如， **删除对象** 在列表视图中不可用的点击动作。

{{% /报警 %}}

### 2.1 创建对象选项 {#create-object-option}

当您设置 **在单击动作** 到 **打开页面**时，您可以启用 **创建对象** 选项。 如果选中的页面需要上下文，您需要传递对象。

让我们研究一个示例：你想通过点击 **新的** 按钮来创建一个新的客户。 此按钮将打开一个页面来填写新客户的详细信息并保存。 然而， *客户详细信息* 页面需要先获取数据。 换言之，它期望将对象 *客户* 传递给它。

{{% image_container width="350" %}}![数据视图期望客户对象](attachments/consistency-errors-pages/data-view-customer.png)
{{% /image_container %}}

因此，当将 **新的** 按钮的点击操作设置为 **页面**您需要启用 **创建对象** 选项并选择 **客户** 实体。

![](attachments/page-editor-widgets-events-section/create-object-example.png)

如果您启用 **创建对象** 选项，您需要设置以下选项：

* **页面** - 指定新创建的对象应该显示哪个页面。 页面应该包含一个期望此对象的数据视图。
* **实体** - 指定将创建哪个实体并将其作为上下文传到选定的页面。

### 2.2 打开链接行动 {#open-link-action}

当您设置 **单击动作** 到 **打开链接**时，有几个属性可用。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/open-link-action.png)
{{% /image_container %}}

见下表中的描述：

| 动作属性      | 描述                                                                                                                                                                                                                                                                                                                              |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Link Type | **链接类型** 的可能值如下： <ul><li>**Web** - 导航到一个网站</li><li>**电子邮件** - 撰写电子邮件</li><li>**Phone 通话** - 开始电话</li><li>**文本消息** - 发送文本消息</li></ul>                                                                                                                                                                                                                                                                                       |
| 来源        | **源** 的可能值如下： <ul><li>**使用字数值** - 您可以填写一个值 (指定**Url** 为 **Web**, **接收者** 为 **Email**, **Phone Number** 为 **Phone Cal**l 和 **Message**) </li><li>**使用属性** - 如果您选择 **Database**>**Entity** 作为列表视图的数据源。 您可以选择属于实体的字符串类型的属性，或者创建一个新的属性(在配置**使用属性**选项时) 您不需要手动填写任何信息，它将被动态更新)</li></ul>{{%alert type="info" %}}When you configure **Email**, **Phone Call** or **Message** options, the corresponding default app will be opened on the device when the action is triggered, for example, the default email client will be opened to compose a message.<br />{{%/alert %}} |

### 2.3 删除对象操作 {#delete-object-action}

**删除对象** 动作的行为取决于一个数据容器： [列表视图](page-editor-data-view-list-view#list-view-properties) 或 [数据视图](page-editor-data-view-list-view#data-view-properties)

#### 2.3.1 删除清单中的对象行动

如果您在列表视图中放置 **删除对象** 当用户点击按钮时，相应的列表视图项将被删除。

例如，您有一个显示客户名称列表视图的页面。 **删除** 按钮放在每个名称旁边的列表中。 因此，如果您单击 **删除** 行中的“Peter”，该客户和所有客户的详细信息将被删除。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/list-view-delete.png)
{{% /image_container %}}


#### 2.3.2 删除数据视图中的对象行动

放置在数据视图上后， **删除对象** 将会删除所连接的对象。 例如，您打开了一个包含客户详细信息的页面。 详细信息放在数据视图中。 您有 **保存** 和 **在页面底部删除** 按钮。 当您按 **删除**时，客户"John" 和客户的详细信息将被删除，页面将被关闭。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/data-view-delete.png)
{{% /image_container %}}

## 3 阅读更多

* [小部件](页面编辑器部件)
