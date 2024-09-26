---
title: "文本"
parent: "普通小部件"
menu_order: 10
tags:
  - "studio pro"
  - "文本"
  - "文本部件"
  - "常见小部件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/text.pdf)。
{{% /报警 %}}

## 1 导言

文本小部件显示一个必要时可以包含参数的文本。 每个属性被此属性的值替换。 例如， 您可以在 [数据视图](data-view) 中放置文本小部件并向其添加参数来向用户显示欢迎消息。

![文本部件](attachments/common-widgets/text.png)

如果您开始在任何空容器中输入，Studio Pro 将自动生成一个文本小部件以显示您的文本。

## 2 属性

下面的图像是文本属性的示例：

{{% image_container width="300" %}}![文本属性](attachments/common-widgets/text-properties.png)
{{% /image_container %}}

文本属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分 {#general}

#### 2.3.1 标题 {#caption}

**标题** 定义了将显示的文本。 标题可以包含括号之间写入的参数，例如 {1}。

欲了解更多关于使用参数的信息，请参阅下面的 [参数]() 部分。

#### 2.3.2 参数 {#parameters}

参数是将显示的属性值。 要查看 **参数**，请执行以下操作之一：

* 双击属性中的 **标题** 设置

*  Double-click the text widget on the page and click **Edit** in the **General** section > **Caption**:

    ![正在打开参数](attachments/common-widgets/caption-edit-button.png)

参数有以下设置：

* **索引** — — 一个参数的识别号码

* **属性 (路径)** - 一个将显示其值的属性

*  **格式** - 一个将显示属性值的格式

    ![参数设置](attachments/common-widgets/parameter-settings.png)

##### 2.3.2.1 添加新参数

要使用参数，请执行以下操作：

1. 将 **文本** 小部件放置在实体的上下文中，就像放置在一个 [数据小部件](data-widgets) 中。

2. 双击文本部件属性中的 **标题** 设置。

3.  在 **编辑标题** 对话框 > **参数** 部分点击 **新**

    ![添加新参数](attachments/common-widgets/adding-parameter.png)

4. 在 **编辑模板参数** 对话框中，点击 **选择**，选择属性并确认您的选择。

5.  在 **标题** 设置中。 写入您想要显示的文本并输入 **索引** 你想要包含的参数. In the example below, to include a full name of your customer and a number of unread messages, you need to use indexes {1} for the *FullName* attribute, and {2} for the *NrOfUnread* attribute:

    ![参数示例](attachments/common-widgets/parameters-example.png)

##### 2.3.2.2 在参数上采取其他行动

除了添加新参数外，您还可以对参数执行以下操作：

* **删除** - 以删除参数，点击删除或按 <kbd>删除您的键盘</kbd>

* **编辑** — 双击一个参数来编辑它或单击编辑

* **向上移动** - 在参数列表中移动参数并更改其索引， 点击 **向上移动**

*  **向下移动** - 在参数列表中向下移动参数并更改其索引， 点击 **向下移动**

    ![参数操作](attachments/common-widgets/parameter-actions.png)

#### 2.3.3 渲染模式

渲染模式决定文本如何显示。

| 值          | 描述                                                                          |
| ---------- | --------------------------------------------------------------------------- |
| 文本  *(默认)* | 文本将与页面上的上一个/下一个文本内嵌(HTML中的`<span>` 标签)。                               |
| 第18段       | 文本将作为单独的一段(`<p>` 标签在 HTML)。                                           |
| 标题1-标题6    | 文本将被呈现为一个选中的标题 (例如，HTML中的 `<h1>` 标签)。 **标题1** 是最大的标题。 **标题6** 是最小的标题。 |

### 2.4 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [常见小部件](普通小部件)
* [页面编辑器中常见的属性](common-widget-properties)