---
title: "日期选择器"
parent: "输入小部件"
menu_order: 60
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/date-picker.pdf)。
{{% /报警 %}}

## 1 导言

**日期选择器** 用于显示并可选. 允许最终用户编辑 [数据类型](data-types) *日期和时间* 的属性值。 它使用 **工程设置的 **语言** 选项卡中设置的值** 向最终用户显示正确的本地化值。 使用 **语言** 与最终用户相关联的对象。

日期选择器必须放置在 [数据部件](data-widgets) 中，并显示从该部件检索到的对象的属性。 要显示的属性名称显示在日期选择器中，方括号和彩色蓝色。

例如，下一个日期选择器允许最终用户查看和设置客户的 **LastContacted** 日期。

![](attachments/date-picker/date-picker.png)

## 2 属性

以下图像显示日期选择器属性的示例：

{{% image_container width="250" %}}![](attachments/date-picker/date-picker-properties.png)
{{% /image_container %}}

日期选择器属性由以下部分组成：

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

#### 2.6.1 日期格式

日期格式决定日期选择器是否以日期、时间、日期和时间或自定义格式显示属性值。

这里选择的格式不影响数据的储存方式；在所有情况下，日期和时间都将被记录。 它仅仅影响数据的显示方式。 日期和/或时间格式还取决于数据最终用户的本地化(语言)。

日期格式的可能值如下：

* **日期** *(默认)*
* **时间**
* **日期和时间**
* **自定义** (详情见下面)

#### 2.6.2 习惯日期格式

如果您选择 **自定义** 作为日期格式(见上文)，此属性将决定如何格式化属性。 自定义日期格式是一个字符串，允许下面表格中的任何符号组合。 任何标点都将以字面形式呈现。

{{% snippet file="refguide8/custom-date-form-tokens.md" %}}

{{% alert type="info" %}}
即使一个自定义日期格式的日期选择器是可以编辑的。 只有当自定义格式代表一个完整日期时才显示日历下拉按钮 (即) 年 [`y`-`yyy`], 月 [`M`-`MMMM`], 月份和日 [`d`-`dd`] 代币都存在自定义格式)。
{{% /报警 %}}

#### 2.6.3 占位符文本

如果日期属性为空，则显示占位符文本。 它可以用来向最终用户说明预期的格式。

{{% alert type="warning" %}}
如果原生日期选择器可用(即iOS和安卓4.0及以上版本)，占位符文本将不会显示。
{{% /报警 %}}

### 2.7 标签部分{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.8 验证部分{#validation}

{{% snippet file="refguide8/widget-validation-link.md" %}}

### 2.9 可见性部分{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

*   [数据视图](data-view)
*   [属性](attributes)
