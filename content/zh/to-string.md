---
title: "到字符串"
parent: "表达式"
---


将各种数据类型的值转换为字符串的基本函数。

## toString

将指定的值转换为字符串表示.

如果您需要完全控制输出格式，请考虑使用数据类型的特定格式函数。 例如，对于小数点，使用 [格式小数组](parse-and-format-decimal-function-calls)。

### 输入参数

应转换为字符串的值。 支持 [类型](data-types): Integer/Long, 十进制, Float (废弃), 日期和枚举. 在枚举的情况下，返回枚举值的键值，而不是标题。 也在表达式中查看 [枚举](enumerations-in-expressions)。

```java
toString(1.4)
```

返回：

```java
'1.4'
```

与日期时间：

```java
toString(dateTime(2007))
```

返回：

```java
'Mon Jan 01 00:00:00 CET 2007'
```
