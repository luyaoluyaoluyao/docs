---
title: "关闭页面"
parent: "客户活动"
menu_order: 10
tags:
  - "studio pro"
  - "关闭页面"
  - "客户活动"
aliases:
  - /refguide/Close+Form.html
  - /refguide/close-form.html
---

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

{{% alert type="warning" %}}
这个动作被忽略，当从离线、本地或混合应用调用微流时不起作用。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

## 1 导言

**关闭页面** 活动将关闭当前打开的页面。 例如，它可以用来关闭弹出页面：

{{% image_container width="200" %}}
![](attachments/client-activities/close-page.png)
{{% /image_container %}}

## 2 属性

**关闭页面** 活动属性由以下部分组成：

* [行 动](#action)

* [常用的](#common)

![关闭页面属性](attachments/client-activities/close-page-properties.png)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

### 3.1 页数

{{% alert type="info" %}}
此选项仅适用于本机移动设备，并且是与Mendix Studio Pro v8.14一起引入的。
{{% /报警 %}}

此属性允许您控制应该关闭多少页。

| 值    | 描述                                       |
| ---- | ---------------------------------------- |
| 单一的  | 关闭一个页面(默认行为)。                            |
| 多个选项 | 一次关闭当前堆栈中的多个页面，只显示单个动画。 这个数字可以使用表达式进行配置。 |
| 所有的  | 关闭当前堆栈中的所有页面，但在堆栈中的第一页除外，只显示单个动画。        |

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 阅读更多

* [显示页面](show-page)
* [原生导航](native-navigation)
