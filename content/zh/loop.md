---
title: "循环"
parent: "微流和微流法"
menu_order: 80
tags:
  - "studio pro"
  - "循环"
  - "迭代结束"
  - "为每一个"
  - "时"
---

## 1 导言

循环用于执行重复的行动，并可视化为一个框架。 对于每次迭代，循环内的流程都会被执行。 循环可以配置为在列表上迭代或基于布尔表达式。 欲了解更多信息，请参阅下面的 [循环类型属性](#loop-type) 部分。

循环可以包含微流中使用的所有类型元素，但 [开始事件](start-event) 和 [结束事件](end-event) 除外。 只有循环可以包含 [中断事件](break-event) 和 [继续事件](continue-event)。

## 2 循环类型属性 {#loop-type}

下面介绍了两种循环类型。

### 2.1 每一项（清单上的物品） {#for-each}

这是创建新循环活动时的默认类型，它可以用来在对象列表中迭代。 可以通过在您的流程范围内设置 **迭代到** 属性来配置列表。 对于列表中的每个对象，循环内的流程将被执行。 迭代器 (看起来与参数相同) 代表每次迭代列表中的当前对象， 并且可以通过设置 **循环对象名称** 来重命名它。 此对象以黑色显示，而对象的实体类型是蓝色。

![](attachments/loop/foreach-loop-edit-form.png)

例如， 如果您有 **订单行** 实体的对象列表并且您想为每个对象设置购买日期， 您可以使用一个循环，并在循环中设置购买日期：

![](attachments/loop/foreach-loop.png)

### 2.1 在(条件是真) {#while}

此循环类型多次重复循环中的流程，直到某些条件评估为 `false`。 此条件在循环实体的每次执行之前进行评估。 典型的情况是，当无法事先确定循环迭代的确切次数时， **则使用** 循环。

您可以通过设置 **标题** 字段来提供循环或条件的描述。 The loop condition can be entered as an [expression](expressions) in the **Expression** editor, and it should result in a Boolean value. **同时显示** 个关键字， **标题** 下面以黑体显示。

![](attachments/loop/while-loop-edit-form.png)

例如，如果你想要 [日志](log-message) 个数字介于 1 到 5 之间。 您可以使用循环，条件是检查 **计数器** [变量](variable-activities) 是否小于或等于 5。 循环内， 您将记录 **个计数器** 值，并将1添加到 **计数器** 变量，以便循环停止执行 **计数器** 大于 5 时：

![](attachments/loop/while-loop.png)
