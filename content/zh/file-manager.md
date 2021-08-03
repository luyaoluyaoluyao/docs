---
title: "文件管理器"
parent: "文件小部件"
---


文件管理器用于上传和/或下载文件。

{{% alert type="info" %}}

![](attachments/pages/file-manager.png)

{{% /报警 %}}

必须将其置于与实体System.FileDocument 或其专门化相关的数据视图内。

## 常规属性

### 类型

此属性表示终端用户如何与文件管理器交互。

| 值    | 描述                |
| ---- | ----------------- |
| 上传   | 文件管理器只能用于上传文件。    |
| 下载   | 文件管理器只能用于下载文件。    |
| 两者都是 | 文件管理器可以用于上传和下载文件。 |

_默认值：_

### 最大文件大小(MB)

此属性决定了上传文件的最大大小(以兆字节为单位)。

_默认值：_ 5

### 允许的扩展

您可以指定允许上传的文件扩展名。 如果没有指定扩展名, 则允许所有文件扩展名。 用半冒号分隔多个扩展，例如 `txt;doc`

如果选择了一个不允许的扩展名文件, 系统文本(文件管理器 > 不正确的文件扩展名) 将在文件管理器下显示。

### 在浏览器中显示文件

此属性表示该文件是否会在浏览器中显示，而不是下载。

_默认值：_ False

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
