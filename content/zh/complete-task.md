---
title: "Complete Task"
parent: "工作流程活动"
menu_order: 10
tags:
  - "studio pro"
  - "用户任务"
  - "工作流"
  - "任务结果"
  - "complete task"
---

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

**完整任务** 活动可以用于定义 [用户任务](user-task) 应该遵循的结果。

![Complete Task](attachments/set-task-outcome/complete-task.jpg)

## 2 属性

一个完整任务属性的示例在下面的图像中显示：

![完成任务属性](attachments/set-task-outcome/complete-task-properties.jpg)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

**完整任务** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 用户任务

从微流程参数中可用的用户任务实体。

### 3.2 工作流程任务

您想要设置结果的用户任务。

### 3.3 结果

为您提供了所选用户任务的可用结果列表。 用户任务将跟随选定的结果。 如果只有一个结果可用，值将设置为 *默认* ，不能编辑。

## 4 共同部分 {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}