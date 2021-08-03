---
title: "显示消息"
parent: "客户活动"
menu_order: 4
tags:
  - "studio pro"
  - "显示消息"
  - "客户活动"
aliases:
  - /refguide8/Show+Message.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/show-message.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

{{% alert type="warning" %}}
这个动作被忽略，当从离线、本地或混合应用调用微流时不起作用。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

## 1 导言

**显示消息** 活动向最终用户显示了一个屏蔽或非屏蔽消息。 例如，如果最终用户没有在表格中选择客户评分， 您可以显示一个错误消息，告诉他们选择一个成绩以继续：

{{% image_container width="300" %}}
![显示消息](attachments/client-activities/show-message.png)
{{% /image_container %}}

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![显示消息属性](attachments/client-activities/show-message-properties.png)

**显示消息** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 Type

**输入** 定义消息的配色方案和图标。

有三个消息选项：

* 信息 *(默认)*
* 警告
* 错误

### 3.2 模板

**模板** 定义消息的文本。 模板可以包含以数字写在括号之间的参数，例如 {1}。 第一个参数包含数字1，第二个参数，等等。

### 3.3 参数

对于模板中的每个参数，您定义了上下文实体或关联实体的属性。 此属性的值将插入参数的位置。 参数应该使用 [表达式](expressions) 输入，结果是一个字符串。

使用参数，您可以根据特定情况自定义您的消息。 例如，消息“电子邮件已经发送给客户 {1}。 带参数 `$customer/FullName` 将显示电子邮件发送给的客户的全名。

### 3.4 屏蔽

**屏蔽** 属性定义了显示给最终用户的消息是否被屏蔽。 非屏蔽消息允许用户在弹出窗口打开时继续在应用中工作。 当屏蔽消息不允许用户继续工作，直到弹出窗口关闭。

| 选项       | 描述                                                    |
| -------- | ----------------------------------------------------- |
| 是 *(默认)* | 消息出现在屏幕中心的弹出窗口中，不允许用户继续工作，直到弹出窗口关闭。                   |
| 否        | 消息出现在屏幕中心的弹出窗口中，但不会屏蔽屏幕的其余部分， • 让最终用户能够在弹出窗口的情况下继续工作。 |

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 阅读更多

* [活动](活动)