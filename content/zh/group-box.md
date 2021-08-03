---
title: "组框"
parent: "容器部件"
menu_order: 30
tags:
  - "studio pro"
  - "组框"
  - "容器部件"
  - "小部件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/group-box.pdf)。
{{% /报警 %}}

●{% alert type="warning" %}}本机移动页面不支持群组窗口小部件。{{% /提醒 %}}

## 1 导言

一个组框可以用来一起视觉分组相关的小部件。 分组框显示为嵌套小部件周围的可选标题。 组框可以配置为折叠和动态扩展。

![](attachments/container-widgets/group-box.jpg)

## 2 属性

下面的图像显示了组框属性的示例：

{{% image_container width="300" %}}![群组框属性](attachments/container-widgets/group-box-properties.png)
{{% /image_container %}}

组框属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分 {#general}

#### 2.3.1 显示标题

**显示标题** 定义是否在组框上方显示页眉。

默认： *True*

#### 2.3.2 标题

此属性仅在 **显示页眉** 选项启用时才显示。 它定义了标题中显示的标题。

默认： *组框*

#### 2.3.3 可折叠性

此属性指定是否可以通过单击标题折叠组框，如果可以，它是否被折叠或扩展。 此属性仅在 **显示页眉** 启用时才显示。

此属性的可能值如下：

* **是 (开始扩展)**  *(默认)* - 当用户点击头部的一个负图标时，组框内的元素将会最初显示并折叠。
* **是 (开始折叠)** - 当用户点击标题中的加号图标时，组框内的元素将会被隐藏并被扩展
* **无** - 组框元素总是显示出来的，组框不能折叠。

### 2.4 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [容器部件](容器部件)
* [页面编辑器中常见的属性](common-widget-properties)


