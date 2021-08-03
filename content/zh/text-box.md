---
title: "文本框"
parent: "输入小部件"
menu_order: 10
tags:
  - "studio pro"
  - "数据"
---

## 1 导言

文本框用于显示并在可选情况下显示。 允许最终用户以文本形式编辑对象的属性值。 它可以用于显示以下 [数据类型](data-types) 的属性：

* Autonumber
* 小数
* 哈希字符串
* 整数
* 长
* 字符串

文本框必须放置在 [数据部件](data-widgets) 中，并显示从该部件检索到的对象的属性。 要显示的属性名称显示在文本框中，方括号和彩色蓝色。

例如，下面的文本框允许最终用户查看和设置客户的 **名称**。

![](attachments/text-box/text-box.png)

## 2 属性

文字框属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![](attachments/text-box/text-box-properties.png)
{{% /image_container %}}

文本框属性由以下部分组成：

* [无障碍环境](#accessibility)
* [常用的](#common)
* [数据源](#data-source)
* [设计属性](#design-properties)
* [编辑性](#editability)
* [事件](#events)
* [格式化](#formatting)
* [A. 概况](#general)
* [标签](#label)
* [验证](#validation)
* [可见性](#visibility)

### 2.1 辅助功能部分{#accessibility}

#### 2.1.1 自动完成

自动完成属性指定文本框是否启用自动完成。 自动完成属性也提高了浏览器使用用户首选值预先填充字段的能力。 关于这如何帮助您遵守无障碍指南的更多信息，请参阅 [网页内容无障碍指南(WCAG 2.1](https://www.w3.org/TR/WCAG21/#input-purposes)

### 2.2 共同部分{#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.3 数据源部分{#data-source}

{{% snippet file="refguide/data-source-section-link.md" %}}

### 2.4 设计属性部分{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.5 可编辑性部分{#editability}

{{% snippet file="refguide/editability-section-link.md" %}}

### 2.6 事件部分{#events}

#### 2.6.1 变化事件{#on-change}

更改事件属性指定了当值被更改并提交时将执行的动作。 当按 <kbd>输入</kbd> 键或离开小部件时，将提交一个值， 通过使用 <kbd>Tab</kbd> 键或点击另一个小部件。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.2 关于改变行为

The On Change Behaviour property lets users select how **on change** is handled via the following options Studio Pro:

* 当用户离开输入字段 (默认)
* 用户正在输入数据

##### 2.6.2.1 用户离开输入领域时(默认)

此选项将和以前版本Studio Pro一样工作。 Textbox 将在一个值与数据库中先前保存的值不相同且符合以下条件之一时应用更改：

* 输入按键时按下：这将在更改时触发并进入按键新闻事件
* 模糊度：这将在更改和休假事件时触发

这意味着用户无法在输入更改时触发一个事件。 此用例需要第二个选项： **用户输入数据**。

##### 2.6.2.2 用户输入数据时

此选项允许用户在输入更改时触发一个事件。 文本框将保存更改，如果值与数据库中先前保存的值不相同，如果最后一次更改是在配置的 **应用后(毫秒)** 时间长度后发生的。

使用 **当用户输入数据**时，用户现在可以调整一个又一个属性，名为 **Applied after (ms)** (上文描述)。 这将减少对更改事件的呼叫，从而提高应用性能。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.3 进入事件时

输入事件属性指定了当小部件输入时要执行的动作。 要么使用 <kbd>Tab</kbd> 键，要么用鼠标点击它。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.4 请假时

休假事件属性指定了离开部件时要执行的动作， 要么使用 <kbd>Tab</kbd> 键，要么点击另一个部件。

This differs from the [On change](#on-change) property in that the event will always be triggered, even if the value has not been changed.

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.5 Enter Key Press Event

输入按键事件属性指定了当焦点在小部件内并且按 <kbd>输入</kbd> 键时将执行的动作。 在一个 web 应用程序中，小部件将在执行操作后保持焦点。

{{% snippet file="refguide/events-section-link.md" %}}

### 2.7 格式部分{#formatting}

格式化部分仅适用于数字属性的显示方式。 这些是以下数据类型的属性：

* 小数
* 整数
* 长

{{% snippet file="refguide/numeric-form-link.md" %}}

### 2.8 一般部分{#general}

#### 2.8.1 以密码显示

数据类型 `字符串` 或 `哈希字符串` 的属性可以隐藏其值。 这可以用于密码，例如防止旁观者看到密码。

| 值         | 描述                               |
| --------- | -------------------------------- |
| 错误 *(默认)* | 普通文本框                            |
| 真的        | 输入的字符不会显示给最终用户，相反，每个输入字符都会显示一个星号 |

#### 2.8.2 Input Mask

●{% alert type="info" %}}本地移动页面不支持输入遮罩。

输入掩码是为字符串数据类型设计的。 在使用数字或哈希字符串数据类型时保持谨慎。
{{% /报警 %}}

输入掩码按照下面的规则限制最终用户可以在文本框中输入的内容：

| 字符  | 允许输入       |
| --- | ---------- |
| `9` | 任意数字       |
| `Z` | 任意字母       |
| `U` | 大写字母       |
| `L` | 小写字母       |
| `*` | 字母 *或* 个数字 |

其它字符将以字面表示。

例如，输入掩码 `99-LL-9999` 匹配 `24-2008`。

#### 2.8.3 最大长度

此属性指定了可以在此文本框中输入的最大字符数。

| 值           | 描述                |
| ----------- | ----------------- |
| 属性长度 *(默认)* | 最大字符数与连接属性的最大长度相同 |
| 无限制         | 最大字符数是无限的         |
| 自定义         | 小部件属性中指定的最大字符数    |

#### 2.8.4 占位符文本

当没有输入文本或显示属性为空时，将显示占位符文本。

例如，它可以用来向最终用户说明应填写何种案文。

<a name="label-properties"></a>

### 2.9 标签部分{#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.10 验证部分{#validation}

{{% snippet file="refguide/widget-validation-link.md" %}}

### 2.11 可见性部分{#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 阅读更多

* [数据类型](data-types)
* [数据视图](data-view)
* [属性](attributes)
