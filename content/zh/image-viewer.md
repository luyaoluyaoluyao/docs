---
title: "图像查看器"
parent: "文件小部件"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/image-viewer.pdf)。
{{% /报警 %}}

## 1 导言

图像查看器可以用来显示图像或缩略图。 例如，您可以显示个人资料图片：

![](attachments/pages/image-viewer.png)

图像查看器必须放置在数据视图或模板网格中。

## 2 属性

图像查看器属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![图像查看器属性](attachments/file-widgets/image-viewer-properties.png)
{{% /image_container %}}

图像查看器属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [事件](#events)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分{#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 数据源部分 {#data-source}

#### 2.3.1 实体(临)

**实体 (路径)** 属性指定了哪些对象将会显示在图像查看器中。 它必须是一种系统图像或其专门化。 如果数据视图中的对象是一个专门化的 System.Image 您也可以在图像查看器中使用此对象。

### 2.4 事件部分 {#events}

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.5 一般部分{#general}

#### 2.5.1 Default Image

如果没有上传图像，这是显示的图像。

#### 2.5.2 Width Unit {#width-unit}

下表描述了指定图像宽度的可能方式：

| 值           | 定 义                                              |
| ----------- | ------------------------------------------------ |
| Pixels      | 宽度以若干像素为单位。 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。 |
| 百分比  *(默认)* | 宽度以原始宽度的百分比表示。 它可以大于原来的宽度，在这种情况下，图像会被拉伸。         |
| 自动操作        | 使用给定图像的宽度。                                       |

{{% alert type="info" %}}
本机移动页面不支持。
{{% /报警 %}}

#### 2.5.3 Width

此属性仅在 [宽度单位](#width-unit) 属性设置为 *像素* 或 *百分比* 时才显示。 此属性决定图像宽度，或者像素，或者百分比值。

默认： *0*

#### 2.5.4 高度单位 {#height-unit}

下表描述了指定图像高度的可能方式：

| 值          | 定 义                                                |
| ---------- | -------------------------------------------------- |
| Pixels     | 以一些像素为单位指定高度. 如果您同时指定宽度和高度，图像将自动缩放：比例将保持，图像将不会被拉伸。 |
| 百分比        | 高度以原始高度的某个百分比来指定。 它可以大于原来的高度，在这种情况下，图像会被拉伸。        |
| 自动  *(默认)* | 使用给定图像的高度                                          |

●{% alert type="info" %}}本机移动页面不支持此属性。{%/提醒 %}}

#### 2.5.5 高度

此属性仅在 [高度单位](#height-unit) 属性设置为 *像素* 或 *百分比* 时才显示。 此属性决定图像的高度，以像素或百分比表示。

默认： *0*

#### 2.5.6 回应

此属性决定图像的缩放方式。 如果值设置为 *是*，图像将永远不会大于原来的大小，但它可能变得更小。 如果值设置为 *没有*，则图像可能会变得既大于也小于原来的大小。

默认： *是*

#### 2.5.7 显示

此属性表示是否显示生成的缩略图或完整图像。

Default: *Thumbnail*

### 2.6 可见属性{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [文件部件](文件小部件)
* [页面编辑器中常见的属性](common-widget-properties)
