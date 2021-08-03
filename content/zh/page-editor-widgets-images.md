---
title: "图像部件"
parent: "页面编辑器部件"
description: "在 Mendix Studio 中描述图像部件。"
menu_order: 30
tags:
  - "工作室"
  - "页面编辑器"
  - "图片"
  - "图像部件"
  - "小部件"
---

## 1 导言

图像 [小部件](page-editor-widgets) 用于向用户显示图像。

Mendix Studio中有两个图像部件：

* 图像 - 允许您在应用中显示静态(无更改)
*  动态图像 - 允许您在应用程序中显示动态图像 (例如，每个客户不同的相关个人资料图片)

   {{% image_container width="350" %}}![](attachments/page-editor-widgets-images/image-widgets.png)
   {{% /image_container %}}

{{% alert type="info" %}}

您可以在部件属性中切换静态和动态图像。 欲了解更多信息，请参阅 [常规部分](#image-general)。

{{% /报警 %}}

## 2 一般部分 {#image-general}

您可以在 **常规** 部分中切换静态和动态图像。 除了设置图像本身，配置图像的宽度和高度，等等。

Before configuring settings in the **General** section for the **Dynamic Image**, keep in mind that it can only function inside a data container (a list view or a data view). 您可以在现有数据容器中放置部件； 或点击 **用新的数据视图** 在 **属性** 自动创建数据视图并放置输入元素。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-images/dynamic-image-data-view.png)
{{% /image_container %}}

**静态图像** 和 **动态图像** 可用的设置在下表中描述：

| 财产    | 该属性适用于： | 描述                                                                                                                                                                                                                              |
| ----- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 图像来源  | 静态和动态图像 | 在静态和动态图像之间切换。                                                                                                                                                                                                                   |
| 实体    | 动态图像    | 指定在动态图像中显示哪个实体。 您只能为动态图像设置一个实体，如果该实体被配置为Studio Pro中的图像。 更多信息 查看 [常规属性](/refguide/entities#entities-general-properties) 在 *实体* 在 *Studio Pro 指南* 和 [动态图像 (文档模板)](/refguide/dynamic-image-document-template) 在 *Studio Pro 指南* 中。 |
| 图片    | 静态图像    | 设置将显示给最终用户的图像。                                                                                                                                                                                                                  |
| 默认图像  | 动态图像    | 如果没有上传图像，这是显示的图像。                                                                                                                                                                                                               |
| 宽度单位  | 静态和动态图像 | 图像宽度可以通过以下方式指定：  <br /><ul><li>**自动** ——使用给定图像的宽度。</li><li>**Pixels** - 以若干像素指定宽度。 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。</li><li>**百分比** - 以原始宽度的百分比指定宽度。 它可以大于原来的宽度，在这种情况下，图像会被拉伸。</li></ul><br />Default value for **Width Unit**: Auto                                                                                                                        |
| Width | 静态和动态图像 | **宽度** 选项仅在 **像素** 或 **为 **宽度单位** 选择百分比** 时才显示。 它以像素或百分比指定图像宽度。                                                                                                                                                                 |
| 高度单位  | 静态和动态图像 | 图像的高度可以通过以下方式指定：  <br /><ul><li>**自动** ——使用给定图像的高度。</li><li>**Pixels** - 以多个像素来指定高度. 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。</li><li>**百分比** - 高度以原始高度的百分比指定。 它可以大于原来的高度，在这种情况下，图像会被拉伸。</li></ul><br />**高度单位**的默认值：自动                                                                                                                                              |
| 高度    | 静态和动态图像 | **高度** 选项仅在 **像素** 或 **** 被选定为 **高度单位** 时才显示。 它指定图像的像素高度或百分比。                                                                                                                                                                   |

## 3 事件部分

您可以在 **事件** 部分中选择 **点击动作**。 **点击动作** 定义用户点击图像时执行什么操作。

### 3.1 共同财产

The static image and the dynamic image share the properties in the **Events** section, except for one property that is [specific for the dynamic image](#events-dynamic-image).

欲了解更多关于 **事件** 部分的静态和动态图像，请参阅 [小部件中的事件部分](page-editor-widgets-events-section)

### 3.2 动态图像特定属性 {#events-dynamic-image}

动态图像有一个特定的点击操作 **放大点击**。 当用户点击时将显示全尺寸的图像。 此属性覆盖其他点击动作。

## 4 设计部分

关于 **设计** 部分及其属性的信息，请参阅 [小部件中的设计部分](page-editor-widgets-design-section)。

## 5 阅读更多

* [页 次](page-editor)
* [小部件](页面编辑器部件)
