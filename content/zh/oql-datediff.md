---
title: "OQL DATEDIFF"
parent: "oql-函数"
tags:
  - "studio pro"
---

## 1 个描述

`DATEDIFF` 函数返回两个给定日期/时间值之间的差额。 差异是在指定的单元中给出。

## 2 种语法

语法如下：

```sql
DATEDIFF ( unit , startdate_expression, enddate_expression )
```

### 2.1 单位

`单位` 指定要检索的日期/时间值的单位。 这可以是以下内容之一： `YEAR`, `QUARTER`, `MONTH`, `日`, `WEEK`, `HOUR`, `MINTE` 或 `SECOND` 关于日期/时间值的更多信息，请参阅 *OQL DATEPART* 中的 [示例](oql-datepart#oql-datepart-example) 部分。

### 2.2 启动日期表达式

`startdate_expression` 指定了所计算的周期的起始日期。 这个格式应该用一个表达式解析成一个日期/时间值。

### 2.3 末日表达式

`enddate_expression` 指定了计算周期的结束日期。 这个格式应该用一个表达式解析成一个日期/时间值。
