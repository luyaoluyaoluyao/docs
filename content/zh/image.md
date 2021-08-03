---
title: "图片"
parent: "普通小部件"
menu_order: 20
tags:
  - "studio pro"
  - "图片"
  - "图像部件"
aliases:
  - /refguide/image-property.html
---

## 1 导言

图像部件可以用于在页面、布局或代码片段上显示静态图像。

例如，您可以配置一个图片单击一个包含客户详细信息的页面：

![图像示例](attachments/common-widgets/image-example.png)

{{% alert type="info" %}}

If you want to dynamically show different images based on data, you need to add [image viewer](image-viewer) on your page.

{{% /报警 %}}

## 2 属性

下面的图像是图像属性的示例：

{{% image_container width="300" %}}![图像属性](attachments/common-widgets/image-properties.png)
{{% /image_container %}}

图像属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [事件](事件)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 事件科 {#events}

关于事件部分及其属性的信息，见 [点击事件 & 事件部分](on-click-event)

### 2.4 一般部分 {#general}

#### 2.4.1 图像

此部件显示的文件名。 关于何时使用图像和支持格式的更多信息，请参阅 [图像](images)。

#### 2.4.2 Width Unit

图像的宽度。 该属性的可能值见下表：

| 值          | 定 义                                                |
| ---------- | -------------------------------------------------- |
| 自动  *(默认)* | 使用给定图像的宽度。                                         |
| Pixels     | 他的宽度以若干像素为单位。 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。 |
| 百分比        | 宽度以原始宽度的百分比表示。 它可以大于其原始宽度，在这种情况下图像被拉伸了             |

●{% alert type="info" %}}本机移动页面不支持此属性。{%/提醒 %}}

#### 2.4.3 Width

指定图像宽度以像素或百分比。 此选项仅在 **像素** 或 **上面所述 **宽度单位** 被选中的百分比** 时才显示。

默认： *不适用*

#### 2.4.4 高度单位

图像的高度。 该属性的可能值见下表：

| 值          | 定 义                                                |
| ---------- | -------------------------------------------------- |
| 自动  *(默认)* | 使用给定图像的高度                                          |
| Pixels     | 以一些像素为单位指定高度. 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。 |
| 百分比        | 高度以原始高度的某个百分比来指定。 它可以大于原来的高度，在这种情况下，图像会被拉伸。        |

●{% alert type="info" %}}本机移动页面不支持此属性。{%/提醒 %}}

#### 2.4.5 高度

指定图像宽度以像素或百分比。 此选项仅在 **像素** 或 **上面所述 **宽度单位** 被选中的百分比** 时才显示。

默认： *不适用*

#### 2.4.6 回应

此属性影响图像的缩放。 如果值为“是”，图像将永远不会超过原来的大小。 它可能变得更小。 如果值为“否”，图像可能会变得既大于也小于原来的大小。

默认： *是*

●{% alert type="info" %}}本机移动页面不支持此属性。{%/提醒 %}}

### 2.5 可见性部分 {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 转换为图像查看器

您可以将图像转换为允许您显示动态数据的图像查看器。 欲了解更多关于图像查看器及其属性的信息，请参阅 [图像查看器](image-viewer)。

要将图像部件转换为图像查看器，请执行以下操作：

1. 选择页面上的图像小部件并右键单击它。
2. 从操作列表中选择 **转换为图像查看器**。

图像部件被转换为图像查看器，您可以进行配置。

## 4 阅读更多

* [页](page)
* [常见小部件](普通小部件)
* [页面编辑器中常见的属性](common-widget-properties)


