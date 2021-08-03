---
title: "呼叫Nanoflow"
parent: "客户活动"
menu_order: 2
tags:
  - "studio pro"
  - "nanoflow 呼叫"
  - "调用 nanoflow"
---

## 1 导言

{{% alert type="warning" %}}
此活动只能用于 **Nanoflows**。
{{% /报警 %}}

**调用 nanoflow** 活动可以调用另一个 [nanoflow](nanoflows)。

{{% image_container width="200" %}}
![Nanoflow 呼叫](attachments/action-call-activities/nanoflow-call.png)
{{% /image_container %}}

参数可以传递到 nanoflow 中，结果可以存储在变量中。

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![Nanoflow 通话属性](attachments/action-call-activities/nanoflow-call-properties.png)

**Nanoflow 调用** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 纳诺夫low

这种活动叫做纳米。

### 3.2 参数

根据选定的微流程，您将在表中看到其参数列表。 参数将数据传递到活动中。

#### 3.2.1 名称

只读参数的名称。

#### 3.2.2 类型

只读参数的类型。 欲了解更多关于参数类型的信息，请参阅 [数据类型](data-types)。

#### 3.2.3 参数 {#argument}

**编辑参数值** 按钮允许您编辑参数值。 对于nanoflow的每个参数，您必须提供一个相同类型的参数。 参数的值使用 [表达式](expressions) 表达。

### 3.3 退货类型

此只读属性表示您是否将检索变量、对象或列表。

### 3.4 使用退货价值

这个属性决定是否应该在当前纳米调节的其余部分提供来自所谓纳米调节器的返回值。 如果 **使用返回值** 设置为 *是*, 您需要填写活动返回的变量、对象或列表的 [名称](#name)。

### 3.5 变量名称、对象名称或列表名称 {#name}

活动返回的变量、列表或对象的名称。

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}