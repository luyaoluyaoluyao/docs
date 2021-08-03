---
title: "XPath 计数"
parent: "xpath-query函数"
---

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
