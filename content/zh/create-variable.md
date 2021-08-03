---
title: "创建变量"
parent: "可变活动"
tags:
  - "studio pro"
  - "创建变量"
  - "变量"
  - "可变活动"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/create-variable.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

通过此操作，您可以创建一个新变量并分配一个值。 例如，您可以创建一个 *$Discount* 变量并分配一个值 0。 给予客户50%的折扣，并使用此值计算客户的价格：

![创建变量](attachments/variable-activities/create-variable.png)

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![创建变量属性](attachments/variable-activities/create-variable-properties.png)

**创建变量** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 数据类型

**数据类型** 定义了在变量中存储的数据类型。 一个变量可以有以下 [数据类型](data-types)中的一种：Boolean, Enumeration, Decimal, Integer/Long, or String.

### 3.2 初始值

定义变量的初始值。 值是使用 [表达式](expressions) 输入的(微流程表达式的结果必须匹配变量的数据类型)。

### 3.3 变量名称

变量定义生成变量的名称。 该变量可以被所有在流程中跟随此活动的活动使用。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 阅读更多

* [活动](活动)