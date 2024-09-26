---
title: "XPath 最大"
parent: "xpath-query函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-max.pdf)。
{{% /报警 %}}

## 1 概览

`max()` 函数返回其参数的最大值。

函数需要一个 XPath 查询作为参数。

函数必须在查询中指定要聚合的一列。

查询必须指定一个有数字类型的属性。

## 2 示例

此查询返回在任何对象中找到的最高总价格：

```java
max(//Sales.Order/TotalPrice)
```

此查询返回一个客户所下订单的最高总价格，其名称为“Jansen”：

```java
max(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen']/TotalPrice)
```
