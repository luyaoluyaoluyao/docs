---
title: "OQL 选择条款"
parent: "oql"
---

SELECT 条款规定必须检索哪些实体属性或其他特定数据。 `SELECT` 条款由术语 `SELECT` 和一个或多个表达式组成。 这些表达式必须用逗号分隔。 每个表达式在结果中定义列. 每个表达式都可以有一个别名，这个别名将是结果中列的名称。

语法如下：

```
选择[ DISTINCT ]
    format@@
            *
        | { entity_name | from_alias }
        | 演变表达式 [ [ AS ] column_alias ] } [ ,. .n ]
}
```

`DISTINCT` -- 指定结果中不能显示双行。

`*` (星号) - 指定来自FROM 条款中所有实体的所有属性均应退回。

`entity_name。*`, `from_alias。*` - 指定应该返回指定实体或FROM 条款表达式的所有属性。

{{% alert type="info" %}}

```
SELECT Sales.Customer.* FROM Sales.客户
```

```
选择个人。* 从 Sales.Customer as person
```

{{% /报警 %}}

`表达式`

是一个常性、函数或属性名称、常量和由操作者连接的函数或子查询的任何组合。 当您添加更多表达式时，在每个表达式之间放置逗号。

{{% alert type="info" %}}

```
选择客户名称、 姓氏、 生日客户名称、 类别FROM 销售.客户
```

{{% /报警 %}}

更多信息请访问 [此页面](oql-expressions)。

`column_alias` - 是替代在此结果中的列名的替代名称。 当获取属性名称时，结果列为“名称”。 使用别名，您可以指定另一个结果列名，如“客户名称”。 别名可以包含空格。

{{% alert type="info" %}}

```
选择销售。Customer.name as Customername FROM Sales.客户
```

```
SELECT Sales.Customer.name AS '客户名称' FROM Sales.客户
```

{{% /报警 %}}
