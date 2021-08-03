---
title: "图片上传器"
parent: "文件小部件"
---


图像上传器用于上传图片到服务器。 它还生成了上传图像的缩略图。 上传的图像或缩略图可以通过图像查看器显示。

{{% alert type="info" %}}

![](attachments/pages/image-uploader.png) 图像上传器放置在嵌套数据视图中。 简介实体是系统图像专业化实体。

{{% /报警 %}}

图像上传器必须放置在连接到实体系统的数据视图或其专门化中。

## 常规属性

### 最大文件大小(MB)

使用此属性，您可以指定上传图像的最大文件大小(以megabytes为单位)。

_默认值：_ 5

### 允许的扩展

您可以指定允许上传的文件扩展名。 如果没有指定扩展名, 则允许所有文件扩展名。 用半冒号分隔多个扩展，例如 `png;jpg`

如果选择了一个不允许的扩展名文件, 系统文本(文件管理器 > 不正确的文件扩展名) 将在文件管理器下显示。

### 缩略图宽度

此属性决定生成的缩略图的像素宽度。 然而，在缩略图生成期间，图像的纵横比将保持不变。

### 缩略图高度

此属性决定生成的缩略图的像素高度。 然而，在缩略图生成期间，图像的纵横比将保持不变。

{{% snippet file="refguid7/Label+Property.md" %}}

## 可编辑属性

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 共同属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 相关文章

*   [数据视图](data-view)
*   [实体](实体)
*   [社会联系](关联)
