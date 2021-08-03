---
title: "XPath 秒-日期时间"
parent: "xpate-constraint-function"
---

## 1 概览

`秒-日期时间()` 函数从日期时间属性中提取秒数，以便它可以用于比较一个值。

## 2 个示例

此查询返回 `日期属性` 中秒数为30秒的所有日志(例如，"2011-12-30 08:30")：

```java
//Logging.log[秒-日期时间(DateAttribute) = 30]
```
