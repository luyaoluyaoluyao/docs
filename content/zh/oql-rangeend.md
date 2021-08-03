---
title: "OQL RANGEEND"
parent: "oql-函数"
tags:
  - "studio pro"
---

## 1 个描述

`RANGEEND` 函数提取范围参数的最终值。

[RANGEBEGIN](oql-rangebegin) and `RANGEEND` 是使用参数的 OQL 函数， 和 OQL 参数仅在 [数据集](data-sets) 中可用(用于生成报告)。 当您创建一个页面并添加具有数据集的报告时， 您可以在该数据集中使用 `RANGEBEGIN` and `RANGEEND`

## 2 种语法

语法如下：

```sql
RANGEEND ( $range )
```

`$range` 指定了范围参数。

## 3 个示例

这是在 OQL 中使用范围的一个例子，在这里 `$range` 设置为上星期。 这将给您所有在上周出生的客户：

```sql
选择姓氏为姓氏，姓氏为姓名，生日为姓氏，客户类型为销售。客户
生日为生日为生日 ($rangeLastWeek)
```

此示例在 `WHERE` 条款中使用 `RANGEEND` 功能， 这将给您所有自上周末以来出生的客户：

```sql
选择姓氏为姓氏，姓氏为姓名，生日为姓名，客户类型为ROM销售。客户
生日 > RANGEEND($rangeLastWeek)
```
