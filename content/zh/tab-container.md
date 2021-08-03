---
title: "标签容器"
parent: "容器部件"
menu_order: 40
tags:
  - "studio pro"
  - "标签容器"
  - "tab page"
  - "容器部件"
  - "小部件"
aliases:
  - /refguide/tab-page.html
---

## 1 导言

标签容器用于显示按标签分类的信息。 如果必须显示的信息数量大于屏幕上的空间数量，这将非常有用。

![标签容器](attachments/container-widgets/tab-container.png)

## 2 属性

标签容器属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![标签容器属性](attachments/container-widgets/tab-container-properties.png)
{{% /image_container %}}

标签容器属性由以下章节组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 可见科 {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 Tab Page {#tab-page}

标签容器包含一个或多个您放置小部件的标签页。 例如，标签页可以包含一个网格订单。

### 3.1 特定页数属性

#### 3.1.1 Default Tab Page

**默认标签页** 定义打开页面时显示哪个标签页。 如果没有标签被设置为默认标签，将显示第一个标签页。

默认： *False*

#### 3.1.2 显示时刷新 {#refresh}

**在显示时刷新** 表示标签页的内容是否应该在显示标签页时刷新。 如果您知道什么都不会影响标签页上的信息，将此属性设置为 *没有*。

默认： *True*

{{% alert type="info" %}}
本机移动页面不支持此属性。
{{% /报警 %}}

## 4 阅读更多

* [页](page)
* [容器部件](容器部件)
* [页面编辑器中常见的属性](common-widget-properties)
