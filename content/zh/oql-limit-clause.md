---
title: "OQL 限制条款"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-limit-clause.pdf)。
{{% /报警 %}}

限定条款可以返回查询结果的一部分。

语法如下：

```
[ 有限编号] [ OFFSET number ]
```

**LIMIT** 指定必须返回多少行。

**OFFSET** 指定返回结果行之前必须跳过多少行。

{{% alert type="info" %}}

```
从销售处选择姓氏。客户
按姓氏
LIMIT 10
```

此查询获取前十个客户，按其姓氏排序。

{{% /警示%}}!{% alert type="info" %}}

```
从销售处选择姓氏。客户
按姓氏排列的订单
OFFSET 10
```

此查询检索所有客户，除第一个客户外，按其姓氏排序。

{{% /警示%}}!{% alert type="info" %}}

```
从销售处选择姓氏。客户
按姓氏
限定名 10 开关10
```

此查询获取客户的11点到20，按其姓氏排序。

{{% /报警 %}}
