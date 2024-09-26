---
title: "文件管理器"
parent: "文件小部件"
tags:
  - "studio pro"
  - "文件管理器"
  - "文件小部件"
  - "小部件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/file-manager.pdf)。
{{% /报警 %}}

●{% alert type="warning" %}}。本地移动页面不支持文件管理器小部件。{{% /提醒 %}}

## 1 导言

文件管理器用于上传和/或下载文件。

![文件管理器](attachments/file-widgets/file-manager.png)

必须将其置于与实体System.FileDocument 或其专门化相关的数据视图内。

{{% alert type="info" %}}
当通过文件管理器上传文件时，文件文件对象将立即执行。
{{% /报警 %}}

## 2 属性

下面的图像是文件管理器属性的示例：

{{% image_container width="250" %}}![文件管理器属性](attachments/file-widgets/file-manager-properties.png)
{{% /image_container %}}

文件管理器属性由以下部分组成：

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

#### 2.4.1 Type

**类型** 属性表示最终用户将如何使用文件管理器。

| 值          | 描述                |
| ---------- | ----------------- |
| 上传         | 文件管理器只能用于上传文件。    |
| 下载         | 文件管理器只能用于下载文件。    |
| 两者都 *(默认)* | 文件管理器可以同时上传和下载文件。 |

#### 2.4.2 最大文件大小 (MB)

**最大文件大小(MB)** 决定可上传的文件的最大大小(以兆字节为单位)。

默认： *5*

#### 2.4.3 允许的扩展

您可以指定用户可以上传的文件扩展名。 如果没有指定扩展名, 则允许所有文件扩展名。 用半冒号分隔多个扩展，例如 `txt;doc`

如果选择了一个不允许的扩展名文件, a [系统文本](system-texts) for **File Manager/image viewer** > **错误：不正确的文件扩展名** 将显示在文件管理器下。

#### 2.4.4 在浏览器中显示文件

**在浏览器中显示文件** 表示是否会在浏览器中显示文件而不是下载。

默认： *False*

### 2.5 标签部分 {#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.6 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [文件部件](文件小部件)
* [页面编辑器中常见的属性](common-widget-properties)
* [系统文本](system-texts)
