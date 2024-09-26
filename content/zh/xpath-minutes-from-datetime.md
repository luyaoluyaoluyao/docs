---
title: "XPath 分钟从日期开始"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-minutes-from-datetime.pdf)。
{{% /报警 %}}

## 1 概览

`分钟从-dateTime()` 函数从 **日期和时间** 提取分钟值，这样它可以用来比较一个值。

## 2 个示例

此查询返回 `日期属性` 分钟部分的所有日志(例如"2011-12-30 08:30:00)：

```java
//Logging.Log[分钟-从日期时间(DateAttribute) = 30]
```
