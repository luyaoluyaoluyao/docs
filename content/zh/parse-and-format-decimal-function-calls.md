---
title: "解析和格式小数点函数调用"
parent: "表达式"
---

欲了解所有模式可能性的详情，请参阅 [Class DecimalFormat](http://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html)。

## parseDecimal

解析字符串值为十进制值。 允许格式和默认值的可选参数。

### 输入参数

* 要解析的值
    * 类型：字符串
* 默认值(可选)
    * 类型：十进制或为空

### 产出

与输入字符串匹配的十进制值。 如果无法解析值(意指不匹配格式参数或包含非法字符)，将返回默认值。 如果没有提供默认值，则发生错误。

* `parseDecimal('3.45')` 返回 3.45
* `parseDecimal('noDecimal', 5.05)` 返回 5.05
* `parseDecimal('noDecimal'，空)` 返回

## formatDecimal

根据指定格式将十进制值转换为字符串值。

### 输入参数

* 要转换的值
    * 类型：小数
* 基于 Java 库的结果格式 `十进制格式` (详情，请参阅 [类十进制格式](https://docs.oracle.com/javase/8/docs/api/java/text/DecimalFormat.html))
    * 类型：字符串
* 结果应格式化的区域(可选)
   * 支持的值，请参阅 [forLanguageTag](https://docs.oracle.com/javase/8/docs/api/java/util/Locale.html#forLanguageTag-java.lang.String-)
   * 当忽略时，用户配置的区域设置已被使用
   * 由 Mendix 7.3 支持
   * 类型：字符串

### 产出

在 `格式` 参数指定的格式中的十进制字符串表示.

* 类型：字符串

```java
formatDecimal(1234.56, '#,###.#')
```

返回 (取决于语言设置):

```java
'1,234.5' 或 '1.234,5'
```

```java
formatDecimal(1234.56, '¤ #,##0.00')
```

返回 (取决于语言设置):

```java
“1.234.50欧元”或“1,234.50美元”
```

```java
formatDecimal(0.56, '% ##0')
```

返回：

```java
'% 56' 
```
