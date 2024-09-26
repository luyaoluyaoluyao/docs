---
title: "XPath 计数"
parent: "xpath-query函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-count.pdf)。
{{% /报警 %}}

## 1 概览

`count()` 函数计算所有从封闭查询中检索到的对象，并返回作为整数的值。

## 2 示例

此查询返回所有已放置订单的数量：

```java
计数(/Sales.order)
```

此查询返回一个名叫"Jansen"的客户下达的所有订单的数量：

```java
计数(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen'])
```
