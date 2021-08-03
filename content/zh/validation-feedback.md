---
title: "验证反馈"
parent: "客户活动"
menu_order: 70
tags:
  - "studio pro"
  - "验证反馈"
  - "客户活动"
aliases:
  - /refguide/Validation+Feedback.html
---

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

{{% alert type="warning" %}}
这个动作被忽略，当从离线、本地或混合应用调用微流时不起作用。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

## 1 导言

**验证反馈** 活动进行验证检查，如果此检查失败， 它向小部件下方的最终用户显示红色信息，显示失败的属性或关联性。 例如，如果客户没有验证他们的电子邮件， 一个消息将被显示在客户可以登录之前应该验证它：

{{% image_container width="200" %}}
![验证反馈](attachments/client-activities/validation-feedback.png)
{{% /image_container %}}

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![验证反馈属性](attachments/client-activities/validation-feedback-properties.png)

**验证反馈** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 变量

**变量** 指定哪些对象将被验证。

### 3.2 成员

**成员** 定义消息将显示哪个属性或关联。 您有 [个参考选择器](reference-selector) 或 [参考设置选择器](reference-set-selector), 您应该选择用这些小部件编辑的关联。

### 3.3 模板

**模板** 是将显示给最终用户的消息。 模板可以包含以数字写在括号之间的参数，例如 {1}。 第一个参数包含数字1，第二个参数，等等。

{{% alert type="warning" %}}

Nanoflow不支持验证反馈中的文本模板。 只能提供静态消息文本。

{{% /报警 %}}

### 3.4 参数

参数是将显示的属性值。 参数需要使用 [表达式](expressions) 输入导致字符串。

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 阅读更多

* [活动](活动)