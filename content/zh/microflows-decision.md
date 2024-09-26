---
title: "决 定"
category: "微型流动"
menu_order: 20
description: "在 Mendix Studio 中描述一个决定。"
tags:
  - "工作室"
  - "微流"
  - "专用拆分"
  - "决 定"
---

## 1 导言

本文档在 Mendix Studio 描述了一个 **决定**。

一项决定是基于一项条件的要素；它只依靠一项外流量。 例如，您需要使用决定为不同级别的客户显示不同的订单表单， 或阻止被屏蔽的客户订单。

## 2 条件 {#condition}

有两种方式来配置一个条件用于决策：

* [使用 **变量/属性**](#variables-attributes-tab) (例如您可以用它来为枚举类型的属性创建不同的流程)
*  [使用 **表达式**](#expression-tab) (例如，您可以创建一个与它比较)

   ![](attachments/microflows-decision/configure-condition-dialog.png)

### 2.1 用变量或属性配置条件 {#variables-attributes-tab}

以下元素可以在 **变量/属性** 标签中作为决策条件：

* 带布尔值数据类型的变量
* 有枚举数据类型的变量
* 布尔类型的属性
* 枚举类型的属性

{{% alert type="info" %}}

您想要在配置决策条件时使用的参数和实体应该存在于微流程中， 要么作为输入参数，要么作为活动的结果。

{{% /报警 %}}

### 2.2 用表达式配置条件 {#expression-tab}

您也可以通过写入表达式来配置条件。 关于如何写一个表达式的更多信息，见 [微流程表达式](microflows-expressions)。

## 3 个案件

**案件** 定义了输出流量的数量，取决于所选的 [条件](#condition)。

对于参数或属性的布尔类型，可能有两种流： **true** and **false**。

![](attachments/microflows-decision/decision-boolean.png)

可用于列举类型的案例数量取决于相应的列举值。 还有 *空的* 案例可供枚举：如果一个对象的枚举参数或属性未分配， 带标题 **(空)** 的序列流被遵循。

例如，如果最终用户需要选择客户等级，但不这样做， 标签为 **(空)** 的流程被遵循，一个错误消息被显示给最终用户：

![](attachments/microflows-decision/decision-enumeration.png)

## 4 个标题

标题描述了这个元素发生的情况。

## 5 阅读更多

* [微型流动](微流)
* [微流程表达式](microflows-expressions)
* [配置决定](/studio-how-to8/microflows-how-to-configure-decision) 

