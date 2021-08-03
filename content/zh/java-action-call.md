---
title: "Java 行动电话"
parent: "行动呼叫活动"
menu_order: 10
tags:
  - "studio pro"
  - "Java"
  - "java 动作调用"
  - "动作呼叫"
---

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

**Java 动作调用** 活动可以调用 [Java 动作](java-actions)。

{{% image_container width="200" %}}

![Java 操作](attachments/action-call-activities/java-action-call.png)

{{% /image_container %}}

参数可以传递到操作中，结果可以存储。

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![Java 动作调用属性](attachments/action-call-activities/java-action-call-properties.png)

**Java 动作调用** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 Java 行动

此活动调用的 Java 动作。

### 3.2 参数

点击 **编辑参数旁边的** 以填写参数。

一个参数是您正在传递到 Java 操作的输入数据。 对于每一个 Java 动作参数，您必须提供一个相同类型的参数。

使用 [表达式](expressions) 定义参数的值：

![参数](attachments/action-call-activities/argument-edit.png)

### 3.3 退货类型

此只读属性表示您是否将检索变量、对象或列表。 返回类型由 Java 动作定义。

### 3.4 使用退货价值

如果 **用户返回值** 设置为 *是* 您将被要求给返回值一个名称。

### 3.5 变量名称、对象名称或列表名称

Java 动作的结果将具有此名称。 标签表示结果是否为变量、 对象或列表。 如果它是对象或列表， **返回类型** 将表示正在返回的实体。

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}