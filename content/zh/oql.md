---
title: "OQL"
parent: "数据集"
---


Mendix OQL (Object Query Langue) 是一个关系查询语言，就像 [SQL](http://en.wikipedia.org/wiki/Sql)。 OQL的主要优点是，OQL使用实体和协会名称，而不是实际的数据库表名称。

此外，OQL可以使用预定义的关系(社团)轻松加入对象，而不必计算哪个列应该是合并的。 尽管有这些差异，许多SQL关键字也可以在 OQL 中工作。

OQL查询的例子是：

*   `从销售中选择用户名。客户` 检索所有客户的名称。
*   `从Sales.Customer WHERE name = 'Jansen'` 检索所有客户的名字，名字为 'Jansen'。
*   `从Sales.Order WHERE IsPayed = 1` 获取所有支付订单总价格的平均值。

OQL 查询由几个组件组成。 点击组件以获取更多具体信息。

| 查询部分                                            | OQL                  | 目的                                  |
| ----------------------------------------------- | -------------------- | ----------------------------------- |
| **[选择条款](oql-select-clause)** (必须)              | `选择AVG(总价格)`         | 决定检索要查询对象的属性。 此处还应界定检索数据上需要履行的任何功能。 |
| **[来自条款](oql-from-clause)** (必须)                | `从 ROM Sales.订单`     | 指定将从中检索数据的源实体。                      |
| **[在哪里条款](oql-where-clause)** (可选)              | `鉴于伊斯帕德=1`           | 限制检索数据。                             |
| **[按条款](oql-group-by-clause)** 分组</strong> (可选) | `按部门排列的组`            | 将行分组到指定属性的值上。                       |
| **[按条款order](oql-order-by-clause)** (可选)        | `按日期排序`              | 按指定属性排序行.                           |
| **[限制条款](oql-limit-clause)** (可选)               | `LIMIT 50 OFFSET 30` | 限制行到总金额的子集。                         |
