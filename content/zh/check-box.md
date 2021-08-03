---
title: "复选框"
parent: "输入小部件"
menu_order: 40
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/check-box.pdf)。
{{% /报警 %}}

## 1 导言

**复选框** 用于显示或可选显示。 允许最终用户编辑 [数据类型](data-types) *布尔值* 的属性。 如果值是真的，它会显示一个勾画，如果它是假的，则保持空。

●{% alert type="info" %}}在本机移动应用程序中，复选框部件作为toggle。{%/提醒 %}}

必须将复选框放入 [数据部件](data-widgets) 并显示从该部件检索到的对象的属性。 要显示的属性名称显示在复选框部件中，方括号和彩色蓝色。

例如，此复选框允许您查看并设置是否有人订阅了您的新闻。

![](attachments/check-box/check-box.png)

## 2 属性

下面的图像显示了复选框属性的示例：

{{% image_container width="250" %}}![](attachments/check-box/check-box-properties.png)
{{% /image_container %}}

复选框属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [编辑性](#editability)
* [事件](#events)
* [标签](#label)
* [可见性](#visibility)

### 2.1 共同部分{#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 数据源部分{#data-source}

{{% snippet file="refguide8/data-source-section-link.md" %}}

### 2.3 设计属性部分{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.4 可编辑性部分{#editability}

{{% snippet file="refguide8/editability-section-link.md" %}}

### 2.5 事件部分{#events}

#### 2.5.1 更改时{#on-change}

更改属性指定了离开部件时要执行的动作， 通过使用 <kbd>Tab</kbd> 键，或点击另一个部件，在值被更改后再点击。

{{% snippet file="refguide8/events-section-link.md" %}}

#### 2.5.2 输入时

输入小部件时指定了一个执行的动作。 要么使用 <kbd>Tab</kbd> 键，要么用鼠标点击它。

{{% snippet file="refguide8/events-section-link.md" %}}

#### 2.5.3 请假

请假属性指定了离开部件时要执行的动作， 要么使用 <kbd>Tab</kbd> 键，要么点击另一个部件。

This differs from the [On change](#on-change) property in that the event will always be triggered, even if the value has not been changed.

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.6 标签部分{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.7 可见性部分{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
