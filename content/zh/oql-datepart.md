---
title: "OQL 日期"
parent: "oql-函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-datepart.pdf)。
{{% /报警 %}}

DATEPAT 函数从日期/时间值中检索指定的元素。 此元素是类型整数。

语法如下：

```
DATEPAT ( datepart , date_expression )
```

| 日期部分        | 定义                      | 例如，2005年7月1日星期五使用时，16：34：20 |
| ----------- | ----------------------- | --------------------------- |
| `YEAR`      |                         | 2005                        |
| `去除数`       | 1、2、3或4                 | 3                           |
| `MONH`      | 1 到 12                  | 7                           |
| `DAYOFYEAR` | 1 到 366                 |                             |
| `日`         | 1 到 31                  | 5                           |
| `周一`        | 1 到 53 (取决于数据库实现情况)     |                             |
| `周日`        | 1 到 7 (1 = 星期日，7 = 星期六) | 6                           |
| `房源`        | 0 到 23                  | 16                          |
| `分`         | 0 到 59                  | 34                          |
| `秒`         | 0 到 59                  | 20                          |

**日期部分** 指定要检索的日期/时间值的部分。 这可以是以下内容之一：

**date_expression** 指定获取元素的日期。 这个格式应该用一个表达式解析成一个日期/时间值。
