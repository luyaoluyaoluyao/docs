---
title: "结构部件"
parent: "页面编辑器部件"
description: "描述Mendix Studio中的结构部件。"
menu_order: 60
tags:
  - "工作室"
  - "页面编辑器"
  - "布局"
  - "布局部件"
  - "结构部件"
---

## 1 导言

结构部件是允许您为您的页面提供结构并在其中分组其他部件的小部件。

布局小部件如下：

* [列和侧栏](#columns)
* [容器](#container-overview)
* [组框](#group-box-overview)
* [标签容器](#tab-container)

## 2 列和侧边栏{#columns}

**列** 和 **侧边栏** 小部件是预设列数的小部件。 此类别中的所有小部件都是基于一个 [布局网格](#layout-grid) ——一个用行和列构造你的页面的元素。

## 3 布局网格概览 {#layout-grid}

**布局网格** 有助于您配置一个页面并立即做出响应。 这意味着布局网格有内置行为来显示页面在不同设备上的外观。 在顶部栏中切换 **设备** 模式，以查看一个页面将如何显示在手机、 平板电脑或桌面上。

{{% image_container width="350" %}}![设备模式](attachments/page-editor-widgets-structure/device-modes.png)
{{% /image_container %}}

布局网格包含 [列和行](#columns-and-rows)。

一行包含在响应(桌面)视图中彼此放置的项目。

![行示例](attachments/page-editor-widgets-structure/row-example.png)

列是行内的单元格。 您可以在列中放置一个或多个元素。例如，您可以在列中放置两个按钮。

{{% image_container width="400" %}}![列示例](attachments/page-editor-widgets-structure/column-example.png)
{{% /image_container %}}

使用列对齐一行中的项目。  关于行和列的更多信息，见第 [2.2 行和列属性](#columns-and-rows) 部分。

### 2.1 布局网格 {#layout-grid-properties}

您可以通过面包crumb 轨迹访问 **布局网格** 属性 (以获取更多信息)。 查看 **[Breadcrumb Trail](page-editor#breadcrumb)** section in *pages*)。 布局网格属性由以下部分组成：

* [扩展](#expand-section)
* [A. 概况](#general-section)
* [设计](page-editor-widgets-design-section)

#### 2.1.1 扩展 {#expand-section}

**展开** 章节 > **添加行** 允许您在选定的一行上方或下方添加一行，以创建更多的空间来放置小部件。

{{% image_container width="300" %}}![展开部分](attachments/page-editor-widgets-structure/layout-grid-expand-row.png)
{{% /image_container %}}

要添加一行，请在布局网格中选择一行，然后点击 **添加行** 中的一个按钮。 将插入与所选行完全相同的一行。

{{% alert type="info" %}}

**行** and **列** 也有具有相同属性的 **扩展** 部分。

{{% /报警 %}}

#### 2.1.2 一般部分 {#general-section}

布局网格的 **常规** 部分包含 **全宽度** 属性。 启用此属性时，布局网格会占用容器的整个宽度。 当禁用时，布局网格将在您的页面中心有固定大小，根据您的设备自动调整。

#### 2.1.3 设计科

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

### 2.2 行和列属性 {#columns-and-rows}

**行** 和 **列** 属性由以下部分组成：

* [扩展](#expand-section)
* [行布局](#row-layout)

{{% image_container width="300" %}}![行和列属性](attachments/page-editor-widgets-structure/row-and-column-sections.png)
{{% /image_container %}}

#### 2.2.1 扩展

**展开** 版块 **列** 和 **行** 与布局网格的 **扩展** 版块有相同的属性和功能。 欲了解详情，请参阅 *布局网格概览* 中的 [扩展部分](#expand-section)。

#### 2.2.2 行布局部分 {#row-layout}

在 **行布局** 部分中，您可以更改列的排列排列排列安排方式。 更改列数并选择它们在桌面、平板电脑和手机上显示的方式。

| 财产   | 描述                                              |
| ---- | ----------------------------------------------- |
| 桌面   | 更改桌面列的数量和宽度。                                    |
| 平板电脑 | 更改平板电脑列的数量和宽度。 **绘图板** 布局可用的选项取决于 **桌面** 所选的选项。 |
| 电话   | 更改手机列的数量和宽度。 **Phone** 布局可用的选项取决于 **桌面** 所选的选项。 |

在下面的示例中 您可以看到您可以为不同类型的设备选择不同的行布局，并检查在您的应用程序中显示布局的方式。

![不同设备的行布局](attachments/page-editor-widgets-structure/row-layout-scheme.png)

## 4 容器概述 {#container-overview}

**容器** 被用作布局元素，您可以同时放置部件或组小部件， 拖动或删除它们。 例如，您可以在一个容器中放置一个章节标题和输入小部件以填写程序细节， 然后将整个容器重新定位到页面上的不同位置。

{{% image_container width="400" %}}![容器示例](attachments/page-editor-widgets-structure/container.png)
{{% /image_container %}}

容器属性由 **设计** 部分组成。 欲知详情，请参阅小部件中的 [设计部分](page-editor-widgets-design-section)。

## 5 组框概述 {#group-box-overview}

群组框用于群组小部件。 组框可以配置为使用内置的所有元素折叠或动态扩展。

{{% image_container width="400" %}}![组框示例](attachments/page-editor-widgets-structure/group-box.png)
{{% /image_container %}}

### 5.1 组盒子属性

组框属性由 **常规** 部分和 **设计** 部分组成。 关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

下面的表格描述了 **常规** 部分中可用的属性。

| 财产   | 描述                                                                                 |
| ---- | ---------------------------------------------------------------------------------- |
| 显示标题 | **显示标题** 定义是否在组框上方显示页眉。 <br />*此属性默认启用。*                                     |
| 标题   | 此属性仅在 **显示页眉** 选项启用时才显示。 它定义了标题中显示的标题。                                             |
| 可折叠的 | 此属性仅在 **显示页眉** 选项启用时才显示。 它确定了是否能够瓦解或扩大集团盒及其成分。 此属性的可能值如下：<ul><li>**是(开始扩展)** - 当用户点击顶部图标时，组框内的元素将会被初始扩展并折叠。</li><li>**是 (开始折叠)** - 当用户点击标题中的加号图标时，组框内的元素将会被首次折叠并被扩展 </li><li>**否** - 组框元素不能被扩展或折叠。</li></ul> |

## 6 个标签容器概述 {#tab-container}

制表符容器是用于显示按标签分类的信息的容器。 如果您想要显示的信息数量大于屏幕上的空间数量，这将是有用的。 例如，您可以在一个标签上显示客户列表，并在另一个标签上显示订单。

{{% image_container width="400" %}}![标签容器示例](attachments/page-editor-widgets-structure/tab-container-example.png)
{{% /image_container %}}

您可以在每个选项卡中放置小部件或小部件组，并在它们中单独配置信息。

### 6.1 Tab Container General 属性

在 **常规** 部分中，您可以配置以下属性：

*  **标签** - 使用无线电按钮切换一个标签到另一个标签； 单击标签页并拖动它来更改标签顺序； 点击 **编辑** 图标打开标签属性并配置它(详情请参阅章节 [5)。 标签属性](#tab-properties))

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-container-tabs-property.png)
    {{% /image_container %}}

*  **添加新标签** - 为您的标签容器添加一个新标签； 标签属性将自动打开(详细信息，参见 [5部分)。 标签属性](#tab-properties))

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/add-new-tab.png)
    {{% /image_container %}}

### 6.2 制表容器设计属性

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

### 6.3 Tab 属性 {#tab-properties}

每个标签具有以下属性：

* **标题** - 定义标签的名称；您也可以在页面中双击它来编辑标题。

*  **默认标签** - 定义打开页面时哪个标签处于活动状态。 如果没有标签被设置为默认标签，将显示第一个标签页。 默认情况下，没有一个标签被设置为默认标签。

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-properties.png)
    {{% /image_container %}}

## 7 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
