---
title: "OQL 案例表达式"
parent: "oql运算符"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-case-expression.pdf)。
{{% /报警 %}}

CASE 表达式是一个条件表达式，类似于其他编程语言中的如果/否则语句。 每个条件都是返回布尔结果的表达式。 如果条件的结果为 true，CASE 表达式的值是跟随条件的结果。 和 CASE 表达式的其余部分未处理。 如果条件的结果不成立，则以同样的方式审查随后的任何WHEN条款。 如果没有WHEN条件产生真值，CASE表达方式的值是ELSE条款的结果。 如果省略ELSE条款且没有条件为真，结果为空。

CASE 表达式可以用两种方式：

_简单的_

```
CASE input_expression
when_expression THEN result_expression [ ...n ]
ELSE else_result_expression
END
```

_扩展_

```
CASE
WHEN boolean_expression THEN result_expression [ ...] 
ELSE else_result_expression
enD
```

**input_expression** 将与何时表达式相比较的表达式。 如果input_expression 与 when_expression，整个CASE 表达式的结果将是 THEN之后给出的结果表达式。

**当表达式** 将被比较到 input_expression的表达式。 当输入法表达式匹配此表达式时，整个CASE表达式的结果将是结果表达式之后给出。

**boolean_expression** 表达式，结果必须是一个布尔值。 当这个表达式返回 true时，整个CASE 表达式的结果将是 THEN之后提供的结果表达式。

**结果表达式** 整个CASE表达式可能产生的结果。

**else_result_expression** 当结果无法表达式时，整个CASE 表达式的结果将是此else_result_expression.
