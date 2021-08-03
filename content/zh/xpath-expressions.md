---
title: "XPath 表达式"
parent: "xpat-conditions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-expressions.pdf)。
{{% /报警 %}}

## 1 概览

表达式用于生成一个真值的值。

有三种表达式可用于约束：

* 与操作者比较
* 职能
* 存在表达式

## 2 个比较

A comparison expression consists of two attributes or values separated by a comparison [operator](xpath-operators) like `=`, `<=,` and `>`.

### 2.1 实例

例如，这个查询会检索名称为“Jansen”的所有客户：

```java
//Sales.Customer[name = 'Jansen']
```

此查询检索价格总额小于50.00欧元的所有订单：

```java
//Sales.Order[TotalPrice < 50.00]
```

此查询检索所有有至少一个未支付订单的客户：

```java
//Sales.Customer[Sales.Customer_order/Sales.Order/HasPayed = false()]
```

此查询检索所有与他们居住的城市具有相同名称的客户：

```java
//Sales.Customer[name = 城市]
```

此查询检索使用给定唯一身份号码下订单的客户：

```java
//Sales.Customer_Order = 'ID_124123512341']
```

通过以下查询可以检索到相同的结果：

```java
//Sales.Customer[Sales.Customer_Order/ID = 'ID_124123512341']
```

不过，强烈建议不要使用上面的注解。 这是因为它的执行效率低下，而且由于数据库处理的方式将导致性能下降。

## 3 职能

关于可用函数的信息，请参阅 [XPath 约束函数](xpath-constraint-functions)。

## 4 Exist-Expressions {#exist}

最后一种表达式是存在的表达式，可用来检查某个特定的关联是否填写。

### 4.1 实例

此查询检索所有已下单的客户：

```java
//Sales.Customer[Sales.Customer_order/Sales.Order]
```

此查询检索所有没有下单的客户：

```java
//Sales.Customer[not(Sales.Customer_order/Sales.Order)]
```
