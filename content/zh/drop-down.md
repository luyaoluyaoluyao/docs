---
title: "下拉列表"
parent: "输入小部件"
menu_order: 30
tags:
  - "下拉列表"
  - "input"
  - "页面"
  - "小部件"
  - "枚举数"
  - "studio pro"
aliases:
  - /refguide/drop-down-widget.html
---

## 1 导言

**下拉** 用于显示并且可选的。 允许最终用户编辑 [数据类型](data-types) *枚举* 的属性值。

下拉菜单必须放置在 [数据部件](data-widgets) 中，并显示从该部件检索到的对象的属性。 要显示的属性名称显示在下拉框中，方括号和彩色蓝色。

{{% alert type="info" %}}
下拉菜单不应与 [引用选择器](reference-selector)混淆，它用于选择 [关联](associations) 到另一个对象。
{{% /报警 %}}

例如，下面的下拉允许最终用户查看和设置客户分配到的 **区域**。 **区域** 可能的值被保存在枚举中。

![](attachments/drop-down/drop-down.png)

## 2 属性

下拉属属性的示例在下面的图像中显示：

{{% image_container width="300" %}}![](attachments/drop-down/drop-down-properties.png)
{{% /image_container %}}

下拉属属性由以下部分组成：

* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [编辑性](#editability)
* [事件](#events)
* [A. 概况](#general)
* [标签](#label)
* [验证](#validation)
* [可见性](#visibility)

### 2.1 共同部分{#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 数据源部分{#data-source}

{{% snippet file="refguide/data-source-section-link.md" %}}

### 2.3 设计属性部分{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 可编辑性部分{#editability}

{{% snippet file="refguide/editability-section-link.md" %}}

### 2.5 事件部分{#events}

#### 2.5.1 更改时{#on-change}

更改属性指定了离开部件时要执行的动作， 通过使用 <kbd>Tab</kbd> 键，或点击另一个部件，在值被更改后再点击。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.5.2 输入时

输入小部件时指定了一个执行的动作。 要么使用 <kbd>Tab</kbd> 键，要么用鼠标点击它。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.5.3 请假

请假属性指定了离开部件时要执行的动作， 要么使用 <kbd>Tab</kbd> 键，要么点击另一个部件。

This differs from the [On change](#on-change) property in that the event will always be triggered, even if the value has not been changed.

{{% snippet file="refguide/events-section-link.md" %}}

### 2.6 一般部分{#general}

#### 2.6.1 空选项标题

空选项标题是显示给最终用户下拉菜单中的空选项的文本。 这是一个可翻译的文本。 欲了解更多详情，请参阅 [语言菜单](translatable-texts)。

为空选项添加一个标题可以提高应用程序的用户体验。 它还帮助最终用户使用屏幕阅读器轻松地操作应用程序。

例如，允许最终用户选择分配给客户的区域的下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式下拉式最终用户选择分配给客户的区域。 在 **区域** 的可能值被包含在枚举中， 可以有标题 `选择一个区域`。

![](attachments/drop-down/select-a-region.png)

### 2.7 标签部分{#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.8 验证部分{#validation}

{{% snippet file="refguide/widget-validation-link.md" %}}

### 2.9 可见性部分{#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
