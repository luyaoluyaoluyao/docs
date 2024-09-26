---
title: "图片上传器"
parent: "文件小部件"
tags:
  - "studio pro"
  - "图片上传器"
  - "文件小部件"
  - "小部件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/image-uploader.pdf)。
{{% /报警 %}}

●{% alert type="warning" %}}。本地移动页面不支持图像上传小部件。{%/提醒 %}}

## 1 导言

图像上传器用于上传图片到服务器。 它还生成了上传图像的缩略图。 上传的图像或缩略图可以由图像查看器显示。 必须将其置于与实体系统图像或其专门化相连接的数据视图中。

在下面的示例中，图像上传器被放置在嵌套数据视图中 ( *配置* 实体是一个专业化的 System.Image):

![图片上传器](attachments/file-widgets/image-uploader.png)

## 2 属性

图像上传属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![图像上传器属性](attachments/file-widgets/image-uploader-properties.png)
{{% /image_container %}}

图像上传属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [编辑性](#editability)
* [A. 概况](#general)
* [标签](#label)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 可编辑部分 {#editability}

{{% snippet file="refguide8/editability-section-link.md" %}}

### 2.4 一般部分 {#general}

#### 2.4.1 最大文件大小(MB)

**最大文件大小(MB)** 决定可上传的文件的最大大小(以兆字节为单位)。

默认： *5*

#### 2.4.2 允许的扩展 {#allowed-extensions}

您可以指定用户可以上传的文件扩展名。 如果没有指定扩展名, 则允许所有文件扩展名。 用半冒号分隔多个扩展(例如， `txt;doc`)。

如果选择了一个不允许的扩展名文件, a [系统文本](system-texts) for **File Manager/image viewer** > **错误：不正确的文件扩展名** 将显示在文件管理器下。

#### 2.4.3 缩略图宽度

**缩略图宽度** 决定生成的缩略图的像素宽度。 然而，在缩略图生成期间，图像的纵横比将保持不变。

#### 2.4.4 缩略图高度

**缩略图高度** 决定生成的缩略图的像素高度。 然而，在缩略图生成期间，图像的纵横比将保持不变。

### 2.5 标签部分 {#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.6 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [文件部件](文件小部件)
* [页面编辑器中常见的属性](common-widget-properties)
