---
title: "结构"
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

有以下结构部件：

* [列和侧栏](#columns)

* [容器](#container-overview)

* [组框](#group-box-overview)

* [标签容器](#tab-container)

* [代码片段](#snippet)

    ![](attachments/page-editor-widgets-structure/structure-widgets.jpg)

## 2 列和侧边栏{#columns}

**列** and **侧边栏** 小部件基于一个 [布局网格](#layout-grid) - 一个用行和列构造你的页面的部件。 **列和侧边栏** 是预设列数的布局网格配置。

## 3 布局网格概览 {#layout-grid}

**布局网格** 有助于您构建一个页面并立即做出响应。 这意味着布局网格有内置行为来显示页面在不同设备上的外观。 切换 **设备** 模式以查看一个页面将如何显示在手机、 平板电脑或桌面上：

{{% image_container width="300" %}}![设备模式](attachments/page-editor-widgets-structure/device-modes.png)
{{% /image_container %}}

布局网格包含 [列](#column) 和 [行](#row).

行由一个或多个列组成，它们放在响应(桌面)视图中。

![行示例](attachments/page-editor-widgets-structure/row-example.png)

列是行内的单元格。 您可以在列中放置一个或多个小部件，例如，您可以在列中放置两个按钮。

{{% image_container width="300" %}}![列示例](attachments/page-editor-widgets-structure/column-example.png)
{{% /image_container %}}

关于行和列的更多信息，请参阅 [行属性](#row) 和 [列属性](#column) 部分。

### 3.1 布局网格 {#layout-grid-properties}

您可以通过面包屑导航访问 **布局网格** 属性 (以获取更多信息) 见 [Breadcrumb](page-editor#breadcrumb) 章节在 *页面*。 布局网格属性由以下部分组成：

* [扩展](#expand-section)

* [A. 概况](#general-section)

* [设计](page-editor-widgets-design-section)

    {{% image_container width="250" %}}![布局网格属性](attachments/page-editor-widgets-structure/layout-grid-properties.png)
    {{% /image_container %}}

#### 3.1.1 扩展 {#expand-section}

**展开** 章节 > **添加行** 允许您在选定的一行上方或下方添加一行，以创建更多的空间来放置小部件。

{{% alert type="info" %}}

[行](#row) 和 [列](#column) 有具有相同设置的 **扩展** 部分。

{{% /报警 %}}

若要添加新行，请执行以下内容之一：

1. 在面包屑导航及其 **属性** > **添加行**点击其中一个按钮插入上面或下面的一行。
2. 选择行及其 **属性** > **添加行**点击其中一个按钮插入上面或下面的一行。
3. 选择列及其 **属性** > **添加行**点击其中一个按钮插入上面或下面的一行。

将插入一个空行。

#### 3.1.2 一般部分 {#general-section}

在 **常规** 部分中，您可以设置布局网格的宽度。 您可以选择以下一种：

* **完整宽度** - 布局网格将其放置在容器中的整个宽度
* **固定宽度** — 布局网格将在你的页面中心处有固定大小，根据你的设备自动调整

#### 3.1.3 设计部分

关于 **设计** 部分及其属性的信息，请参阅 [设计部分](page-editor-widgets-design-section)。

### 3.2 行属性 {#row}

*行* 属性由以下部分组成：

* [扩展](#expand-section-row)

* [容器设置](#container-settings)

* [A. 概况](#general-section-row)

    {{% image_container width="250" %}}![行属性](attachments/page-editor-widgets-structure/row-sections.png)
    {{% /image_container %}}

#### 3.2.1 扩展 {#expand-section-row}

**展开** 章节 > **添加行** 允许您在选定的行上方或下方添加一行。 For more details, see the [Expand Section](#expand-section) of the *layout grid*.

#### 3.2.2 容器设置部分 {#container-settings}

在 **容器设置** 部分中，您可以设置布局网格的宽度并在全宽度或固定宽度之间进行选择。

{{% alert type="info" %}}

此属性与布局格子的 [常规部分](#general-section) 中的属性相同。 欲了解详情，请参阅 [常规部分](#general-section)。

{{% /报警 %}}

#### 3.2.3 一般部分 {#general-section-row}

在行的 **常规** 部分中，您可以选择其中的列数，对齐列并在它们之间添加间距。 本节包含以下设置：

* **列** - 设置列中的列数

    * 您也可以在工作区设置列数：从列中选择一个列，然后点击顶部的加号图标向右添加一个新列

        {{% image_container width="300" %}}![Adding New Column](attachments/page-editor-widgets-structure/adding-new-column.png){{% /image_container %}}

* <a name="align-columns"></a>**垂直对齐列** - 垂直对齐行中所有列，您可以选择以下选项：

    {{% image_container width="280" %}}![](attachments/page-editor-widgets-structure/align-columns.png)
    {{% /image_container %}}

* **列之间的间距** - 启用后，在列之间添加间距

### 3.3 列属性 {#column}

列属性由以下部分组成：

* [扩展](#expand-section-column)

* [A. 概况](#general-section-column)

    {{% image_container width="250" %}}![列部分](attachments/page-editor-widgets-structure/column-sections.png)
    {{% /image_container %}}

#### 3.3.1 扩展 {#expand-section-column}

一列的扩展部分允许您添加一行或一列。


##### 3.3.1.1 增加行

**添加行** 允许您在选定行上方或下方添加一行。 For more details, see the [Expand Section](#expand-section) of the *layout grid*.

##### 3.3.1.2 增加列

**添加列** 允许您在左侧或右侧添加一列。

#### 3.3.2 一般部分 {#general-section-column}

在 **常规** 部分中，您可以设置列 [宽度](#column-width) 和 [对齐](#align-column) 单独列.

##### 3.3.2.1 Width {#column-width}

您可以通过选择相应的设备模式来设置桌面、平板电脑或手机的列宽度：

![](attachments/page-editor-widgets-structure/width-per-device.png)

您可以选择以下选项：

* **自动填充** — — 需要一个列的可用空间 (例如，如果有一个列， 它将跨越整个行的列，对于两列，它将在它们之间平均分空格)

* **自动适合内容** — — 自动使列大小与它的内容匹配

* **手动** - 允许您手动设置列大小

    * 当您选择 **手册** 时，滑块显示允许您设置列宽度从1到12：

        ![](attachments/page-editor-widgets-structure/column-size.png)

您也可以手动调整工作区域的列大小：拖动列边框以改变其大小。

{{% image_container width="300" %}}
![调整列大小](attachments/page-editor-widgets-structure/resizing-column.png)
{{% /image_container %}}

**宽度** 属性可以用于使您的布局更加灵活，更适合不同类型的设备。

例如，您有一个布局网格，一个列和两个列：一个图片在一个列， 还有一个详细的文本在另一个地方。

对于 *桌面* and *平板*, 您可能想要将第一列的图片设置为 **自动适合内容** ，而第二列设置为 **自动填充**， 这样，第一列将根据图片的大小进行调整，而第二列将占用行的其余部分：

![布局示例桌面](attachments/page-editor-widgets-structure/layout-example-desktop.png)

对于 *电话*, 最好把两个列放在另一个列下。 设置它们为 **手册** 宽度 *12* 的宽度。 在这种情况下，第二列将被自动包装到另一行：

 {{% image_container width="300" %}}
![布局示例电话](attachments/page-editor-widgets-structure/layout-example-phone.png)
{{% /image_container %}}

##### 3.3.2.2 垂直对齐 {#align-column}

**垂直对齐** 属性覆盖 [垂直对齐列](#align-columns) 行上的属性，并为单个列设置对齐。

## 4 容器概述 {#container-overview}

**容器** 被用作布局元素，您可以同时放置部件或组小部件， 拖动或删除它们。 例如，您可以在一个容器中放置一个章节标题和输入小部件以填写程序细节， 然后将整个容器重新定位到页面上的不同位置。

{{% image_container width="300" %}}![容器示例](attachments/page-editor-widgets-structure/container.png)
{{% /image_container %}}

容器属性由 **设计** 部分组成。 欲知详情，请见 [设计部分](page-editor-widgets-design-section)。

## 5 组框概述 {#group-box-overview}

群组框用于群组小部件。 组框可以配置为使用内置的所有元素折叠或动态扩展。

{{% image_container width="300" %}}![组框示例](attachments/page-editor-widgets-structure/group-box.png)
{{% /image_container %}}

### 5.1 组盒子属性

组框属性由 **常规** 部分和 **设计** 部分组成。 关于 **设计** 部分及其属性的信息，请参阅 [设计部分](page-editor-widgets-design-section)。

下面的表格描述了 **常规** 部分中可用的属性。

| 财产   | 描述                                                                                 |
| ---- | ---------------------------------------------------------------------------------- |
| 显示标题 | **显示标题** 定义是否在组框上方显示页眉。 <br />*此属性默认启用。*                                     |
| 标题   | 此属性仅在 **显示页眉** 选项启用时才显示。 它定义了标题中显示的标题。                                             |
| 可折叠的 | 此属性仅在 **显示页眉** 选项启用时才显示。 它确定了是否能够瓦解或扩大集团盒及其成分。 此属性的可能值如下：<ul><li>**是(开始扩展)** - 当用户点击顶部图标时，组框内的元素将会被初始扩展并折叠。</li><li>**是 (开始折叠)** - 当用户点击标题中的加号图标时，组框内的元素将会被首次折叠并被扩展 </li><li>**否** - 组框元素不能被扩展或折叠。</li></ul> |

## 6 个标签容器概述 {#tab-container}

制表符容器是用于显示按标签分类的信息的容器。 如果您想要显示的信息数量大于屏幕上的空间数量，这将是有用的。 例如，您可以在一个标签上显示客户列表，并在另一个标签上显示订单。

{{% image_container width="300" %}}![标签容器示例](attachments/page-editor-widgets-structure/tab-container-example.png)
{{% /image_container %}}

您可以在每个选项卡中放置小部件或小部件组，并在它们中单独配置信息。

### 6.1 一般部分

在 **常规** 部分中，您可以配置以下属性：

*  **标签** - 使用无线电按钮切换一个标签到另一个标签； 单击标签页并拖动它来更改标签顺序； 点击 **编辑** 图标打开标签属性并配置它(以获取更多信息) 查看 [标签属性](#tab-properties) 章节)

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-container-tabs-property.png)
    {{% /image_container %}}

*  **添加新标签** - 为您的标签容器添加一个新标签； 标签属性将自动打开(详情请查看 [标签属性](#tab-properties) 部分)

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/add-new-tab.png)
    {{% /image_container %}}

### 6.2 设计科

关于 **设计** 部分及其属性的信息，请参阅 [设计部分](page-editor-widgets-design-section)。

### 6.3 Tab 属性 {#tab-properties}

每个标签具有以下属性：

* **标题** - 定义标签的名称；您也可以在页面中双击它来编辑标题。

*  **默认标签** - 定义打开页面时哪个标签处于活动状态。 如果没有标签被设置为默认标签，将显示第一个标签页。 默认情况下，没有一个标签被设置为默认标签。

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-structure/tab-properties.png)
    {{% /image_container %}}

## 7 片段概述 {#snippet}

代码片段定义了可重复使用的页面元素，并在 Studio Pro中创建。 通过使用代码片段，你可以在更少的地方修改页面.

例如， 您在 Studio Pro 中的团队成员创建了一个代码片段并添加了一个客户表单，将此表单变成一个可重复使用的页面元素。 您也可以在工作室中使用这个代码片段：

{{% image_container width="500" %}}![](attachments/page-editor-widgets-structure/snippet-example.jpg)
{{% /image_container %}}

虽然您可以在工作室的页面上调用 (use) 代码片段，但您不能创建、更改或删除它们。 关于Studio Pro中代码片段的更多信息，请参阅 [代码片段](/refguide/snippet)。

{{% alert type="info" %}}
如果你不包含任何代码片段 **代码片段** 小部件将不会显示。
{{% /报警 %}}

要调用代码片段并将其添加到您的页面，请做以下操作：

1. 在 **工具箱** > **小部件**中，找到 **片段** 小部件并拖放在您的页面上。

2. 打开属性并点击 **代码片段** 属性。

3. 在 **选择代码片段** 对话框中，选择你想要在你的页面上使用的代码片段，然后点击 **选择**。

    ![](attachments/page-editor-widgets-structure/select-snippet.jpg)

代码片段已添加到您的页面。

## 8 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
