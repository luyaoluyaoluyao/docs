---
title: "来自条款的 OQL"
parent: "oql"
---

## 1 导言

`FROM` 条款指定了必须从中检索数据的实体或其他来源。 此条款以 `FROM` 关键字开始，然后由实体名称跟进。 若要从其他实体中选择数据，请通过 `JOIN` 关键字添加这些实体。 此语法比官方的 `SQL FROM` 条款语法更加严格。

这是完整语法的一个示例：

```
FROM
    {
        entity_name | ( sub_oql_query )
    }
    [ [ AS ] from_alias ]

    {
        { INNER | { { LEFT | RIGHT | FULL } [ OUTER ] } } JOIN
        entity_path [ [ AS ] from_alias ]
        ON <constraint>
    } [ ,...n ]
```

## 2 实体名称

这指定了必须从其中检索数据的实体。

## 3 ( sub_oql_查询)

这指定了另一个必须从其中检索数据的 OQL 查询。 这将是当前查询的来源。 子查询必须放在括号内。

## 4 個聯繫人

这指定了一个实体加入此查询的路径。 支持四种不同类型的JOINS：

* InNER JOIN
* 从我们开始的游戏
* 右侧加入
* 完整的JOIN

语法如下：

```
 { INNER | { { LEFT | RIGHT | FULL } [ OUTER ] } } JOIN
        entity_path [ [ AS ] from_alias ]
        [ ON <constraint> ]
```

### 4.1 实体路径

这指定了要加入的实体以及从 `FROM` 条款中早先定义的实体到这个实体的路径。

路径 `Crm.Customer/Crm.Customer_Address/Crm.Address` 定义了一个从早先定义的实体 **Crm.客户** 到新实体 **Crm.Address** 的路径。

### 4.2 \[ on \<constraint\>\]

这限制了 `JOIN` 部分 `FROM` 条款中指定的实体。 约束语法类似于 `WHERE` 条款。 Only the entities and `from` aliases from the current and preceding `JOIN` elements can be used in the constraint.

这部分是可选的。 系统将根据指定的 `entity_path` 生成相应的 JOIN 条件。

### 4.3 JOIN类型

#### 4.3.1 INNER JOIN

`INNER JOIN` 是实体之间最常见的联合操作，代表默认的联合类型。 查询比较了实体A的每一行和实体B的每一行，以找到具有关联并满足 `JOIN` 预测的所有行对。 如果关联存在且 `JOIN` 上游已经满足， A 和 B 每对匹配行的列值合并为一个结果行。

语法如下：

```
[ INNER ] JOIN entity_path [ on <constraint>]
```

#### 4.3.2 我们的热点

使用 `个我们的 JOIN` 构造， 查询比较了实体A的每一行和实体B的每一行，以找到所有具有关联的行，从而满足 `JOIN` 预测。 当关联存在且 `JOIN` 上游已经满足时， A和 B的每一对匹配行的列数值合并为一个结果行。

然而，与 `INNER JOIN` 构建形成对比。 查询还将返回与实体B不匹配的实体A的行数。 当实体B列被指定时，这些列包含这些行的空值。

语法如下：

```
LEFT [ OUTER ] JOIN entity_path [ on <constraint>]
```

#### 4.3.3 RIGHTR JOIN

使用 `Right OUTER JOIN` 构建， 查询比较了实体A的每一行和实体B的每一行，以找到所有具有关联的行，从而满足 `JOIN` 预测。 如果关联存在且 `JOIN` 上游已经满足， A 和 B 每对匹配行的列值合并为一个结果行。

然而，与 `INNER JOIN` 构建不同，实体B中与实体A不匹配的行也将被还原。 实体A栏被指定时，这些栏目包含这些行的空值。

语法如下：

```
右[ OUTER ] JOIN entity_path [ on <constraint>]
```

#### 4.3.4 完整的

使用 `完整的JOIN` 构造， 查询比较了实体A的每一行和实体B的每一行，以找到所有拥有一个关联的行，从而满足连接预测的要求。 当该社团存在并满足加入前提条件时， 从 A 和 B 的每对匹配行的列数值合并成一个结果行。

然而，与 `INNER JOIN` 结构不同，来自不 _的实体的数据_ 将会被还原。 对于这些行，缺失实体的列将包含空值。

语法如下：

```
完整的 [ OUTER ] JOIN entity_path [ on <constraint>]
```

### 4.4 例子

在这种情况下， 您正在使用 `LEFT OUTER JOIN` 来获取表A中与表B没有关联的记录。

例如，您有实体 **客户** 和 **订单**，客户可以在其中有多个订单。 您想要检索所有没有订单的客户。

```
选择 
  客户名称，
  客户名称，<anyotherattribute> 为 <anyotherattribute>
从MyModule.客户
  LEFT OUTER JOIN Customer/MyModule.Customer_Order/MyModule.order 为订单
WHERE 订单/ID IS NULL
```
