---
title: "表达式的枚举数"
parent: "表达式"
menu_order: 170
tags:
  - "studio pro"
  - "表达式"
  - "枚举数"
  - "表达式"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/enumerations-in-expressions.pdf)。
{{% /报警 %}}

## 1 导言

枚举由 `<modulename>引用。<enumerationname>。<enumerationvalue>`。

例如，您有一个名为 *订单处理*的模块， 枚举 *状态* 定义了两个可能的值： *开始* 和 *完成*。

To set the value of an attribute in a change list, object, or variable activity to *completed*, use the following input:

```java
已完成
```

条件语句也是可能的：

```java
如果4>3 则
  orderProcessing.Status.completed
否则
  OrderProcessing.Status.completed
```

## 2 getCaption

`getCaption` 函数需要一个枚举值并返回此值的标题。 *标题* 是一个可翻译的字符串，这个函数的结果取决于当前语言。

### 2.1 输入参数

作为输入参数，您可以使用任何枚举的枚举值。

### 2.2 产出

产出情况见下表：

| 值            | 类型  |
| ------------ | --- |
| 当前语言中枚举值的标题。 | 字符串 |

### 2.3 例子

如果您使用以下输入：

```java
getCaption($Customer/成绩)
```

输出可以是：

```java
Gouden
```

## 3 getKey

`getKey` 函数需要枚举值并返回此值的密钥 (Studio Pro中称为 *Name*)。 密钥是枚举值的技术名称，语言是独立的。 欲了解更多信息，请参阅 [枚举](enumerations)。

### 3.1 输入参数

作为输入参数，您可以使用任何枚举的枚举值。

### 3.2 产出

产出情况见下表：

| 值                | 类型  |
| ---------------- | --- |
| 当前语言的枚举值的键值(名称)。 | 字符串 |

### 3.3 示例

如果您使用以下输入：

```java
getKey($Customer/成绩)
```

输出可以是：

```java
金色
```

## 4 阅读更多

* [枚举数](enumerations)