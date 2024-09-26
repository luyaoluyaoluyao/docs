---
title: "更改变量"
parent: "可变活动"
tags:
  - "studio pro"
  - "更改变量"
  - "变量"
  - "可变活动"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/change-variable.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

更改变量允许您更改现有变量的值。 例如，如果您有一个 *$Discount* 变量给予客户50%的折扣。 您可以更改此变量并赋予它一个新值。 您可以使用此值给新客户一个更大的折扣：

![更改变量](attachments/variable-activities/change-variable.png)

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![更改变量属性](attachments/variable-activities/change-variable-properties.png)

**更改变量** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

### 3.1 变量

你想要更改值的变量。

### 3.2 价值

变量的新值。 值是使用 [表达式](expressions) 输入的。 表达式的类型必须与所选变量的类型相同。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 阅读更多

* [活动](活动)