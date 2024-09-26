---
title: "非ary 表达式"
parent: "表达式"
menu_order: 10
tags:
  - "studio pro"
  - "取消表达式"
  - "表达式"
  - "表达式"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/unary-expressions.pdf)。
{{% /报警 %}}

## 1 导言

一个不小心的负操作者被用来将一个数字从负数转换为正数，反之亦然。

{{% alert type="info" %}}

没有任何疏忽。

{{% /报警 %}}

## 2 个示例

下面的示例表示“8”的负值。

```java
-8
```

当使用的变量已经具有负值时，结果是正数。

例如，如果 $myVariable 有整数值“-7”：

```java
-$myVariable
```

输出为：

```java
7
```

