---
title: "按钮"
parent: "页面编辑器部件"
description: "在 Mendix Studio 中描述按钮部件。"
menu_order: 50
tags:
  - "工作室"
  - "页面编辑器"
  - "按钮"
  - "小部件"
---

## 1 导言

按钮 [小部件](page-editor-widgets) 允许最终用户执行各种操作，例如保存更改或关闭当前页面：

{{% image_container width="400" %}}![](attachments/page-editor-widgets-buttons/button-example.png)
{{% /image_container %}}

以下类别和按钮可在 Mendix Studio 中作为默认小部件使用：

* **按钮** - 有一般动作的按钮，如打开或关闭一个页面，调用微流程，签出用户，打开链接：
  * 打开页面
  * 调用微流
  * 关闭页面
  * 登出
  * 打开链接
* **数据按钮** - 操纵数据并用于创建或删除对象、保存或取消更改的按钮：
  * 创建对象
  * 保存更改
  * 删除对象
  * 取消更改
* **工作流按钮** - 与 [工作流相关的按钮](workflows) 用于调用工作流， 完成或显示一个 [用户任务](workflows-user-task), 显示一个工作流页面:
  * 呼叫工作流
  * Complete Task
  * 显示用户任务
  * 显示工作流

{{% alert type="info" %}}

除了默认按钮小部件外，您还可以 [从Mendix Marketplace](https://marketplace.mendix.com/) 下载小部件到您的应用。 For more information, see the [Widgets by Origin](page-editor-widgets#widgets-by-origin) section in *Widgets*.

{{% /报警 %}}

## 2 事件部分

**事件** 部分的属性是上面列出的按钮的部分预设。 他们取决于按键执行的动作。 例如，如果按钮是要打开一个页面， **点击动作** 在 **事件** 部分将是 **页面**。 然而，您需要指定哪个页面将打开该按钮。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-buttons/events-section-page-button.png)
{{% /image_container %}}

欲了解更多信息，请查看事件部分</a> 部分中的
默认属性。 </p> 

{{% alert type="info" %}}

您可以更改预设属性，并使按钮执行另一个操作。 

{{% /报警 %}}

关于 **事件** 部分和点击动作的更多信息，见 [Events Sec](page-editor-widgets-events-section)。



### 2.1 事件部分中的默认财产 {#default-properties}

**点击动作** 在 **事件** 部分决定按钮的动作。 

{{% image_container width="300" %}}![](attachments/page-editor-widgets-buttons/events-section.png) 

{{% /image_container %}}

您可以在下表中找到需要配置的默认动作和属性列表：

| 按钮            | 默认操作          | 要配置的属性                                                                                                                                                                                                                 |
| ------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 打开页面          | 页             | 对于 **打开页面** ，您可以配置以下属性：<ul><li>**页面**</li><li>**创建对象** 和 **Entity** - 如果您想创建一个新对象并将其作为上下文传到选定的页面， 启用 **Create Object** (默认禁用) 并选择 **Entity** 。</li></ul> For more information on these properties, see section the [Create Object Option](page-editor-widgets-events-section#create-object-option) section in *Events Section*. |
| 调用微流          | 微流            | **微流**                                                                                                                                                                                                                 |
| 关闭页面          | 关闭页面          | 无                                                                                                                                                                                                                      |
| 登出            | 登出            | 无                                                                                                                                                                                                                      |
| 打开链接          | 打开链接          | 对于 **打开链接** ，您需要配置以下属性： <ul><li>**Link Type** (Default: *Web*)</li><li>**Source** (默认：*使用字数值*)</li><li>**Url**</li></ul> For more information on these properties, see the [Open Link Action](page-editor-widgets-events-section#open-link-action) section in *Events Section*.                 |
| 创建对象          | 创建对象          | **页面** 和 **实体**                                                                                                                                                                                                        |
| 保存更改          | 保存更改          | 无                                                                                                                                                                                                                      |
| 删除对象          | 删除对象          | 无                                                                                                                                                                                                                      |
| 取消更改          | 取消更改          | 无                                                                                                                                                                                                                      |
| 呼叫工作流         | 呼叫工作流         | **工作流**                                                                                                                                                                                                                |
| Complete Task | Complete Task | **任务**                                                                                                                                                                                                                 |
| 显示用户任务        | 显示任务页面        | 无                                                                                                                                                                                                                      |
| 显示工作流         | 显示工作流页面       | **管理页面**                                                                                                                                                                                                               |




## 3 一般部分

下面的表格描述了 **常规** 部分中可用的属性。

| 财产   | 描述                                                                                                                 |
| ---- | ------------------------------------------------------------------------------------------------------------------ |
| 标题   | 定义按钮上将显示的文本。 按钮有预设字幕，取决于它们执行的动作。                                                                                   |
| 图标   | 确定按钮标题前面显示的图标。                                                                                                     |
| 渲染模式 | 定义按钮向最终用户显示的方式。 可能的备选办法如下： <ul><li>按钮*(默认)* - 小部件将作为按钮渲染。</li><li>链接 — 小部件将呈现为超链接</li></ul>                                                                |
| 样式   | 将预定义的样式应用于按钮。 可能的备选办法如下： <ul><li>默认 <em>(除**保存变更**外的所有按钮默认值)</em></li><li>反转</li><li>主要的</li><li>信息</li><li>成功 <em>(缺省**保存变更** 按钮)</em></li><li>警告</li><li>危险</li></ul>每个样式的颜色取决于您在 **主题定制器** 中的设置。 欲了解详情，请参阅 [主题定制器](theme-customizer)。 |




## 4 条件可见性

{{% snippet file="studo/visibility-section-link.md" %}}



## 5 设计科

关于 **设计** 部分及其属性的信息，请参阅 [设计部分](page-editor-widgets-design-section)。



## 6 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
