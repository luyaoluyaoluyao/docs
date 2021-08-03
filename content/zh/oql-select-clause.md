---
title: "OQL 选择条款"
parent: "oql"
tags:
  - "studio pro"
---

## 1 个描述

`SELECT` 条款指定了必须检索哪些实体属性或其他指定数据。 `SELECT` 条款由术语 `SELECT` 和一个或多个表达式组成。 这些表达式必须用逗号分隔。 每个表达式在结果中定义列. 每个表达式都可以有一个别名，这个别名将是结果中列的名称。

## 2 种语法

语法如下：

```sql
选择[ DISTINCT ]
    format@@
            *
        | { entity_name | from_alias }
        | 演变表达式 [ [ AS ] column_alias ] } [ ,. .n ]
}
```

### 2.1 情况介绍会

`DISTINCT` 指定结果中不能显示双行。

### 2.2 * (星号)

`*` (asterisk) 指定所有实体在 `FROM` 条款中的所有属性都应该返回.

### 2.3 entity_name.* 和 from_alias.*

`entity_name.*` and `from _alias.` 指定所有指定实体或表达式的属性 `FROM` 条款应返回. `entity_name` 可以选择地置于双引号中。 如果实体名称是一个保留的 OQL 单词，则必须使用双引号 (例如 `订单` 或 `组`)。

```sql
SELECT Sales.Customer.* FROM Sales.客户
```

```sql
选择个人。* 从 Sales.Customer as person
```

```sql
选择"Sales.Order"。* 从"Sales.Order"
```
### 2.4 表达式

`表达式` 是一个常数、一个函数或属性名称、常数和函数的任何组合，或是一个子查询或是一个子查询。 当您添加更多表达式时，在每个表达式之间放置逗号。

```sql
选择客户名称、 姓氏、 生日客户名称、 类别FROM 销售.客户
```

欲了解更多信息，见 [OQL Expressions](oql-expressions)。

### 2.5列别名

`column_alias` 是替换结果中列名的替代名称。 当获取名称属性时，结果列为“名称”。 使用别名，您可以指定另一个结果列名，如“客户名称”。 别名可以包含空格。

```sql
选择销售。Customer.name as Customername FROM Sales.客户
```

```sql
SELECT Sales.Customer.name AS '客户名称' FROM Sales.客户
```
