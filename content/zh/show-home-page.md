---
title: "显示主页"
parent: "客户活动"
menu_order: 30
tags:
  - "studio pro"
  - "显示主页"
  - "首页"
  - "客户活动"
aliases:
  - /refguide8/Show+Home+Page.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/show-home-page.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

{{% alert type="warning" %}}
这个动作被忽略，当从离线、本地或混合应用调用微流时不起作用。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

## 1 导言

**显示主页** 活动为最终用户打开主页。 例如，您可以在用户未登录时导航到主页。

{{% image_container width="200" %}}
![显示主页](attachments/client-activities/show-home-page.png)
{{% /image_container %}}

此活动显示登录后显示给最终用户的相同页面。 指向当前用户角色定义的首页。 关于基于角色的主页的更多信息，见 [Navigation](navigation)。

## 2 属性

**显示主页** 活动属性由以下部分组成：

* [行 动](#action)

* [常用的](#common)

    {{% image_container width="300" %}}
![显示主页属性](attachments/client-activities/show-home-page-properties.png)
{{% /image_container %}}

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 阅读更多

* [显示页面](show-page)
* [活动](活动)

