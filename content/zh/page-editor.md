---
title: "页 次"
description: "在 Mendix Studio 中描述页面编辑器。"
menu_order: 20
tags:
  - "工作室"
  - "页面编辑器"
  - "页面"
---

## 1 导言

页面定义Mendix 应用程序的最终用户接口。 页面已在 *页面编辑器* 中创建和编辑。

要在 Mendix Studio 中查看您应用的 **页面** ，请点击 **页面** 在工作室左侧菜单栏中的图标。

{{% image_container width="300" %}}![](attachments/page-editor/pages-icon.png)
{{% /image_container %}}

{{% alert type="warning" %}}

工作室仅支持基于Atlas界面框架的应用。 关于Atlas界面的详细信息，见 [Atlas界面](/howto8/front-end/atlas-ui)。

{{% /报警 %}}

Every page is *based on* a layout and a template:

* **布局** — — 一个你放置你的页面的框架。 每个页面都基于一个布局。 例如， **Atlas_default** 或 **PopupLayout** 是您在创建页面时可以选择的布局。 布局定义此界面元素的位置和外观作为页面头和菜单栏。
* **模板** - 一个新页面的起始点。 每次您创建一个新页面， 您选择一个模板，取决于您想要在页面上显示的数据以及您想要显示的方式：一个列表 一个控制面板，一个表单。 根据您的选择，页面模板可以在它上有一些预定义的元素，例如图片列表、表格。 例如， **仪表板动作瓷块**, **列表默认**, **主详细信息** 是模板类型。

*页面的外观和结构* 由以下元素定义：

* **小部件** — — 单个用户界面元素。 欲了解更多信息，请参阅 [小部件](#widgets) 部分和 [小部件](page-editor-widgets)。
* **Building block** — — 预先配置的一组 *小部件* 可以加速构建你的页面和设计它的过程。 欲了解更多信息，请参阅 [Building Blocks](#building-blocks) 部分。

下图说明布局、模板和部件的功能：

![](attachments/page-editor/page-structure.png)

上述所有元素(布局、模板、部件和建筑块)都由Atlas界面提供动力。 关于Atlas界面的更多信息，见 [Atlas界面](/howto8/front-end/atlas-ui)。

## 2 执行基本函数 {#page-editor-basic-functions}

### 2.1 开放页面

打开工作室后，它会自动打开应用程序的主页。

要在 Studio 中打开一个页面, 请执行以下操作：

1. 点击左侧菜单栏中的 **页面** 图标。

2.  在显示的应用页面列表中，选择您想要打开的页面并单击它。

    {{% image_container width="400" %}}![](attachments/page-editor/opening-a-page.png)
    {{% /image_container %}}

所选页面已打开。

### 2.2 创建新页面 {#creating-new-page}

要在 Studio 中创建一个新的页面, 请执行以下操作:

1. 点击 **页面** 图标。

2.  单击显示侧面板右上角的 **新**。

    {{% image_container width="400" %}}![](attachments/page-editor/new-page.png)
    {{% /image_container %}}

3.  在 **创建新页面** 对话框框中，填写页面标题，选择一个布局和一个页面模板。

    ![](attachments/page-editor/create-new-page-dialog.png)

5. 点击 **创建**。

新页面已创建。

### 2.3 复制页

要复制一个现有的页面，请执行以下操作：

1. 点击左侧菜单栏中的 **页面** 图标。

2. 在侧面板中，单击椭圆图标并在下拉菜单中选择 **重复**

    {{% image_container width="400" %}}
![Duplicate Page](attachments/page-editor/duplicate-page.png)
{{% /image_container %}}

页面已重复。

### 2.4 复制并粘贴一个页面

要复制和粘贴一个页面，请做以下操作：

1. 点击左侧菜单栏中的 **页面** 图标。

2.  在侧面板中，单击椭圆图标并在下拉菜单中选择 **复制到剪贴板**：

    {{% image_container width="400" %}}
![复制页面](attachments/page-editor/copy-page.png)
{{% /image_container %}}

3. 打开工作室应用程序以粘贴页面并按 <kbd>Ctrl</kbd> +<kbd>V</kbd> 或 <kbd>Cmd</kbd> +<kbd>V</kbd>。

您的页面已粘贴。 欲了解工作室中复制/粘贴函数的更多信息，请在 *常规信息* 中查看 [复制/粘贴页面、微流和枚举](general#copy-paste-documents) 部分。

### 2.5 删除页面

若要删除工作室中的一个页面, 请执行以下操作之一：

1. 打开您想要删除的页面并按照下面的步骤：
    1. 打开 **属性** 选项卡。
    2. 点击 **在 **属性底部删除**** 标签。

    ![](attachments/page-editor/page-delete.png)

2. 点击左侧菜单栏中的 **页面** 图标并执行以下操作：

    1. 在侧面板中，单击椭圆图标并在下拉菜单中选择 **删除**

        {{% image_container width="400" %}}
![删除页面](attachments/page-editor/delete-page.png)
{{% /image_container %}}

所选页面已删除。

### 2.6 在页面上添加元素 {#adding-elements}

要在页面上添加元素，请执行以下操作：

1. 在 **工具箱**, 打开 [小部件](#widgets) 标签或 [构建块](#building-blocks) 标签页。
2. 选择一个你想要添加、拖放此元素到页面上的元素。

### 2.7 页面上显示元素

有两种方式可以查看元素及其 [属性](#page-editor-properties)：

* 点击页面上的元素
* 点击面包屑中的元素(详情请参阅 [Breadcrumb](#breadcrumb) 部分)

选中的元素用蓝边框标明。 此外，如果元素在数据容器内(数据视图或列表视图)，则将用数据容器图标表示：

{{% image_container width="400" %}}![](attachments/page-editor/input-widget-example.png)
{{% /image_container %}}

### 2.8 从一页删除元素

要从页面中删除元素，请执行以下操作之一：

* 选择此元素并按 <kbd>删除</kbd>
* 打开此元素的 **属性** 标签，点击 **在标签底部删除**

## 3 显示选项

位于页面左上角， **显示** 选项突出显示了具有 [条件可见性](page-editor-widgets-visibility-section) 配置给他们的项目。 点击眼睛图标启用此选项。 关于条件可见性及其工作方式的更多信息，见 [条件可见性部分](page-editor-widgets-visibility-section)。

## 4 Breadcrumb {#breadcrumb}

在工作室左下角的每个页面都显示面包屑。

面包屑服务两种功能：

* 在页面上显示选中项目的自下而上的布局。 例如，当您在页面上选择一个按钮时，您会看到它放在一个列中的容器中。  如果列在一行中，此行放置在页面的布局格子里：

    ![](attachments/page-editor/breadcrumb.png)

* 允许您选择页面上的元素并查看其属性。 要导航到页面和视图元素属性上的元素，请在面包屑导航中单击此元素。

## 5 Toolbox Tab

**工具箱** 显示了可以在页面上使用的工具。

此选项卡由以下内容组成：

* [小部件](#widgets)
* [构建块](#building-blocks)

### 5.1 部件 {#widgets}

部件是可以配置的单个用户界面元素。

You can [quickly configure](page-editor-widgets#quick-config) most of the non-custom widgets when adding them on a page. 关于如何配置小部件的更多信息，请参阅 [小部件](page-editor-widgets)。

您可以在 [部件概述](settings-widget-overview) 中更新部件。

### 5.2 建筑块 {#building-blocks}

建筑块由预设的小部件组成，可以让您更快地构建一个页面：

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

如果您想要读取某个建筑块上的文档，并了解更多关于如何和何时使用它的信息， 点击建筑块右上角的小图标。

![](attachments/page-editor/info-icon-building-blocks.png)

{{% alert type="info" %}}

建筑块类别可能不同，因为Atlas UI可以使用 Studio Pro自定义的。

{{% /报警 %}}

## 6 个属性选项卡 {#page-editor-properties}

**属性** 标签显示当前选中元素的属性，每个元素可能不同。

{{% image_container width="300" %}}![](attachments/page-editor/properties.png)
{{% /image_container %}}

For example, if you click **Layout**—which is the layout that you choose when [creating a page](#creating-new-page)—in the breadcrumb, properties will display reference information on page-related actions that you can perform, such as changing the page title and customizing pages' look:

{{% image_container width="300" %}}![](attachments/page-editor/layout.png)
{{% /image_container %}}

## 7 个此类别中的主要文档

* [小部件](page-editor-widgets) -- 描述不同类型的小部件
