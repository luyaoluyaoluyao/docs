---
title: "解析 & 格式浮动函数调用"
parent: "表达式"
---

{{% alert type="warning" %}}

这些函数与浮动类型一起被废弃。 使用高精度小数点型号和相关函数代替。

{{% /报警 %}}

关于所有模式可能性，请参阅 [http://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html](http://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html)。

## parseFloat

解析一个字符串值为浮点数。 表示格式和默认值的可选参数。

### 输入参数

*   要解析 类型的值：字符串
*   匹配模式(可选) 类型：字符串
*   默认值(可选) 类型：浮点数

### 产出

匹配输入字符串值的浮动值。 如果无法解析该值(如在，不匹配格式参数或含有非法字符)，将返回默认值。 如果没有提供默认值，则发生错误。

```java
parseFloat('3.45')
```

返回：

```java
3.45
```

默认值：

```java
parseFloat('noFloat'5.05)
```

返回：

```java
5.05
```

格式参数：

```java
parseFloat('3.33', '$#.##')
```

返回：

```java
3.33
```
## 格式浮点数

根据指定的格式将浮动值转换为字符串值。

### 输入参数

*   转换 类型：浮点数
*   结果应该在 类型中的格式：字符串

### 产出

一个 Float 值的字符串表示，以'格式' 参数指定的格式。 类型：字符串

```java
格式浮动(1234.56, '#,###.#')
```

返回：

```java
'1,234.5'
```
