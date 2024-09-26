---
title: "OQL DATEDIFF"
parent: "oql-函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-datedeiff.pdf)。
{{% /报警 %}}

DATEDIFF 函数返回两个给定日期/时间值之间的差额。 差异是在指定的单元中给出。

语法如下：

```
DATEDIFF ( unit , startdate_expression, enddate_expression )
```

**单位**

指定要检索的日期/时间值单位。 这可以是以下内容之一：

`是, <code>QUARTER`, `MONTH`, `天`, `WEEK`, `HOUR`, `MINTE` 或 `SECOND`

**startdate_expression** 指定所计算的周期的开始日期。 这个格式应该用一个表达式解析成一个日期/时间值。

**enddate_expression** 指定所计算的周期的结束日期。 这个格式应该用一个表达式解析成一个日期/时间值。
