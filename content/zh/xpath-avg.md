---
title: "XPath 平均值"
parent: "xpath-query函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-avg.pdf)。
{{% /报警 %}}

## 1 概览

`avg()` 函数返回其参数的平均值。

函数需要一个 XPath 查询作为参数。

函数必须在查询中指定要聚合的一列。

查询必须指定一个有数字类型的属性。

## 2 示例

此查询返回所有订单的平均总价格：

```java
avg(//Sales.Order/TotalPrice)
```

此查询函数返回一个名为“Jansen”的客户下达的所有订单的平均总价格：

```java
avg(//Sales.Order[Sales.Customer_Order/Sales.Client = 'Jansen']/TotalPrice)
```
