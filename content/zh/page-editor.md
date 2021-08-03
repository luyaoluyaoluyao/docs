---
title: "页 次"
description: "在 Mendix Studio 中描述页面编辑器。"
menu_order: 30
tags:
  - "工作室"
  - "页面编辑器"
  - "页面"
---

## 1 导言

页面编辑器允许用户定义Mendix 应用程序的最终用户界面。

要在 Mendix Studio 中查看您应用的 **页面** ，请点击 **页面** 在工作室左侧菜单栏中的图标。

{{% image_container width="300" %}}![](attachments/page-editor/pages-icon.png)
{{% /image_container %}}

{{% alert type="warning" %}}

工作室仅支持基于Atlas界面框架的应用。 关于Atlas界面的详细信息，见 [Atlas界面](/howto/front-end/atlas-ui)。

{{% /报警 %}}

## 2 个组件

工作室的页面由以下部分组成：

* **布局** 构造您的页面。 每个页面都基于一个布局。 例如， **Atlas_default** 或 **PopupLayout** 是您在创建页面时可以选择的布局。
* **模板** - 创建新页面的起点。 每次您创建一个新页面， 您选择一个模板，取决于您想要在页面上显示的数据以及您想要显示的方式：一个列表 一个控制面板，一个表单。 例如， **仪表板动作瓷块**, **列表默认**, **主详细信息** 是模板类型。
* **小部件** — — 单个用户界面元素。 欲了解更多信息，见第 [5.2节。 小部件](#widgets) 和 [小部件](page-editor-widgets)。
* **Building block** — — 预先配置的一组元素加速构建你的页面和样式的过程。 欲了解更多信息，见第 [5.1节Building Blocks](#building-blocks)。

上述组成部分由Atlas界面提供动力。 欲了解更多信息，请参阅 [Atlas UI](/howto/front-end/atlas-ui)。

## 3 执行基本功能 {#page-editor-basic-functions}

### 3.1 开启页面

打开工作室后，它会自动打开应用程序的主页。

要在 Studio 中打开一个页面, 请执行以下操作：

1. 点击左侧菜单栏中的 **页面** 图标。

2.  在显示的应用页面列表中，选择您想要打开的页面并单击它。

    {{% image_container width="400" %}}![](attachments/page-editor/opening-a-page.png)
    {{% /image_container %}}

所选页面已打开。

### 3.2 创建一个新页面 {#creating-new-page}

要在 Studio 中创建一个新的页面, 请执行以下操作:

1. 点击 **页面** 图标。
2.  单击显示侧面板右上角的 **新**。

    {{% image_container width="400" %}}![](attachments/page-editor/new-page.png)
    {{% /image_container %}}

3. 在 **创建新页面** 对话框窗口，填写页面标题，选择布局和页面模板。
4.  点击 **创建**。

    ![](attachments/page-editor/create-new-page-dialog.png)

新页面已创建。

### 3.3 删除页面

若要删除工作室中的一个页面, 请执行以下操作:

1. 打开您想要删除的页面。
2. 打开 **属性** 选项卡。
3.  点击 **在 **属性底部删除**** 标签。

    ![](attachments/page-editor/page-delete.png)

   所选页面已删除。

### 3.4 页面上显示元素

要查看元素及其 [属性](#page-editor-properties)，请单击此元素。

选中的元素用蓝边框标明。 此外，如果元素在数据容器内(数据视图或列表视图)，它将以数据容器图标表示。

{{% image_container width="400" %}}![](attachments/page-editor/input-widget-example.png)
{{% /image_container %}}

## 4 个面包屑轨迹 {#breadcrumb}

当您在您的页面上选择一个项目时，在Studio左下角会出现一个面包屑路径。

面包屑追踪服务于两个功能：

* 在页面上显示选中项目的自下而上的布局
* 允许用户选择页面上的元素并查看其属性

例如，当您在页面上选择一个按钮时，您会看到它放在一个列中的容器中。  如果列在一行中，此行放置在页面的布局格子中。

![](attachments/page-editor/breadcrumb.png)

要查看该元素的信息，请点击面包屑导航线中的此元素及其属性自动显示。

### 4.1 使用面包屑导航轨迹查看导航布局信息

您也可以通过在面包屑路径中点击导航布局查看信息。

以下选项将在 **属性** 标签中显示：

{{% image_container width="300" %}}![](attachments/page-editor/navigation-layout.png)
{{% /image_container %}}

## 5 Toolbox Tab

**工具箱** 显示了可以在页面上使用的工具。

此选项卡由以下内容组成：

* [小部件](#widgets)
* [构建块](#building-blocks)

### 5.1 部件 {#widgets}

部件是可以配置的单个用户界面元素。 You can [quickly configure](page-editor-widgets#quick-config) most of the non-custom widgets when adding them on a page. 欲了解更多信息，见 [小部件](page-editor-widgets)。

{{% alert type="info" %}}

您可以在 [部件概述](settings-widget-overview) 中更新部件。

{{% /报警 %}}

### 5.2 建筑块 {#building-blocks}

建筑块由预设的小部件组成，让你能够更快地构建一个页面：你只需要拖放它们到页面。

![](attachments/page-editor/building-blocks.png)

Studio的构件分为以下几类：

| 构建块   | 描述                                            |
| ----- | --------------------------------------------- |
| 信头    | 页眉结合了页面标题的功能和您的页面的控制栏。 由于其精密设计和多面性，它常常用于移动网页。 |
| 列表    | 当您需要显示数据列表时使用这些块。                             |
| 卡片    | 卡片含有不同用途的不同构件。                                |
| 图表    | 如果你想要以图表显示你的数据，请使用这些建筑块。                      |
| 形式    | 使用这些建筑块来填写一个表单，由用户在您的应用程序中填写。                 |
| 列表控件  | 代表数据作为控制列表，并帮助您排序和搜索列表中的项目。                   |
| 主详细信息 | 使用这些建筑块来显示许多项目的列表，但只显示所选元素的详细信息。              |
| 面包屑导航 | 当您想要在应用程序中显示当前页面位置时，使用这些建筑块。                  |
| 时间表   | 包含显示事件列表的积木块。                                 |
| 向导    | 使用这些构建模块一步一步输入信息。                             |
| 通知    | 包含用于不同通知的建筑块。                                 |
| 对齐    | 使用这些构建模块来对齐元素。                                |

要插入一个建筑块，请在页面上拖放所选的建筑块。

如果您想要读取某个建筑块上的文档，并了解更多关于如何和何时使用它的信息， 点击建筑块右上角的小图标。

![](attachments/page-editor/info-icon-building-blocks.png)

{{% alert type="info" %}}

Building Blocks 类别可能不同，因为Atlas UI 可以使用 Studio Pro自定义的。

{{% /报警 %}}

### 5.2 小部件 {#widgets}

部件是可以配置的单个用户界面元素。 You can [quickly configure](page-editor-widgets#quick-config) most of the non-custom widgets when adding them on a page. 欲了解更多信息，见 [小部件](page-editor-widgets)。

{{% alert type="info" %}}

您可以在 [部件概述](settings-widget-overview) 中更新部件。

{{% /报警 %}}

## 6 个属性选项卡 {#page-editor-properties}

**属性** 标签显示当前选中元素的属性，并根据此元素而有所不同。

{{% image_container width="300" %}}![](attachments/page-editor/properties.png)
{{% /image_container %}}


## 7 阅读更多

* [数据视图 & 列表视图属性](page-editor-data-view-list-view)
