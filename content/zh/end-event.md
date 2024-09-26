---
title: "结束事件"
parent: "事件"
menu_order: 2
tags:
  - "studio pro"
  - "结束事件"
  - "事件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/end-event.pdf)。
{{% /报警 %}}

## 1 导言

结束事件定义流将停止的位置。

结束事件可以返回一个值：对象、枚举、列表等。 欲了解更多信息，请参阅 [返回值](#return-value) 部分。

在下面的示例中，客户 ** 实体的 *买方* 变量在结束事件中返回：

![](attachments/events/end-event.png)

最终事件的数量取决于微流或纳米流可能结果的数量。 这意味着可以有多个结束事件，例如使用 [决定](decision) 时：

![](attachments/events/end-events.png)

## 2 行为属性

### 2.1 退货价值 {#return-value}

返回值是返回到调用当前流的流的值。 如果你有几个结束事件并且它们有返回值，它们都需要返回同类型的值。 例如，如果一个结束事件返回类型为 *实体*的对象，其他事件需要返回相同类型：

{{% image_container width="300" %}}
![](attachments/events/return-value.png)
{{% /image_container %}}

您可以选择什么都不返回，或者返回，例如一个列表、枚举或布尔值：

![](attachments/events/end-event-type.png)

返回值可以输入为 [表达式](expressions)。

{{% alert type="info" %}}

如果您正在调用另一个微流的微流，请注意 *调用* 微流无法控制返回的内容。 它由 *调用* 微流程控制。

{{% /报警 %}}

## 3 阅读更多

* [开始事件](start-event)

* [微流程呼叫](microflow-call)
