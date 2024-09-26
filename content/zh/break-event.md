---
title: "中断事件"
parent: "事件"
menu_order: 5
tags:
  - "studio pro"
  - "休息事件"
  - "事件"
  - "循环"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/break-event.pdf)。
{{% /报警 %}}

## 1 导言

{{% alert type="warning" %}}
断开事件只能在 [循环](loop) 中使用。
{{% /报警 %}}

休息活动被用来停止在对象列表上的迭代，继续流的其余部分。 如果没有休息活动，循环将会继续重复下一个目标。

例如，如果您想要通知用户任何未支付的订单行，您可以使用中断事件。 首先，您检索所有与订单相关联的 *OrderLine* 实体的对象。 您检查每个订单行是否已支付。 如果支付订单线，微流将继续到下一个订单线。 然而，如果发现未支付的订单线，则通知用户并停止循环； 微流从循环中中断，继续保持微流的其余部分。 一旦您找到了一个未支付的订单行，您不必继续在订单线的其余部分迭代。

![打破事件示例](attachments/events/break-event-example.png)

## 2 次阅读更多

* [循环](循环)
* [继续事件](continue-event)