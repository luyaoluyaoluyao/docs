---
title: "列表视图"
parent: "数据部件"
menu_order: 40
tags:
  - "studio pro"
---

## 1 导言

列表视图显示对象列表。 例如，您可以显示所有配置文件列表：

![](attachments/data-widgets/list-view-example-profile.png)

每个对象都使用模板显示。 此模板是通过在列表视图的下拉区域中放置小部件定义的。 显示的对象列表是由 [数据源](#data-source) 决定的。

## 2 属性

列表视图属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![](attachments/data-widgets/list-view-properties.png)
{{% /image_container %}}

列表视图属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [模板](#templates)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2. 数据源部分 {#data-source}

数据源决定在列表视图中显示哪些对象。 关于数据源的一般信息，请参阅 [数据源](data-sources)。

#### 2.2.1 Type

列表视图支持以下类型的数据源：

* [数据库源](database-source) - 直接检索对象组成数据库。 数据库源可以在 [离线](offline-first) 应用程序中使用。
* [XPath 源](xpath-source) - 直接从数据库中检索对象
* [微流程源](microflow-source) - 通过执行微流程计算对象列表
* [Nanoflow 源](nanoflow-source) — — 通过执行 nanoflow 计算对象列表
* [关联源](association-source) - 关注一个协会来到对象

数据库和 XPath 源从数据库中检索对象并支持搜索和排序。

{{% alert type="warning" %}}Searching is not supported on native mobile pages.{{% /alert %}}

### 2.3 设计属性部分{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 一般部分 {#general}

#### 2.4.1 可编辑

如果此属性设置为 *是*，列表视图中的项目可以被编辑。 对列表视图项目所作的更改可以通过 **保存** 按钮保存并使用 **取消** 按钮还原。 **点击** and **页面大小** 将不会显示为避免在保存或还原的更改方面出现混乱。

#### 2.4.2 点击时

点击事件定义了用户点击列表视图行时执行的动作。 关于点击事件的更多信息，见 [点击事件](on-click-event)。

#### 2.4.3 页大小 {#page-size}

页面上显示的行数；达到指定的上限后， **加载更多...** 按钮将显示在页面上。

{{% alert type="info" %}}The **Load more** button is not visible on native mobile pages. 当显示当前加载的最后一个项目时，列表视图将自动加载新项目。{{%/提醒 %}}

#### 2.4.4 滚动方向

●{% alert type="info" %}}只在本机移动页面上支持滚动方向属性。{%/提醒 %}}

此属性决定列表视图是垂直(默认)或水平显示其项目。

#### 2.4.5 栏数

●{% alert type="info" %}}。只在本机移动页面上支持列属性。{%/提醒 %}}

有了这个属性，你可以更改彼此以一行显示的条目数量。 如果您将滚动方向属性设置为水平，这个属性决定每列的项目数量。

#### 2.4.6 下一步行动

●{% alert type="info" %}}。只在本机移动页面上支持列属性。{%/提醒 %}}

下拉动操作定义了在列表视图上向下拖动时执行的操作。 它的常见行为是通过同步数据更新列表视图的内容。

### 2.5 模板部分 {#templates}

原生移动页面不支持{% alert type="warning" %}}模板。{{%/提醒 %}}

如果连接到列表视图的实体有专业化，您可以为每个专业指定模板。 列表中每行显示最特定的模板。 可以通过单击添加专业化模板时出现的额外页眉来选择不同的模板。

{{% alert type="info" %}}

让我们说你有一辆实体车辆及其两种专业：自行车和汽车。 还有称作运动车的汽车专业化。 您创建了一个连接到车辆的列表视图。 使用列表视图的模板属性，您指定了任意车辆显示的模板。 对于专业自行车和汽车，您创建单独的模板来显示它们。

现在，如果有一行类型自行车，将显示自行车的特定模板。 车型车行将显示在车模版中。 汽车模板中显示了一行类型的SportsCar。 没有针对运动车的模板(这个例子)，汽车是有模板的“最接近”的概括。

{{% /报警 %}}

### 2.6 可见性科 {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 执行特定操作

要在列表视图中执行操作，请在页面上选择并右键单击它。 可能的动作列表已打开。 此列表中的一些动作，例如 **选择数据源**, **编辑可见条件**这是设置属性的快速方式，下面是您可以执行的特定动作：

* **转到实体** — 打开一个域模型并突出显示一个实体被用作数据源
* **转到数据源** **microflow **-这个动作仅在微流程设置为数据源并打开这个微流程时显示
* **转到数据源 nanoflow** - 这个动作仅在将nanoflow 设置为数据源并打开这个nanoflow 时显示

## 4 阅读更多

* [页](page)
* [数据部件](data-widgets)
* [数据源](数据来源)
* [页面编辑器中常见的属性](common-widget-properties)
