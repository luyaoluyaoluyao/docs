---
title: "工作流呼叫"
parent: "工作流程活动"
menu_order: 40
tags:
  - "studio pro"
  - "调用 Workflow"
  - "工作流调用"
---

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

**工作流调用** 活动可以调用并触发 [工作流](workflows)。

![](attachments/call-workflow/workflow-call.jpg)

## 2 属性

下面的图像显示了工作流调用属性的示例：

![](attachments/call-workflow/workflow-call-properties.jpg)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

**工作流程调用** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 工作流 {#workflow}

此活动所调用的工作流。

### 3.2 上下文对象

您想要用作上下文的对象。 它应该是在 [Workflow](#workflow) 属性中设置的实体类型。

### 3.3 变量名称、对象名称或列表名称 {#name}

活动返回的变量、列表或对象的名称。

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}