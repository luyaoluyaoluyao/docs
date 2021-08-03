---
title: "布尔表达式"
parent: "表达式"
---

### 布尔表达式



布尔表达式可以用于执行逻辑操作，如检查是否保留两个条件。

## 和

组合两个布尔表达式，只返回 True，如果两个表达式都值为 True。

{{% alert type="info" %}}

```java
(6 > 4) and (3 < 5)
```

因为两个表达式都为 True 而评估为 True。

```java
('hello' = 'hallo') (3 < 5)
```

评估为 False ，因为只有第二个表达式是 True。

{{% /报警 %}}

## 或

组合两个布尔表达式，如果至少有一个表达式评价为 True，则返回 True。

{{% alert type="info" %}}

给出一个域实体实例的名称为“$product”，它有一个整数属性“价格”，其值为“3”，另一个整数属性“推荐价格”，其值为“2”， 以下表达式：

```java
($product/价格 < $product/推荐价格: 2) 或 ($product/价格 > 0)
```

将返回 True，因为至少有一个表达式评价为 True (第二个表达式精确)。 请注意，如果两个语句都为 True，则表达式仍然返回 True。

下面的示例返回 False, 因为两个表达式都对应到False:

```java
('hello' = 'nothello') 或('byebye' = 'stilllnotbyebye')
```

{{% /报警 %}}

## 不是

函数“不是”否定指定的布尔表达式。

### Input

布尔型表达式。

### 产出

返回指定表达式的否定。 如果表达式值为 True，它返回 False；否则它返回 True。

{{% alert type="info" %}}

```java
not('hello' = 'hallo')

```

返回：

```java
true

```

和

```java
not(true)

```

返回：

```java
false

```

{{% /报警 %}}
