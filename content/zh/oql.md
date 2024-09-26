---
title: "OQL"
parent: "数据集"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql.pdf)。
{{% /报警 %}}

## 1 导言

Mendix 对象查询语言 (OQL) 是一个类似 [SQL](http://en.wikipedia.org/wiki/Sql) 的关系查询语言。 OQL的主要优点是它使用实体和协会名称而不是实际的数据库表名称。

此外，OQL可以使用预定义的关系(关联)来轻松加入对象，而无需计算哪个列应该是合并的。 尽管存在这些差异，但许多SQL关键词也可以在 OQL 中使用。

以下是OQL查询的一些例子：

* `选择来自Sales.客户` - 检索所有客户的名称
* `选择来自Sales.Customer WHERE name = 'Jansen'`  — 获取所有客户的名字，名字为 "Jansen"
* `从销售中选择AVG(总计价格)。 订单”WHERE IsPaid = 1`  — 检索所有支付订单总价格的平均值`订单` 需要封装在引号中，因为它是一个保留的单词， 意思是可以用于 `ORDER BY`)

{{% alert type="info" %}}
OQL 查询没有考虑到外部安全因素。 这意味着您可以使用 OQL 手动定义自定义安全表达式。 在某些情况下，使用OQL（而不是使用XPath的箱外安全）处理您自己的安全可能会导致更快的查询。
{{% /报警 %}}

使用 [OQL 游戏场](https://mydemoversion8-sandbox.mxapps.io/p/OQL) 演示应用程序在线试用您的 OQL 示例。

## 2 个查询组件

OQL 查询可以使用这些组件：

| 查询部件                               | OQL                  | 目的                                  |
| ---------------------------------- | -------------------- | ----------------------------------- |
| [选择条款](oql-select-clause) (必须)     | `选择AVG(总价格)`         | 决定检索要查询对象的属性。 此处还应界定检索数据上需要履行的任何功能。 |
| [来自条款](oql-from-clause) (必须)       | `从 ROM Sales.订单`     | 指定将从中检索数据的源实体。                      |
| [条款](oql-where-clause) (可选)        | `鉴于伊斯帕德=1`           | 限制检索数据。                             |
| [按条款](oql-group-by-clause) (可选)分组  | `按部门排列的组`            | 将行分组到指定属性的值上。                       |
| [按条款](oql-order-by-clause) (可选) 排序 | `按日期排序`              | 按指定属性排序行.                           |
| [限制条款](oql-limit-clause) (可选)      | `LIMIT 50 OFFSET 30` | 限制行到总金额的子集。                         |

