---
title: "显示页面"
parent: "客户活动"
menu_order: 50
tags:
  - "studio pro"
  - "显示页面"
  - "客户活动"
aliases:
  - /refguide/Show+Page.html
---

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

{{% alert type="warning" %}}
这个动作被忽略，当从离线本地或混合应用调用微流时不起作用。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

## 1 导言

通过此活动，您可以向最终用户显示一个选定的页面。 Mendix 应用程序作为单一页面应用程序运行，所以该页面将始终显示在同一个浏览器标签/窗口中。

您可以直接从 **App Explorer** 拖放一个页面到您的微流程：

![](attachments/client-activities/show-page-from-project-explorer.png)

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![](attachments/client-activities/show-page-properties.png)

**显示页面** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 出入证的对象 {#object-to-pass}

一个将传递到打开的页面的对象。 此对象将被带有页面参数数据源的 [数据视图](data-view) 使用。

### 3.2 页 次

显示给最终用户的 [页面](page)。 如果指定 [对象传递](#object-to-pass) 属性 页面必须包含一个与传递对象(或其一般化)连接到同一个实体的数据视图。

要创建一个 **显示页面** 活动将显示的新页面, 点击 **选择** 按钮 > **新** 如果您选择了 **个对象通过**，Studio Pro 将自动创建一个数据视图来编辑该对象。

### 3.3 页面标题

默认情况下，页面标题由页面标题属性决定。 如有必要，您可以用自定义标题替换此标题。

此功能允许您在 **新** **编辑** 数据网格的按钮 [](data-grid)中重新使用同一页面。 简单地将标题设置为 *新客户* 和 *编辑客户*您可以保存自己复制页面的麻烦。

### 3.4 闭合页面 {#close-pages}

{{% alert type="info" %}}
此选项仅适用于本机移动设备，并且是与Mendix Studio Pro v8.14一起引入的。
{{% /报警 %}}

您常常需要控制页面历史。 例如，当用户在Android上按下硬件返回按钮时，显示正确的页面。 这些类型的活动一般只会关闭当前堆栈中的一页。 **关闭页面** 提供了对此行为的更多控制。 我们对有关术语的定义如下：

* **源页面**: 您正在导航 _来自_ 的页面
* **目标页面**: 您正在导航 _到_ 的页面

| 值      | 描述                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 无      | 不要删除历史中的任何页面。 这是默认行为。                                                                                                                                                                                                                                                                                                                                                                                                       |
| 单一的    | 导航到 **目标页面**后，从历史记录中移除 **源页面**。                                                                                                                                                                                                                                                                                                                                                                                             |
| 多个选项   | 在导航到 **目标页面**后，从历史记录中移除 **源页面** 和一个或多个页面。 配置使用表达式删除的页面总数。                                                                                                                                                                                                                                                                                                                                                                   |
| 所有的    | 在导航到 **目标页面**后，移除 **源页面** 以及之前的所有页面。 This option is similar to the **Single** and **Multiple** options, except only pages in the current stack will be closed.                                                                                                                                                                                                                                                              |
| 清除历史记录 | 阻止用户完全返回导航。 This is especially useful when navigating away from a login or tutorial flow.<br />{{% alert type="warning" %}}In the page editor and in nanoflows as well as in native apps, this option can only be used in combination with target pages that are included in the bottom bar configuration (if the layout has a bottom bar) and that have a default layout type (meaning, not a pop-up).{{% /alert %}} |

## 4 通用部分{#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 阅读更多

* [活动](活动)
* [原生导航](native-navigation)
