---
title: "按钮属性"
parent: "按钮小部件"
tags:
  - "studio pro"
  - "按钮"
  - "动作按钮"
  - "下拉按钮"
  - "按钮小部件"
  - "图像属性"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/button-properties.pdf)。
{{% /报警 %}}

## 1 导言

按钮可以执行各种动作，如调用微流程或nanoflow 或打开一个页面。

## 2 属性

按钮属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![按钮属性](attachments/button-widgets/button-properties.png)
{{% /image_container %}}

按钮属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design)
* [事件](#events)
* [A. 概况](#general)
* [项目](#items) (仅适用于下拉按钮)
* [可见性](#visibility)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 事件科 {#events}

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.4 一般部分 {#general}

#### 2.4.1 标题 {#caption}

**标题** 属性定义了将显示在按钮上的文本。 标题可以包含括号之间写入的参数，例如 {1}。

欲了解更多关于使用参数的信息，请参阅下面的 [参数]() 部分。

#### 2.4.2 参数 {#parameters}

参数是将显示的属性值。 要查看 **参数**，请执行以下操作之一：

* 双击属性中的 **标题** 设置

* 双击页面上的按钮，然后点击 **在 **常规部分中编辑**** 部分 > **标题**

    ![正在打开参数](attachments/button-widgets/opening-parameters.png)

参数有以下设置：

* **索引** — — 一个参数的识别号码

* **属性 (路径)** - 一个将显示其值的属性

* **格式** - 一个将显示属性值的格式

    ![参数设置](attachments/button-widgets/button-parameter-settings.png)

##### 2.4.2.1 添加新参数

若要添加参数，请执行以下操作：

1. 将 **按钮** 小部件放置在实体的上下文中，就像放置在 [数据小部件](data-widgets) 中。

2. 双击按钮部件属性中的 **标题** 设置。

3.  在 **编辑标题** 对话框 > **参数** 部分点击 **新**

    ![添加新参数](attachments/button-widgets/new-parameter.png)

4. 在 **编辑模板参数** 对话框中，点击 **选择**，选择属性并确认您的选择。

5. 在 **标题** 设置中。 写入您想要显示的文本并输入 **索引** 你想要包含的参数. 在下面的示例中，若要包含您客户的名字，您需要对 *名称* 属性使用索引： {1}：

    ![参数示例](attachments/button-widgets/button-parameter-example.png)

##### 2.4.2.2 在参数上执行其他操作

除了添加新参数外，您还可以对参数执行以下操作：

* **删除** - 以删除参数，点击删除或按 <kbd>删除您的键盘</kbd>

* **编辑** — 双击一个参数来编辑它或单击编辑

* **向上移动** - 在参数列表中移动参数并更改其索引， 点击 **向上移动**

* **向下移动** - 在参数列表中向下移动参数并更改其索引， 点击 **向下移动**

    ![参数操作](attachments/button-widgets/button-parameter-actions.png)

#### 2.4.3 工具提示

**Tooltip** 属性决定了文本最终用户将会在鼠标悬停在按钮上时出现的工具提示中看到。 工具提示文本可以翻译。 关于可翻译文本的更多信息，见 [语言菜单](translatable-texts)。 如果未指明工具提示, 当悬停在按钮上时不会显示工具提示。

#### 2.4.4 图标 {#icon}

**图标** 属性决定了将显示在按钮标题前面的图标。 可能的备选办法是：

* 没有图标
* 玻璃图标
* a (bitmap) 图像

Glyphicons来自Bootstrap 合集。 比特图图像上的 glyphicon 的优点是它们是可以缩放的。 在高分辨率屏幕上看得很清楚，其颜色可以通过更改字体颜色而改变。 图像图标的优点是它可以有多个颜色。

#### 2.4.5 渲染模式

定义按钮向最终用户显示的方式。 可能的备选办法如下：

* **按钮** — 小部件将作为按钮渲染。
* **链接** - 小部件将呈现为超链接

*默认渲染模式：* 按钮

#### 2.4.6 按钮样式

**按钮风格** 属性应用了一个预定义的样式按钮。 可能的备选办法如下：

* 默认设置
* 反转
* 主要的
* 信息
* 成功
* 警告
* 危险

#### 2.4.7 行动期间禁用

此属性仅在 **调用微流程** 或 **调用nanoflow** 被选定为 [点击事件](on-click-event) 时才显示。 选择 **在动作过程中禁用** 禁用按钮直到动作完成或失败。

默认： *true*

### 2.5 物品部分 {#items}

{{% alert type="info" %}}

**项目** 部分仅显示于下拉按钮。

{{% /报警 %}}

当最终用户点击下拉按钮时，一个弹出窗口打开项目列表。 当最终用户点击此项目时，每个项目都会执行一个事件。 不同的项目可以执行不同的事件。 关于可以分配的事件的更多信息，见 [点击事件 & 事件部分](on-click-event)

{{% alert type="info" %}}

* 使用 **创建对象** 事件只在您有足够权限时才显示。 欲了解更多信息，请参阅 [Security](security)。

* **注销** 事件不会显示给匿名用户。 关于不同安全等级和匿名用户的更多信息，请参阅 [Project Security](project-security) and [匿名用户](anonymous-users)。


{{% /报警 %}}

每个物品具有下列特性：

* **标题** - 定义项目的标题

*  **动作** - 定义点击项目时执行的按键事件 (用于点击事件的更多信息) 查看 [点击事件 & 事件部分](on-click-event))

    ![项目属性](attachments/button-widgets/items-properties.png)


#### 2.5.1 增加新项目

若要将项目添加到下拉按钮，请执行以下操作：

1. 双击按钮部件属性中的 **项** 设置。

2.  在 **编辑项目** 对话框中，点击 **新的**：

    ![添加新项目](attachments/button-widgets/adding-new-item.png)

3. 在 **编辑下拉按钮** 项目对话框中，执行以下操作：
   1. 指定项目的标题。
   2. 选择要显示的图像 (图标)。
   3. 选择当最终用户点击此项目时要执行的单击事件。
   4. Click **OK**.
4. 在 **编辑项目** 对话框中，点击 **确定** 保存您的更改并添加新项目。



### 2.6 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 阅读更多

* [页](page)
* [按钮部件](按钮小部件)
* [页面编辑器中常见的属性](common-widget-properties)
* [点击事件 & 事件部分](on-click-event)


