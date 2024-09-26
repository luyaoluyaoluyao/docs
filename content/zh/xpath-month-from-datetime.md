---
title: "XPath 月-从日期时间"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-month-from-datetime.pdf)。
{{% /报警 %}}

## 1 概览

`个月-日期时间()` 函数从 **日期和时间摘取月份值** 属性，以便它可以用来比较一个值。

## 2 个示例

此查询返回月份值 `日期属性` 为12 (12月)的所有日志。 例如，“2011-2012-30”：

```java
//Logging.log[月-从日期时间(DateAttribute) = 12]
```
