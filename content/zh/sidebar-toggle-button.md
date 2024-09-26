---
title: "侧边栏切换"
parent: "布局"
menu_order: 30
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/sidebar-toggle-button.pdf)。
{{% /报警 %}}

## 1 导言

●{% alert type="info" %}}Sidebar 开关不支持本地移动页面，因为不支持滚动容器区域。{%/提醒 %}}

A **sidebar toggle** is a button that when pressed will make either a left or a right region of a [scroll container](scroll-container) appear or disappear. 这就可以创建一个默认隐藏的侧边栏，并可以通过单击按钮显示。

{{% alert type="info" %}}
您只能在滚动容器中使用一个侧边栏切换， 侧边栏切换的行为在 [滚动容器区域](scroll-container#region) 属性中配置。
{{% /报警 %}}

例如， 下面的图像展示了一个示例布局, 它使用侧边栏切换来隐藏并使得 **滚动容器的 **左侧** 区域**

![](attachments/layout/sidebar-toggle-button.png)

## 2 属性

侧边栏切换属性的示例显示在下面的图像中：

{{% image_container width="250" %}}![](attachments/layout/sidebar-toggle-properties.png)
{{% /image_container %}}

侧边栏切换属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [可见性](#visibility)

### 2.1 共同部分{#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性部分{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分 {#general}

#### 2.3.1 标题 {#caption}

**标题** 属性定义了将显示在侧边栏切换上的文本。

#### 2.3.3 工具提示

**Tooltip** 属性决定了文本最终用户将会在当他们悬停在侧边栏切换时出现的工具提示中看到。 工具提示文本可以翻译。 关于可翻译文本的更多信息，见 [语言菜单](translatable-texts)。 如果未指明工具提示, 当悬停在侧边栏切换时不会显示工具提示。

#### 2.3.4 图标 {#icon}

**图标** 属性决定了将显示在侧边栏切换标题前面的图标。 可能的备选办法是：

* 没有图标
* 玻璃图标
* a (bitmap) 图像

Glyphicons来自Bootstrap 合集。 比特图图像上的 glyphicon 的优点是它们是可以缩放的。 在高分辨率屏幕上看得很清楚，其颜色可以通过更改字体颜色而改变。 图像图标的优点是它可以有多个颜色。

#### 2.3.5 渲染模式

定义侧边栏切换到最终用户的方式。 可能的备选办法如下：

* **按钮** — 小部件将作为按钮渲染。
* **链接** - 小部件将呈现为超链接

*默认渲染模式：* 按钮

#### 2.3.6 按钮样式

**按钮风格** 属性适用于侧边栏切换的预定义样式。 可能的备选办法如下：

* 默认设置
* 反转
* 主要的
* 信息
* 成功
* 警告
* 危险

### 2.4 可见部分{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}
