---
title: "表达式的枚举数"
parent: "表达式"
---


枚举被引用了 <modulename>.<enumerationname>.<enumerationvalue>

假设一个模块“订单处理”，在该模块中，枚举的“状态”被定义为两个可能的值：“开始”和“已完成”。 要在更改动作中将属性的值设置为“已完成”，请使用以下代码：

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

## 获取标题

接受枚举值并返回此值的字幕。 标题是一个可翻译的字符串，这个函数的结果取决于当前的语言。

### 输入参数

*   枚举值 类型：任何枚举值

### 产出

当前语言中枚举值的标题。 类型：字符串

```java
getCaption($NewEntity/ TestEnum)
```

## getKey

接受枚举值并返回此值的键 (在模型中的名称)。 密钥是枚举值的技术名称，语言是独立的。 还见 [枚举值](enumeration-values)。

### 输入参数

*   枚举值 类型：任何枚举值

### 产出

枚举值的 类型： 字符串

```java
getKey($NewEntity/TestEnum)
```
