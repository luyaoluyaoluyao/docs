---
title: "继续事件"
parent: "事件"
menu_order: 4
tags:
  - "studio pro"
  - "继续事件"
  - "事件"
  - "循环"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/continue-event.pdf)。
{{% /报警 %}}

## 1 导言

{{% alert type="warning" %}}

继续事件只能在 [循环](loop) 中使用。

{{% /报警 %}}

继续事件用于停止当前迭代并在循环中开始下一个对象的迭代。

通常，下一个对象的迭代将自动开始。 因此，只有在 [决定](decision) 后才需要继续事件(当其中一个路径还没有目标), 因为两个决策路径都需要一个目标。 然而，为了明确起见，你可以选择总是包括一个。

例如， 您有 *订单行* 实体的对象列表，并且您想要仅为支付订单线设置购买日期。 这可以通过一个带有决定的循环、一个连续的事件和一个更改活动来实现。 裁决确定是否支付了订单线。 如果订单行已经支付，购买日期由更改活动设定，循环活动开始于下一个订单行。 如果没有支付订单行，循环开始于下一个订单行，因为该事件将继续。

![](attachments/events/continue-event.png)

## 2 次阅读更多

* [循环](循环)
* [中断事件](break-event)