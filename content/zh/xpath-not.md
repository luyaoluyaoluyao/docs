---
title: "XPath 不是"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-not.pdf)。
{{% /报警 %}}

## 1 概览

`not()` 函数反转参数的含义(和结果)。

{{% alert type="info" %}}
这可能与反向比较有不同的结果(例如， `！ 如果XPath 超过了一对多的关系，` 为 `=`的负数。 更多的解释请见下面的例子。
{{% /报警 %}}

## 2 示例

此查询返回名称为 *的所有客户* 等于"Jansen"：

```java
//Sales.Customer[not(Name = 'Jansen')]
```

在这种情况下，上述查询返回与以下查询相同的结果：

```java
//Sales.Customer[name != 'Jansen']
```

以下查询返回所有没有下单的客户：

```java
//Sales.Customer[not(Sales.Customer_order/Sales.Order)]
```

The following query returns all the customers who have placed *no* orders with a `TotalPrice` of *more than* 30,000, including those who have not placed any orders at all:

```java
//Sales.Customer[not(Sales.Customer_order/Sales.Order/TotalPrice > 30000)]
```

上面的查询不会返回与下面相同的结果。 返回所有已下达 *至少一个* 订单的客户 `总计价格` *小于* 30, 00，无论他们发出的订单数量超过30 000个：

```java
//Sales.Customer[Sales.Customer_order/Sales.Order/TotalPrice <= 30000]
```
例如，如果客户下达了两个订单——一个是15,000份，一个是35份。 00-此查询将返回此客户，而 *不是* 查询将不会返回此客户。 未下订单的客户将不会被此查询退回。
