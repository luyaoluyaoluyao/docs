---
title: "单选按钮"
parent: "输入小部件"
menu_order: 50
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/radio-buttons.pdf)。
{{% /报警 %}}

## 1 导言

●{% alert type="warning" %}}本机移动页面不支持无线电按钮小部件。{%/提醒 %}}

**单选按钮** 用于显示或可选显示。 允许最终用户编辑 [数据类型](data-types) *布尔值* 或 *枚举* 的属性值。

当页面显示给最终用户时，列出了所有可能的值， 与选中值旁边的一个填充的圆圈和未选中值旁边的一个空圆。 只能选择一个值 — — 选择另一个值 取消当前值。 例如：

![](attachments/radio-buttons/radio-buttons-displayed.png)

单选按钮必须放置在 [数据小部件](data-widgets) 中，并显示该小部件检索到的对象的属性。 要显示的属性名称显示在无线电按钮部件中，方括号和彩色蓝色。

例如，下面的图片包含两套无线电按钮。  第一种情况允许最终用户看到和设置。 指明联系此人的首选时间的枚举值(**首选联系人**)。 第二个选项允许最终用户查看并设置一个布尔值表示这是否是一个 **个人** 联系人。

![](attachments/radio-buttons/radio-buttons.png)

## 2 属性

下面的图像显示了单选按钮属性的示例：

{{% image_container width="250" %}}![](attachments/radio-buttons/radio-buttons-properties.png)
{{% /image_container %}}

单选按钮属性由以下部分组成：

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

### 2.6 一般部分{#general}

#### 2.6.1 方向

此属性定义是否将无线电按钮渲染为 **水平** 或 **垂直** 列表。

默认值： *水平*

### 2.7 标签部分{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.8 验证部分{#validation}

{{% snippet file="refguide8/widget-validation-link.md" %}}

### 2.9 可见性部分{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
