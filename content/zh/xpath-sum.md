---
title: "XPath 和"
parent: "xpath-query函数"
---

## 1 概览

`sum()` 函数返回其参数的总和。

函数需要一个 XPath 查询作为参数。

函数必须在查询中指定要聚合的一列。

查询必须指定一个有数字类型的属性。

## 2 示例

此查询返回所有订单总价格的总和：

```java
sum(//Sales.Order/TotalPrice)
```

此查询返回一个客户所下订单总价格的总和，其名称为“Jansen”：

```java
sum(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen']/TotalPrice)
```
