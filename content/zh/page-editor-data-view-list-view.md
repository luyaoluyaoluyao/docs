---
title: "数据视图 & 列表视图属性"
parent: "页面编辑器部件"
description: "描述Mendix Studio页面编辑器中的数据视图和列表视图。"
menu_order: 10
tags:
  - "工作室"
  - "页面编辑器"
  - "页面"
  - "数据视图"
  - "列表视图"
---

## 1 导言

本文档描述了Mendix Studio页面编辑中的数据视图和列表视图。

*数据视图* 是一个页面上显示一个对象内容的起点。  数据视图通常包含像文本框这样的输入小部件。

例如，如果您想要填写每个客户的信息，数据视图是做到这一点的最佳方式。

{{% image_container width="400" %}}![](attachments/page-editor-data-view-list-view/data-view-example.png)
{{% /image_container %}}

在更复杂的模板中，数据视图可以包含相关对象的其他数据视图，例如： 显示客户详细信息并显示客户付款状态，如果这些是作为两个不同实体的模型。

*列表视图* 是显示对象列表的起始点。 例如，如果您想要显示所有客户的列表，请使用列表视图。

{{% image_container width="400" %}}![](attachments/page-editor-data-view-list-view/list-view-example.png)
{{% /image_container %}}

## 2 个数据视图属性 {#data-view-properties}

数据视图由下列属性组成：

* [数据源](#data-source-data-view)
* [A. 概况](#general-section-data-view)
* [设计](#design-section-data-view)

{{% image_container width="300" %}}![](attachments/page-editor-data-view-list-view/data-view-properties.png)
{{% /image_container %}}

### 2.1 数据来源 {#data-source-data-view}

数据源决定在数据视图中显示哪些对象。 关于数据源的一般信息，见[数据源](/refguide/data-sources) 在 *Studio Pro 指南* 中。

| 数据源属性 | 描述                                                                                                                                                                                                                           |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 二. 背景 | 一个数据源来确定无论您从哪里打开页面都会传递选中的对象。 例如，当您在microflow中添加 **显示页面** 活动时，您选择要通过的页面和对象。 (关于微流的更多信息，见 [微流](microflows)。) 这意味着当页面在微流中打开时， 此类型的对象被提供，并将显示在页面上的数据视图中。 欲了解更多关于上下文源的技术信息，见 [上下文源](/refguide/context-source) *Studio Pro Guide*。 |
| 微流    | 一个运行选中微流并显示返回值的数据源。 欲了解更多技术信息，见 [微流程源](/refguide/microflow-source) 在 *Studio Pro 指南* 中。                                                                                                                                      |
| 列表小部件 | 一个数据源，允许数据视图在列表小部件(列表视图)中显示详细信息。 欲了解更多技术信息，请参阅 *Studio Pro 指南* 中的 [监听小部件源](/refguide/listen-to-grid-source)。                                                                                                                 |

### 2.2 概况 {#general-section-data-view}

在 **常规** 部分中，您可以启用/禁用以下选项：

* **只读** (默认禁用) - 启用后，所有 [输入小部件](page-editor-widgets-input-elements) (例如，禁用) 数据视图中的文本区域，复选框将处于只读模式
* **显示页脚** (默认启用) -- 页脚是文档底部的一个区域。 通常包含所有页面的共同信息，例如版权信息

### 2.3 设计 {#design-section-data-view}

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

## 3 列表视图属性 {#list-view-properties}

列表视图由下列属性组成：

* [数据源](#data-source-list-view)
* [A. 概况](#general-section-list-view)
* [设计](#design-section-list-view)

{{% image_container width="300" %}}![](attachments/page-editor-data-view-list-view/list-view-properties.png)
{{% /image_container %}}

### 3.1 数据来源 {#data-source-list-view}

数据源决定在列表视图中显示哪些对象。 关于数据源的一般信息，见[数据源](/refguide/data-sources) 在 *Studio Pro 指南* 中。

| 数据源属性  | 描述                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 数据库    | 确定显示的对象或对象直接从数据库检索的数据源。 您需要选择一个 **实体** (即您在域模型中已有)， 或创建一个新实体，如果您设置数据库为数据源。 欲了解更多技术信息，见 [数据库源](/refguide/database-source) *Studio Pro 指南*。<br />**过滤器** - 限制列表视图中的数据。 您只能在为列表视图指定实体后才能创建过滤器。 欲了解更多关于数据过滤的信息，请参阅 [数据过滤器](filters)。<br />**排序顺序** - 列表视图中各项的显示顺序。 您只能在为列表视图选择实体后才能指定排序顺序。 您可以添加多个排序规则。 例如，您可以添加两个分类规则：一个是按名称按升序排序。 另一个是通过电子邮件按降序排序。 唯一的项目将按名称升序排序 但如果两个或多个项目具有相同的名字，那么这些项目将通过电子邮件排序。 |
| 微流     | 一个运行选定微流并显示返回值的数据源(例如在对象列表中)。 欲了解更多技术信息，见 [微流程源](/refguide/microflow-source) 在 *Studio Pro 指南* 中。                                                                                                                                                                                                                                                                                                             |
| XPath  | 目前，此数据源只能在 Studio Pro中配置。 欲了解更多信息，请参阅 [XPath Source](/refguide/xpath-source)。                                                                                                                                                                                                                                                                                                                                 |
| 纳诺夫low | 目前，此数据源只能在 Studio Pro中配置。 欲了解更多信息，请参阅 [Nanoflows](/refguide/nanoflows)。                                                                                                                                                                                                                                                                                                                                       |
| 协会     | 当列表视图放置在另一个数据容器中，例如数据视图中时可用。 列表视图中包含关联到数据视图对象的对象。 例如，您可以显示客户的所有订单。                                                                                                                                                                                                                                                                                                                                            |

### 3.2 事件

 您可以在 **事件** 部分中选择 **点击动作**。 **点击动作** 定义了用户点击列表视图行时执行的操作。

关于 **事件** 部分和点击动作的更多信息，请参阅 [小部件中的事件部分](page-editor-widgets-events-section)。

### 3.3 概况 {#general-section-list-view}

在 **常规** 部分中 您可以选择要显示在页面上的行数，并为列表视图设置只读行数：

* **页面大小** - 页面上显示的行数； 达到指定的上限后， **加载更多。 。** 按钮显示在页面上。

{{% image_container width="400" %}}![](attachments/page-editor-data-view-list-view/load-more-list-view.png)
{{% /image_container %}}

* **只读** (默认启用) - 启用后，所有 [输入小部件](page-editor-widgets-input-elements) (例如，启用) 列表视图中的文本区域，复选框将处于只读模式

### 3.4 设计科 {#design-section-list-view}

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

## 4 阅读更多

* [页 次](page-editor)
