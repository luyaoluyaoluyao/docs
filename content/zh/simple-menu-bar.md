---
title: "简单菜单栏"
parent: "菜单部件"
menu_order: 2
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/simple-menu-bar.pdf)。
{{% /报警 %}}

●{% alert type="warning" %}}本机移动页面不支持简单的菜单栏小部件。{{% /提醒 %}}

## 1 导言

一个简单的菜单栏以水平或垂直条形形式显示 [导航轮廓](navigation#profiles) 或 [菜单中](menu) 文档。 这些项目是由 [菜单源](#menu-source) 决定的，它们要么在 [导航](navigation) 中配置，要么是 [菜单](menu)。

此部件不显示菜单项子项，这意味着菜单结构只能有一个级别。 关于菜单项及其属性的更多信息，见 [菜单](menu)。

![简单菜单栏](attachments/menu-widgets/simple-menu-bar.png)

## 2 属性

一个简单的菜单栏属性的示例在下面的图像中显示：

{{% image_container width="250" %}}![简单菜单栏属性](attachments/menu-widgets/simple-menu-bar-properties.png)
{{% /image_container %}}

菜单栏属性由以下部分组成：

* [常用的](#common)
* [设计属性](#design)
* [A. 概况](#general)

### 2.1 共同部分 {#common}

{{% snippet file="refguide8/common-section-link.md" %}}

### 2.2 设计属性科 {#design}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般部分 {#general}

#### 2.3.1 菜单源 {#menu-source}

菜单部件中显示的项目由 **菜单源** 决定。 可能的菜单来源见下表：

| 值            | 描述                               |
| ------------ | -------------------------------- |
| 项目导航  *(默认)* | 菜单项取自 [导航](navigation) 中定义的配置文件。 |
| 菜单文档         | 菜单项取自一个 [菜单文档](menu)。            |

#### 2.3.2 简介

只有在 [菜单源](#menu-source) 设置为 **项目导航** 时才可用。 **配置** 属性指定了哪些 [导航配置文件](navigation#profiles) 用于小部件。

默认： *响应性*

#### 2.3.3 菜单

只有在 [菜单源](#menu-source) 设置为 **菜单文档** 时才可用。 **菜单** 属性指定了什么 [菜单](menu) 文档用于小部件。

#### 2.3.4 方向

此属性决定了简单菜单栏的布局。

| 方向         | 描述               |
| ---------- | ---------------- |
| 水平  *(默认)* | 菜单项彼此相邻，图像高于标题。  |
| 垂直的        | 菜单项彼此下面，图像在标题旁边。 |

## 3 阅读更多

* [页](page)
* [菜单部件](菜单部件)
* [页面编辑器中常见的属性](common-widget-properties)
