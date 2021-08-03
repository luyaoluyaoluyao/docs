---
title: "关闭页面"
parent: "客户活动"
menu_order: 10
tags:
  - "studio pro"
  - "关闭页面"
  - "客户活动"
aliases:
  - /refguide8/Close+Form.html
  - /refguide8/close-form.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/close-page.pdf)。
{{% /报警 %}}

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

    {{% image_container width="300" %}}
![关闭页面属性](attachments/client-activities/close-page-properties.png)
{{% /image_container %}}

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

### 3.1 页数

{{% alert type="info" %}}
此选项仅适用于本机移动设备，并且是与Mendix Studio Pro v8.14一起引入的。
{{% /报警 %}}

此属性允许您控制应该关闭多少页。

| 值    | 描述                                  |
| ---- | ----------------------------------- |
| 单一的  | 关闭一个页面(默认行为)。                       |
| 多个选项 | 一次关闭多个页面，并只显示单个动画。 这个数字可以使用表达式进行配置。 |

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 阅读更多

* [显示页面](show-page)
* [原生导航](native-navigation)