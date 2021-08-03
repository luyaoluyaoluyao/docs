---
title: "OQL RANGEEGIN"
parent: "oql-函数"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-rangebin.pdf)。
{{% /报警 %}}

## 1 个描述

`RANGEBEGIN` 函数提取一个范围参数的初始值。

语法如下：

```
英雄( $range)
```

`$range` 指定了范围参数。

## 2 个示例

`RANGEBEGIN` and [RANGEEND](oql-rangeend) 是使用参数的 OQL 函数， 和 OQL 参数仅可在数据集中获取(用于生成报告)。 当您创建一个页面并添加具有数据集的报告时， 您可以在该数据集中使用 `RANGEBEGIN` and `RANGEEND`

这是在 OQL 中使用范围的一个例子，在这里 `$range` 设置为上星期。 这将给您所有在上周出生的客户：

```java
选择姓氏作为姓氏，姓氏作为姓名，生日作为生日作为生日，客户类型作为销售的类型。客户
生日在 ($rangeLastWeek)
```

此示例使用 `RANGEBEGIN` 函数，在其中的条款中，这将给您所有自上周开始以来出生的客户：

```java
选择姓氏作为第一个名字，姓氏作为姓名，生日作为白天，客户类型作为销售的类型。客户
生日 > RANGEBEGIN($rangeLastWeek)
```
