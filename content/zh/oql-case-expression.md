---
title: "OQL 案例表达式"
parent: "oql运算符"
tags:
  - "studio pro"
---

## 1 个描述

`CASE` 表达式是一个条件表达式，类似于其他编程语言中的如果/否则语句。 每个条件都是返回布尔结果的表达式。 如果条件的结果为 true， `CASE` 表达式的值是跟随条件的结果。 和 `CASE` 表达式的其余部分未处理。 如果条件的结果不属实，其后的任何 `WHEN` 条款将以同样的方式进行审查。 如果没有 `WHEN` 条件生成真， `CASE` 表达式的值是 `ELSE` 条款的结果。 如果 `ELSE` 条款被省略且没有条件为 true，结果为 null。

## 2 用法

`CASE` 表达式可以用两种方式——简单：

```sql
    CASE input_expression
    when_expression THEN result_expression [ ...n ]
    ELSE else_result_expression
    END
```

或扩展：

```sql
    CASE
    WHEN boolean_expression THEN result_expression [ ...] 
    ELSE else_result_expression
    enD
```

## 3 种语法

### 3.1 input_expression

`input_expression` 将被比较为 `when_expression`。 如果  `input_expression` 匹配  `when_expression`, 整个结果 `CASE` 表达式将是 `result_expression` 是在 `THEN` 之后给出。

### 3.2 当表达式时

`当表达式` 将被比较为 `input_expression`。 当 `input_expression` 匹配此 `when_expression`, 整个结果 `CASE` 表达式将是 `result_expression` 是在 `THEN` 之后给出。

### 3.3 boolean_expression

`boolean_expression` 必须导致一个布尔值。 当这个表达式返回 true时，整个 `CASE` 表达式的结果将是 `result_expression` 在 `THEN` 之后给出。

### 3.4 结果表达式

`result_expression` 是整个 `CASE` 表达式的可能结果。

### 3.5 else_result_表达式

`else_result_expression` 是整个 `CASE` 表达式的结果，当不可用 `结果_expression`
