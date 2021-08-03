---
title: "XPath 年从日期开始"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-year-from-datetime.pdf)。
{{% /报警 %}}

## 1 概览

`从dateTime()` 函数从 `日期和时间取出年份` 属性，以便它可以用于比较一个值。

## 2 个示例

此查询返回 `日期属性` 中年数为"2011" 的所有日志(例如，"2011-12-30")：

```java
//Logging.Log[年份从日期时间(DateAttribute) = 2011]
```
