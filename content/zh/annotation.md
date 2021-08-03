---
title: "批注"
parent: "微流和微流法"
menu_order: 60
tags:
  - "studio pro"
  - "注释"
  - 批注流程
aliases:
  - /refguide/annotation-flow.html
---

## 1 导言

注解是一个可以用来对流程进行注释的元素。

在下面的示例中，您使用 **显示消息** 活动来警告最终用户关于未支付订单的警告，客户端中有一个弹出消息。 稍后您想要通过发送邮件给用户来扩展此警告。 您可以使用批注作为提醒，并将其置于当前活动之上。

![](attachments/anotation/anotation.png)

## 2 公共属性

### 2.1 标题

欲了解详情，请参阅 [共同属性](microflow-element-common-properties)。

## 3 批注流 {#annotation-flow}

注流是一种连接，可用来将注解链接到一个流程对象 (s)。

例如，这是一个注解流程，将注解和 **微流程调用** 活动联系起来：

![](attachments/anotation/anotation-flow.png)