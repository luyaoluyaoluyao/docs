---
title: "按条款排列的 OQL 组"
parent: "oql"
tags:
  - "studio pro"
---

## 1 个描述

`GROUP BY` 条款将把所有返回的行压缩成一个单行，这个行对该条款定义的表达式具有相同的值。 此条款中的表达式必须存在于查询的 `SELECT` 条款中。 `SELECT` 条款中的所有表达式，如果在 `GROUP BY` 条款中不存在，则必须是一个聚合或结果是一个合计函数。

## 2 种语法

语法如下：

```sql
由
    表达式 [ ,...]

[已有 <constraint>]
```

### 2.1 表达式

`表达式` 指定了以哪个值分组的表达式。

### 2.2 Having\<constraint\>

`having <constraint>` 指定了一个必须在 `已有` 条款中定义的约束， 当使用 `组的` 表达式时使用。

## 3 个示例

此查询返回每个城市所有客户的数量：

```sql
选择COUNT(Sales.Customer/*)
ROM Sales.客户
INNER JOIN Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
```

此查询返回每个城市所有订单总价格的总和：

```sql
SELECT SUM(Sales.Order/ TotalPrice)
从Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
```

此查询返回每个城市所有订单总价的总和，总价大于1000。 0 或 City 是丢失的：

```sql
SELECT SUM(Sales.Order/TotalPrice)
从Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer_Address/ Sales.Address
从销售/地址/地址
已经拥有SUM(Sales.Order/ TotalPrice) > 1000.0 或销售.Address/City = 'Losdun'
```

