---
title: "按条款排序的 OQL 订单"
parent: "oql"
tags:
  - "studio pro"
---

## 1 个描述

`ORDER BY` 条款指定了在 `SELECT` 语句中返回的列的排序顺序。 可以指定多列。 列是按照 `BY` 条款中的项目顺序排序的。

此条款可以包含在 `SELECT` 条款中没有出现的项目， 不适用于 `选择发帖` 已指定或当一个 `组由` 条款存在时。 当使用 `UNION` 时。 列名或别名必须是查询第一部分的 `SELECT` 条款中指定的名称。

## 2 种语法


语法如下：

```sql
ORDER BY
    format@@
        order_by_expression [ ASC | DESC ]
}
```

### 2.1 order_by_expression

`order_by_expression` specifies an attribute of an entity or an alias from the `FROM` clause to sort on.

### 2.2 ASC

`ASC` 指定结果必须从最小值升序到最高值。 这是默认排序类型。

### 2.3 DESC

`DESC` 指定结果必须排序从最高值到最低值。

{{% alert type="info" %}}
关于NULL值的默认排序行为的详细信息。 查看 [NULL Values Order 行为](ordering-behavior#null-ordering-behavior) 部分 *Order by Behavior*。
{{% /报警 %}}

## 3 个示例

此查询可检索所有客户并返回姓氏排序的姓名，升序：

```sql
从销售处选择姓氏。客户
按姓氏排序
```

此查询可检索所有客户并返回按姓氏排序的第一个和姓名，降序：

```sql
选择姓氏+' + 姓氏来自Sales.客户
BY Lastname DESC
```
