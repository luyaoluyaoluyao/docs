---
title: "文本区域"
parent: "输入小部件"
menu_order: 20
tags:
  - "studio pro"
---

## 1 导言

一个 **文本区域** 用于显示并且可选的。 允许最终用户编辑 [数据类型](data-types) *字符串* 的属性值。 它不同于 [文本框](text-box) ，因为值可以显示在几行上。

文本区域必须放置在 [数据部件](data-widgets) 中，并显示从该部件检索到的对象的属性。 要显示的属性名称显示在文本区域中，方括号和彩色蓝色。

For example, the following text area allows the end-user to see, and set, the **Notes** about a contact.

![](attachments/text-area/text-area.png)

## 2 属性

下面的图像是文本区域属性的示例：

{{% image_container width="250" %}}![](attachments/text-area/text-area-properties.png)
{{% /image_container %}}

文本区域属性由以下部分组成：

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

#### 2.6.1 自动扩展

●{% alert type="info" %}}增长自动属性不影响本机移动页面的行为。 在 iOSS 上，文本区域总是自动增长
{{% /报警 %}}

这个属性决定了文本区域是否自动增长取决于其中的文本数量。

默认： *否*

#### 2.6.2 线数

**行数** 根据行高度决定文本区域的大小。 如果文本区域的文本包含更多行，滚动条将使最终用户能够看到所有文本。 此属性仅在 **自动增加** 设置为 *没有* 时才使用。

默认： *5*

#### 2.6.3 计数器信息

{{% alert type="info" %}}Counter message is not supported on native mobile pages.{{% /alert %}}

这是在文本区域输入时显示的文本。 此文本有两个 [参数](text#parameters)。 第一个参数包含已经输入的字符数，第二个参数包含最大字符数。

例如，如果您使用的是计数器消息 `您已经使用了 {1} 个字符的 {2} 个字符。` 对于您的文本区域，最终用户将看到此消息显示在文本区域小部件下方：

![](attachments/text-area/counter-message.png)

#### 2.6.4 案文太长的信息

{{% alert type="info" %}}Text too long message is not supported on native mobile pages.{{% /alert %}}

当输入的字符数高于允许的最大字符数时，这是显示的文本。

#### 2.6.5 最大长度

此属性指定了可以在此文本区域输入的最大字符数。

| 值           | 描述                |
| ----------- | ----------------- |
| 属性长度 *(默认)* | 最大字符数与连接属性的最大长度相同 |
| 无限制         | 最大字符数是无限的         |
| 自定义         | 小部件属性中指定的最大字符数    |

#### 2.6.6 占位符文本

当没有输入文本或显示属性为空时，将显示占位符文本。

例如，它可以用来向最终用户说明应填写何种案文。

#### 2.6.7 自动完成

自动完成属性指定文本区域是否启用自动完成。 自动完成属性也提高了移动设备预填空域的能力。

●{% alert type="info" %}}此选项仅在本机页面中可用。{%/提醒 %}}
{{% alert type="info" %}}In Android when autocomplete is turned off it will remove support for new lines.{{% /alert %}}

### 2.7 标签部分{#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.8 验证部分{#validation}

{{% snippet file="refguide/widget-validation-link.md" %}}

### 2.9 可见性部分{#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
