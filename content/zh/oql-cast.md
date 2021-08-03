---
title: "OQL CAST"
parent: "oql-函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-cast.pdf)。
{{% /报警 %}}

## 1 导言

CAST函数将表达式转换为特定的数据类型。

语法如下：

```
CAST (表达式作为数据类型)
```

* `表达式` - 指定要转换的表达式
* `data_type` -- 指定要转换表达式的数据类型；数据类型可以是以下内容之一：
  * BOOLEAN
  * 日期
  * 十月
  * 安装
  * LONG
  * 触发中

## 2 支持的转换

下表描述了支持哪些CAST转换：

* :very_check_mark: — — 支持转换
* :very_check_mark:* — 支持转换，但每个数据库的行为不同(见下面的注释)
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
* [2] — 只有当值完全符合字符串长度时，才支持将DATEIME 和 DECIMAL 转换为STRING (有限)。 如果生成的字符串长度小于20，转换可能失败。
