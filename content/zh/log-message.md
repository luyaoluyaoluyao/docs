---
title: "日志消息"
parent: "活动"
menu_order: 70
tags:
  - "studio pro"
  - "日志活动"
  - "伐木活动"
  - "日志消息"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/log-message.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

使用 **记录消息** 活动，您可以创建出现在Mendix 应用程序日志中的消息：

![日志消息](attachments/log-message/log-message.png)

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![日志消息属性](attachments/log-message/log-message-properties.png)

**日志消息** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.3 日志级别

日志级别定义日志消息的严重性。 在 [Studio Pro 控制台](view-menu#console)中，消息有不同的颜色和图标用于某些日志级别。

| 选项         | 图标                                                                                                                        | 描述                       |
| ---------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| 轨迹         |                                                                                                                           | 用于详细的执行跟踪。               |
| Debug      |                                                                                                                           | 用于调试执行。                  |
| 信息  *(默认)* |                                                                                                                           | 用于记录信息信息。                |
| 警告         | {{% image_container width="15%" %}}![Warning](attachments/log-message/warning.png){{{% /image_container %}}               | 用于记录警告。 这些消息出现在橙色中。      |
| 错误         | {{% image_container width="15%" %}}![Error](attachments/log-message/error.png){{{% /image_container %}}                   | 用于记录错误消息。 这些消息出现在红色中。    |
| 关键的        | {{% image_container width="15%" %}}![Critical Error](attachments/log-message/critical-error.png){{{% /image_container %}} | 用于记录关键错误。 这些消息以白色显示在红色上。 |

### 3.2 日志节点名称 {#log-node-name}

{{% alert type="warning" %}}
此属性仅在微流中可用。
{{% /报警 %}}

日志节点名称是一个微流程表达式，定义日志消息的来源。 例如，如果您从电子邮件模块记录消息，日志节点名称可以是 *电子邮件模块*。 使用您自己的日志节点名称来避免与 Mendix 运行时写入Mendix 日志节点的消息混淆。 Mendix 日志节点列在 *Logging</a> 部分的

默认Mendix 日志节点</em> 中。</p> 

{{% alert type="info" %}}

建议对日志节点名称使用一个 [常量](constants)。 这样可以防止在输入节点名称时出现错误，并且更容易在其后更改日志节点名称。

如果您的应用已经向该日志节点发布消息，您只能为环境设置自定义 [日志节点级别](/developerportal/deploy/environments-details#log-levels)。 因此建议您在启动微流程后在 [中向您的所有自定义日志节点发送初始消息。](project-settings#after-startup)。 

{{% /报警 %}}



### 3.3 模板

**模板** 定义了消息文本。 模板可以包含一些参数作为数字写在括号之间，例如 `{1}`。 第一个参数有数字 `1`, 第二 `2`, 等等。



### 3.4 参数

对于模板中的每个参数，您定义了一个值将插入参数位置的微流程表达式。 参数需要使用 [表达式](expressions) 输入导致字符串。

{{% alert type="info" %}}

使用参数，您可以根据特定情况自定义您的消息。 例如，消息 *已经发送电子邮件给客户 {1}*。 带参数 `$customer/FullName` 将显示已发送电子邮件的客户的全名。

{{% /报警 %}}



### 3.5 包括最新堆栈跟踪

定义是否在此日志消息中包含最新错误的堆栈跟踪。 在 Studio Pro，包含堆栈跟踪的日志信息被标记为纸面素图标。

双击这些日志信息会显示堆栈跟踪。

此选项也适用于 `$latestSoapFault` 如果您定义了一个 web 服务通话的错误处理程序，并且它会遇到肥皂故障， 选中此框将添加堆栈跟踪到Studio Pro中的日志行。



## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}