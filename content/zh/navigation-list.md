---
title: "导航列表"
parent: "容器部件"
menu_order: 70
tags:
  - "studio pro"
  - "导航列表"
  - "容器部件"
  - "小部件"
---

{{% alert type="warning" %}}
本地移动页面不支持导航列表小部件。
{{% /报警 %}}

## 1 导言

当用户点击此行时，导航列表可以用来将动作附加到整个行。 此行称为导航列表项目。

例如，单击一行可以打开页面，单击另一行可以执行微流。

![导航列表](attachments/container-widgets/navigation-list.png)

## 2 属性

导航列表属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![导航列表属性](attachments/container-widgets/navigation-list-properties.png)
{{% /image_container %}}

导航列表属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 可见科 {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 导航列表项

导航列表中的一行是一个导航列表项。 You can set a separate **On click** event for each row of the navigation list.

### 3.1 导航列表项属性

#### 3.1.1 共同部分

{{% snippet file="refguide/common-section-link.md" %}}

#### 3.1.2 一般部分

在 **常规** 部分中，您可以设置每个导航列表项的单击事件。 点击事件定义了用户点击行时执行的操作。 关于点击事件的更多信息，见 [点击事件 & 事件部分](on-click-event)

{{% alert type="info" %}}

微流设置为单击导航列表项目的事件，但没有 **执行**， **确认**, 或 **高级** 微流程设置。 关于调用微流程的更多信息，见 [点击事件 & 事件部分](on-click-event#call-microflow)

{{% /报警 %}}

#### 3.1.3 可见性科

{{% snippet file="refguide/visibility-section-link.md" %}}

## 4 阅读更多

* [页](page)
* [容器部件](容器部件)
* [页面编辑器中常见的属性](common-widget-properties)