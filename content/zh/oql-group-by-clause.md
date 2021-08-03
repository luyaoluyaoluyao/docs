---
title: "按条款排列的 OQL 组"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-group-by-clause.pdf)。
{{% /报警 %}}

GROUP BY 条款会将所有返回的行压缩成一个单行，这个行对本条款中定义的表达式具有相同的值。 该条款中的表述必须存在于查询中的SELECT 条款中。 SELECT 条款中不存在于GROUP BY 条款中的所有表述都必须是一个汇总函数或结果一个汇总函数。

语法如下：

```
由
    表达式 [ ,...]

[已有 <constraint>]
```

**表达式** 指定了用来分组行数值的表达式。

`Having <constraint>` 指定了一个限制。 当使用按表达式分类时，约束必须在已有条款中加以界定。

{{% alert type="info" %}}

```
选择COUNT(Sales.Customer/*)
ROM Sales.客户
INNER JOIN Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
```

此查询返回每个城市所有客户的计数。

{{% /警示%}}!{% alert type="info" %}}

```
SELECT SUM(Sales.Order/ TotalPrice)
从Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer_Address/Sales.Address
GROUP BY Sales.Address/City
```

此查询返回每个城市所有订单总价格的和。

{{% /警示%}}!{% alert type="info" %}}

```
SELECT SUM(Sales.Order/TotalPrice)
从Sales.Order
INNER JOIN Sales.Order/Sales.Customer_Order/Sales.Customer_Address/ Sales.Address
从销售/地址/地址
已经拥有SUM(Sales.Order/ TotalPrice) > 1000.0 或销售.Address/City = 'Losdun'
```

此查询返回每个城市所有订单总价的总和，总价大于1000。 0或城市是Losdun。

{{% /报警 %}}
