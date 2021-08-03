---
title: "微流程呼叫"
parent: "行动呼叫活动"
tags:
  - "studio pro"
  - "微流程呼叫"
  - "调用微流"
  - "行动呼叫活动"
---

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

**微流程调用** 活动可以调用 [微流程](microflows)。

{{% image_container width="200" %}}
![调用微流](attachments/action-call-activities/microflow-call.png)
{{% /image_container %}}

参数可以传递到微流，结果可以存储。

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![微流程调用属性](attachments/action-call-activities/microflow-call-properties.png)

**微流程调用** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 微流

这种活动所要求的微流。

### 3.2 参数

根据选定的微流程，您将在表中看到其参数列表。 参数将数据传递到活动中。

#### 3.2.1 名称

只读参数的名称。

#### 3.2.2 类型

只读参数的类型。 欲了解更多关于参数类型的信息，请参阅 [数据类型](data-types)。

#### 3.2.3 参数 {#argument}

**编辑参数值** 按钮允许您编辑参数值。 对于microflow的每个参数，您需要提供一个相同类型的参数。 参数的值使用 [表达式](expressions) 表达。 参数值传递到子微流的方式存在差异：

  * 列表和对象作为参考传递(意思，如果列表/对象在子微流程中被更改，则原始列表/对象被更改)
  * 原始类型(字符串、数字等)作为值传递(意思，它们是不可变的，不能通过子微流改变)

{{% alert type="warning" %}}
在离线配置文件内使用 nanoflow 时, 只有原始实体和与可持久实体没有联系的不可持续实体才能被允许作为呼叫的理由。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

### 3.3 任务队列

{{% alert type="warning" %}}
您不能在任务队列中执行微流程，当从 nanoflow 调用它们时。
{{% /报警 %}}

如果您想要调用微流程来使用任务队列在后台运行，您需要做以下操作：

1. 检查 **在任务队列** 中执行此微流。
2. 在 **选择任务队列** 中选择任务队列.

关于任务队列的更多信息，见 [任务队列](task-queue)。

### 3.4 退货类型

此只读属性表示您是否将检索变量、对象或列表。

### 3.5 使用退货值

这个属性决定了从所称微流中返回的值是否应该在目前微流的其余部分或nanoflow 中。 如果 **使用返回值** 设置为 *是*, 您需要填写活动返回的变量、对象或列表的 [名称](#name)。

### 3.6 变量名称、对象名称或列表名称 {#name}

活动返回的变量、列表或对象的名称。

## 离线第一应用中的微流程呼叫

可以从离线第一应用进行微流程呼叫。 然而，它的运作与在线应用程序有些不同。 For more information on the differences, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.

## 5 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}
