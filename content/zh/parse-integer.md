---
title: "解析整数"
parent: "表达式"
menu_order: 140
description: "描述解析来自Mendix字符串的整数的函数。"
tags:
  - "studio pro"
  - "表达式"
  - "parse"
  - "整数"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/parse-integer.pdf)。
{{% /报警 %}}

## 1 导言

此文档描述了将字符串转换为整数的函数。

## 2 parseInteger

带一个字符串并解析为整数。

### 2.1 输入参数

下面的表格描述了输入参数：

| 值            | 类型  |
| ------------ | --- |
| 要解析的字符串      | 字符串 |
| 默认值 **(可选)** | 整数  |

### 2.2 产出

产出情况见下表：

| 值                                                       | 类型 |
| ------------------------------------------------------- | -- |
| 一个整数，如果可以从字符串解析它。 如果字符串无法解析为整数，则返回默认值。 如果没有提供默认值，将发生错误。 | 整数 |

### 2.3 实例

下面的例子说明表达式返回的价值：

* 如果您使用以下输入：

    ```java
    parseInteger('42')
    ```

    输出为：

    ```java
    42
    ```

* 如果您使用以下输入：

    ```java
    parseInteger('not_an_integer', 42)
    ```

    输出为：

    ```java
    42
    ```
