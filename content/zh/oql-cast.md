---
title: "OQL CAST"
parent: "oql-函数"
tags:
  - "studio pro"
---

## 1 个描述

`CAST` 函数将表达式转换为特定的数据类型。

## 2 种语法

语法如下：

```sql
CAST (表达式作为数据类型)
```

### 2.1 表达式

`表达式` 指定了要转换的表达式。

### 2.2 数据类型

`data_type` 指定要转换表达式的数据类型。 数据类型可以是下列类型之一：

* `BOOLEAN`
* `日期`
* `十月`
* `安装`
* `LONG`
* `触发中`

## 3 支持的转换

下表描述了哪些 `CAST` 转换被支持：

* :very_check_mark: — — 支持转换
* :very_check_mark:* - 支持转换，但每个数据库的行为不同。
* six-不支持转换

| 从 \ 到  | BOOLEAN | 日期 | 十月 | 安装 | LONG | STRING (无限制) |                   STRING (有限)                   |
| ------- |:-------:|:--:|:--:|:--:|:----:|:------------:|:-----------------------------------------------:|
| BOOLEAN |    ✔    | ✘  | ✘  | ✘  |  ✘   |      ✔*      | :very_check_mark:*<sup><small>1</small></sup> |
| 日期      |    ✘    | ✔  | ✘  | ✘  |  ✘   |      ✔*      | :very_check_mark:*<sup><small>2</small></sup> |
| 十月      |    ✘    | ✘  | ✔* | ✔* |  ✔*  |      ✔*      | :very_check_mark:*<sup><small>2</small></sup> |
| 安装      |    ✘    | ✘  | ✔  | ✔  |  ✔   |      ✔       |                        ✔                        |
| LONG    |    ✘    | ✘  | ✔  | ✔  |  ✔   |      ✔       |                        ✔                        |
| 触发中     |    ✘    | ✘  | ✔  | ✔  |  ✔   |      ✔       |                        ✔                        |
* [1] — — 支持STRING (有限)只有在生成的字符串长度为P-5时才支持。
* [2] — 只有当值完全符合字符串长度时，才支持将DATEIME 和 DECIMAL 转换为STRING (有限)。 如果生成的字符串长度为 < 20，转换可能失败。
*

## 4 示例

`CAST` 的常用案例是将您的日期从 `DATEIME` 数据类型转换成更易读 `STRING` 类型：

```sql
CAST ( your_datetime_variable AS string)
```
