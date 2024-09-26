---
title: "容器"
parent: "容器部件"
menu_order: 20
tags:
  - "studio pro"
  - "容器"
  - "容器部件"
  - "小部件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/container.pdf)。
{{% /报警 %}}

## 1 导言

容器是一个布局元素，可以同时用于样式、隐藏、拖动或删除放在容器中的部件组：

![容器示例](attachments/container-widgets/container.png)

在浏览器中，默认情况下它是一个简单的 `div` 元素。 还可以将一个容器渲染为 HTML5 语义元素之一(例如) `部分`, `main`, `article`, `nav`).

## 2 属性

下面的图像是容器属性的示例：

{{% image_container width="300" %}}![容器属性](attachments/container-widgets/container-properties.png)
{{% /image_container %}}

容器属性由以下部分组成：

* [无障碍环境](#accessibility)
* [常用的](#common)
* [设计属性](#design-properties)
* [A. 概况](#general)
* [事件](#events)
* [可见性](#visibility)

### 2.1 无障碍环境 {#accessibility}

#### 2.1.1 屏幕阅读器隐藏

此属性指定是否在屏幕阅读器中隐藏容器。

●{% alert type="info" %}} 容器内不应有任何焦点元素，如输入小部件、链接或按钮。 这些元素将导致容器由屏幕阅读器宣布。
{{% /报警 %}}

### 2.2 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.3 设计属性部分{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.4 一般部分 {#general}

#### 2.4.1 渲染模式

**渲染模式** 决定哪些HTML5 标签将用于在网页浏览器中显示容器。

| 值                    | HTML 标签  |
| -------------------- | -------- |
| Div *(default)*      | `div`    |
| 1 P-5, 1 P-4, 1 P-3, | `部分`     |
| 第 1 条                | `文章`     |
| 标题                   | `标题`     |
| 页脚                   | `页脚`     |
| 主要的                  | `主要的`    |
| Nav                  | `nav`    |
| 旁边                   | `留言`     |
| Hgroup               | `hgroup` |
| 地址                   | `地址`     |

{{% alert type="info" %}}Render mode is not supported on native mobile pages.{{% /alert %}}

### 2.5 事件部分 {#events}

#### 2.5.1 点击时 {#on-click}

**点击** 属性指定了当用户点击容器时将执行的动作(使用鼠标指针或按 <kbd>输入</kbd> 或 <kbd>空格</kbd> 键值在容器焦点时)。

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.6 可见性科 {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 4 阅读更多

* [页](page)
* [容器部件](容器部件)
* [页面编辑器中常见的属性](common-widget-properties)
