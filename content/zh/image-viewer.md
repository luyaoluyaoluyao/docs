---
title: "图像查看器"
parent: "文件小部件"
---


图像查看器可以用来显示图像或缩略图。

{{% alert type="info" %}}

![](attachments/pages/image-viewer.png) 此图像查看器显示产品图像。

{{% /报警 %}}

图像查看器必须放置在数据视图或模板网格中。

## 共同属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 数据源属性

### 实体(路径)

实体(路径)属性指定在图像查看器中显示哪个实体。 它从数据视图实体开始，必须以System.Image或其专门化结束。 如果数据视图实体本身是一个专门化的 System.Image 你也可以在图像查看器上使用这个实体。

## 事件

### 点击时

此属性指定了当点击图像时发生的情况：

| 值       | 含义        |
| ------- | --------- |
| 不执行任何操作 | 没有发生任何事情。 |
| 调用微流    | 执行指定的微流。  |
| 大化      | 图像以全尺寸显示。 |

_默认值：_ 不执行任何操作

### 微流程(在'调用微流程'的情况下)

此属性指定图像被点击时将执行的微流。

### 微流程设置(在“调用微流程”中)

点击设置指定将传递给微流程的参数，无论是否显示进度条，以及更多。

查看 [正在启动微流](starting-microflows)。

## 常规属性

### 默认图像

如果没有上传图像，这是显示的图像。

{{% snippet file="refguide7/Image+Width+Unit.md" %}}

_默认值_: 百分比

{{% snippet file="refguide7/Image+Width.md" %}}

_默认值_: 100

{{% snippet file="refguide7/Image+Hight+Unit.md" %}}

_默认值_: 自动

{{% snippet file="refguide7/Image+Height.md" %}}

_默认值_: 不适用

{{% snippet file="refguide7/Image+Responve.md" %}}

### 显示

此属性表示是否显示生成的缩略图或完整图像。

_默认值：_ 缩略图

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 相关文章

*   [数据视图](data-view)
*   [实体](实体)
