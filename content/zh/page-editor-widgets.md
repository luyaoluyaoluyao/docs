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

部件是可以配置的单个用户界面元素。 部件的例子可以是容器、下拉菜单或不同类型的按钮。

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

| 小部件类别                                           | 描述                                                                                                                                                                  |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 数据容器                                            | 包含 [个数据视图](page-editor-data-view-list-view) (显示一个对象内容的起点)，  [列表视图](page-editor-data-view-list-view) (显示对象列表内容的起点) 和一个 [数据网格](page-editor-data-grid) (显示一个表格式的对象列表)。 |
| [结构](page-editor-widgets-structure)             | 包含预设的布局网格，包含一定数量的列和小部件来控制放置部件。                                                                                                                                      |
| [输入元素](page-editor-widgets-input-elements)      | 包含可以用于输入数据的元素。                                                                                                                                                      |
| [文本](page-editor-widgets-text)                  | 包含文本显示部件。                                                                                                                                                           |
| [图像 & 文件](page-editor-widgets-images-and-files) | 包含帮助您显示图像、上传或下载文件和图像的部件。                                                                                                                                            |
| [按钮](page-editor-widgets-buttons)               | 包含一般动作的按钮，如打开或关闭一个页面，调用微流程，签名用户，打开链接。                                                                                                                               |
| [数据按钮](page-editor-widgets-buttons)             | 包含操作数据并用于创建或删除对象、保存或取消更改的按钮。                                                                                                                                        |
| [工作流按钮](page-editor-widgets-buttons)            | 包含与 [工作流](workflows) 相关且用于调用工作流的按钮， 完成或显示一个 [用户任务](workflows-user-task)，显示一个工作流页面。                                                                                  |
| [Menus](/refguide/menu-widgets)                 | 包含菜单创建部件。 目前，这些部件只能在 Studio Pro中配置。                                                                                                                                 |
| 附加组件                                            | 包含之前安装在应用程序中的所有自定义小部件。 如果部件无法与市场匹配，它们将会显示在附加组件中。                                                                                                                    |
| 图表                                              | 包含不同的图表。 此类别由 [市场小部件](#app-store-widgets) 组成。                                                                                                                       |
| 显示                                              | 包含在页面上显示变化元素的小部件，例如地图或进度栏。 此类别由 [市场小部件](#app-store-widgets) 组成。                                                                                                     |
| 列表视图控制                                          | 包含列表视图的控件。 此类别由 [市场小部件](#app-store-widgets) 组成。                                                                                                                     |

## 5 部件 {#widgets-by-origin}

工作室的小部件可以按原产地划分，如下表所示：
作为应用程序模板一部分的小部件，或由您或您的团队通过Studio Pro在本地创建的小部件。 关于开发小部件的更多信息，请参阅 [构建插件插件](/howto/extensibility/pluggable-widgets) 如何去开发小部件。 作为规则本地小部件将被列入 **附加组件** 类别。 欲了解更多分类信息，请按类别</a> 部分查看 部件。</td> 

</tr> </tbody> </table> 



## 添加市场小部件

您可以直接在工作室的 **小部件** 标签中下载市场小部件，从而将其添加到您的应用中。 这些小部件是市场上所有可用的小部件的子集：您只能下载已批准在工作室使用的小部件。 如果有更新，您也可以更新。

要添加市场小部件，请执行以下操作：

1. 打开 **小部件** 标签页。

2.  做以下一件： <br />
   
   a. 使用 **查看市场小部件** 选项查找一个类别并点击它。  <br />
   
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
