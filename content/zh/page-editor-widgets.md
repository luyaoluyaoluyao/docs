---
title: "小部件"
category: "页 次"
description: "在 Mendix Studio 中描述小部件。"
tags:
  - "工作室"
  - "页面编辑器"
  - "页面"
  - "小部件"
---

## 1 导言

小部件是可以配置的单个用户界面元素：例如，下拉菜单或不同类型的按钮。

{{% image_container width="300" %}}![](attachments/page-editor-widgets/widgets-examples.png)
{{% /image_container %}}

工作室中的部件按类别分组，并可按其来源分类。

## 2 视图小部件

要在 Mendix Studio 中查看小部件，请执行以下操作：

1. 点击左侧菜单栏中的 **页面** 图标。

2. 在显示的应用页面列表中，选择您想要打开的页面并单击它。

3. 在 **工具箱** 标签页中， **小部件** 默认打开.

   ![](attachments/page-editor-widgets/toolbox-widgets.png)

## 3 个部件属性快速配置 {#quick-config}

大多数非自定义部件都可以快速配置属性。 这意味着当在页面上添加这些小部件时，他们的属性可以在弹出窗口中配置。

一旦你拖放小部件，它旁边就会出现一个小的弹出窗口。 您可以设置小部件运行所必需的属性，而不会导致 [一致性错误](consistency-errors) 以及其他常用属性来帮助您快速配置小部件。 然而，您可以随时从 **属性** 标签中配置所有属性。

例如，快速配置数据网格的数据源可以帮助您在预览或发布您的应用时避免一致性错误， 您可以稍后配置其余属性。

![](attachments/page-editor-widgets/quick-config.png)

当您开始与页面或菜单项交互时，弹出窗口将会消失。 如果您开始点击页面上的元素，或者如果您打开 **Toolbox**， **属性**, **Buzz**。 要再次访问快速配置弹出窗口，请点击小部件右上角的装备图标：

![](attachments/page-editor-widgets/quick-widget-icon.png)

## 4 个小部件 {#widget-categories}

工作室的小部件被分为当您打开 **小部件** 标签页时可以看到的类别。

{{% image_container width="350" %}}![](attachments/page-editor-widgets/widgets-categories.png)
{{% /image_container %}}

下面的表格描述了小部件类别：

| 小部件类别                                      | 描述                                                             | 链接到更多详细文档                                                                                   |
| ------------------------------------------ | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| 数据容器                                       | 包含数据视图 (显示一个对象内容的起点) 列表视图(显示对象列表内容的起点) 和一个数据网格 (显示一个表格式的对象列表)。 | [数据视图 & 列表视图属性](page-editor-data-view-list-view)<br />[数据网格属性](page-editor-data-grid) |
| [结构](page-editor-widgets-structure)        | 包含预设的布局网格，包含一定数量的列和小部件来控制放置部件。                                 | [结构部件](page-editor-widgets-structure)                                                       |
| [输入元素](page-editor-widgets-input-elements) | 包含可以用于输入数据的元素。                                                 | [输入元素部件](page-editor-widgets-input-elements)                                                |
| [文本](page-editor-widgets-text)             | 包含文本显示部件。                                                      | [文本部件](page-editor-widgets-text)                                                            |
| [图像](page-editor-widgets-images)           | 包含图像显示部件。                                                      | [图像部件](page-editor-widgets-images)                                                          |
| [按钮](page-editor-widgets-buttons)          | 包含了放置在页面上的各种按钮。                                                | [按钮部件](page-editor-widgets-buttons)                                                         |
| [Menus](/refguide/menu-widgets)            | 包含菜单创建部件。 目前，这些部件只能在 Studio Pro中配置。                            | [菜单部件](/refguide/menu-widgets) 在 *Studio Pro 指南*                                            |
| 附加组件                                       | 包含之前安装在应用程序中的所有自定义小部件。 如果部件无法与市场匹配，它们将会显示在附加组件中。               |                                                                                             |
| 图表                                         | 包含不同的图表。 此类别由市场部件组成。                                           | 第 [部分 4 个小部件（按起源分类](#widgets-by-origin)                                                     |
| 显示                                         | 包含在页面上显示变化元素的小部件，例如地图或进度栏。 此类别由市场部件组成。                         | 第 [部分 4 个小部件（按起源分类](#widgets-by-origin)                                                     |
| 列表视图控制                                     | 包含列表视图的控件。 此类别由市场部件组成。                                         | 第 [部分 4 个小部件（按起源分类](#widgets-by-origin)                                                     |

## 5 部件 {#widgets-by-origin}

工作室的小部件可以按原产地划分，如下表所示：

| 类型    | 描述                                                                                                                                                                                 | 始发地                                                             |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| 默认小部件 | 默认情况下包含在您的应用程序的小部件，在右上角没有信息图标。                                                                                                                                                     | 在开发者门户中创建的应用。 关于开发者门户网站的更多信息，见 [开发者门户](/developerportal/index)。 |
| 市场部件  | 您可以直接从工作室下载到应用的小部件。 某些应用市场小部件已经在您的应用中。 这种小部件的信息图标在 **工具箱** 窗口小部件右上角。 <br />欲了解更多关于市场的信息，见 [市场概览](/appstore/general/app-store-overview)。                                      | [市场](/appstore/)                                                |
| 本地小部件 | 作为应用程序模板一部分的小部件，或由您或您的团队通过Studio Pro在本地创建的小部件。 关于开发小部件的更多信息，请参阅 [自定义小部件开发](/howto7/widget-development/)。 作为规则本地小部件将被列入 **附加组件** 类别。 欲了解分类的更多信息，请参阅 [3 类小部件](#widget-categories) 类。 | 开发者门户网站/Studio Pro 中创建的应用程序                                     |

## 添加市场小部件

您可以直接在工作室的 **小部件** 标签中下载市场小部件，从而将其添加到您的应用中。 这些小部件是市场上所有可用的小部件的子集：您只能下载已批准在工作室使用的小部件。 如果有更新，您也可以更新。

要添加市场小部件，请执行以下操作：

1. 打开 **小部件** 标签页。

2.  做以下一件： <br />

    a. 使用 **查看 App Store 小部件** 选项查找一个分类并点击它。  <br />

    {{% image_container width="300" %}}![](attachments/page-editor-widgets/view-app-store-widgets.png)
 {{% /image_container %}}<br />

    b. 会议文件。  在 **搜索** 字段中开始输入类别或特定部件的名称。 <br />

    ![](attachments/page-editor-widgets/slider.png)

3.  点击云图标下载小部件并将其添加到您的应用中。

    ![](attachments/page-editor-widgets/app-store-download.png)

小部件现在被添加到您的应用中，您可以简单地拖放到页面上来使用。 您也可以在 **应用设置** 中查看此部件的设置。  关于您应用中管理小部件的更多信息，请参阅 [设置](settings)。

{{% alert type="info" %}}

一些类似的小部件被包装在一起：下载其中一个小部件也会导致其他小部件被下载。 例如，下载一行图将会给您所有的图表部件。

{{% /报警 %}}

## 7 阅读更多

* [页 次](page-editor)
* [设置](设置)
* [市场概览](/appstore/general/app-store-overview)
