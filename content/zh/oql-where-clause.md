---
title: "OQL 条款位置"
parent: "oql"
tags:
  - "studio pro"
  - "查询"
  - "位置"
---

## 1 个描述

`WHERE` 条款具体规定了如何限制检索数据。

## 2 种语法

语法如下：

```sql
温度 <constraint>
```

`<constraint>` 是一个表达式，其值总是等于真值。 表达式包括使用操作员、函数、关键字或系统变量进行简单比较。

欲了解更多信息，见 [OQL Expressions](oql-expressions)。

## 3 个示例

此查询检索名称等于"Jansen"的所有客户：

```sql
选择来自销售的名字。客户
WHERE LastName = 'Jansen'
```

此查询检索所有生活在鹿特丹的客户：

```sql
SELECT 姓来自 Sales.Customer
INNER JOIN Sales.Customer_Address/Sales.Address
WHERE Sales.Address/City = '鹿特丹'
```
