---
title: "XPath 周从日期开始时间"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-weekday-from-datetime.pdf)。
{{% /报警 %}}

## 1 概览

`周日-dateTime()` 函数从 **日期和时间中提取一周的一天(作为一个数字)** 属性，以便它可以用于比较一个值。 值介于1到7之间(1=星期日，7=星期六)。

## 2 个示例

此查询函数返回周内 `日期属性` 6(星期五)的所有日志：

```java
//Logging.log[周日从日期时间(DateAttribute) = 6]
```
