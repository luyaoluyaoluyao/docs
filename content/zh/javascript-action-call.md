---
title: "JavaScript 动作调用"
parent: "行动呼叫活动"
menu_order: 20
description: "此引用解释了 JavaScript 动作调用活动的属性。"
tags:
  - "javascript"
  - "返回"
  - "变量"
  - "studio pro"
  - "动作呼叫"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/javascript-action-call.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能用于 **Nanoflows**。
{{% /报警 %}}

## 1 导言

JavaScript 动作调用活动可以调用 [JavaScript动作](javascript-actions)。 参数可以传递给操作，结果可以存储。

{{% image_container width="200" %}}
![javascript 动作调用属性](attachments/action-call-activities/javascript-call.png)
{{% /image_container %}}

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![JavaScript 动作属性](attachments/action-call-activities/javascript-action-call.png)

**JavaScript 动作调用** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 JavaScript 行动

此属性设置活动所调用的 JavaScript 动作。

### 3.2 参数

根据所选的 JavaScript 动作，您将看到其参数列表。 参数将数据传递到活动中。

#### 3.2.1 参数

点击 **编辑参数旁边的** 以填写参数。

一个参数是你传递到 JavaScript 动作的输入数据。 对于每一个 JavaScript 动作参数，您必须提供一个相同类型的参数。

使用 [表达式](expressions) 定义参数的值：

![参数](attachments/action-call-activities/argument-edit.png)

### 3.3 退货类型 {#return-type}

此只读属性表示您是否将检索变量、对象或列表。 返回类型由 JavaScript 操作定义。

### 3.4 使用退货价值

此属性决定从 JavaScript 动作返回的值是否应该在微流或nanoflow 的其余部分可用。 如果 **使用返回值** 设置为 *是*, 您需要填写活动返回的变量、对象或列表的 [名称](#name)。

### 3.5 变量名称、对象名称或列表名称 {#name}

活动返回的变量、列表或对象的名称。 如果它是对象或列表， [返回类型](#return-type) 将表示正在返回的实体。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 阅读更多

* [JavaScript 操作](javascript-actions)
* [生成 JavaScript 操作](/howto8/extensibility/build-javascript-actions)
* [纳诺夫拉](nanoflows)
* [Java 行动电话](java-action-call)
