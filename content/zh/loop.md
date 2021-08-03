---
title: "循环"
parent: "应用逻辑："
menu_order: 80
tags:
  - "studio pro"
  - "循环"
  - "迭代结束"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/loop.pdf)。
{{% /报警 %}}

## 1 导言

循环用于在对象列表上进行迭代，并可视化为帧。 对每个对象执行循环内的流程。 迭代器看起来与参数相同，代表每次迭代列表中的当前对象。 对象的名称用黑色显示，而对象的实体类型用蓝色。

例如， 如果您有 *订单行* 实体的对象列表并且您想为每个对象设置购买日期， 您可以使用一个循环，并在循环中设置购买日期：

![](attachments/loop/loop.png)

循环可以包含微流中使用的所有类型元素，但启动和结束事件除外。 只有循环可以包含 [中断事件](break-event) 和 [继续事件](continue-event)。

## 2 输入属性

### 2.1 迭代结束

一个变量是你要循环的项目列表。

## 3 动作属性

### 3.1 循环对象名称

**循环对象名称** 是当前正在处理的列表项的名称。 循环中的流程是针对列表中的每个对象执行的，对象总是有这个名称。 例如，如果循环所用的列表类型是 *订单列表*， 迭代器对象将是 *订单类型*