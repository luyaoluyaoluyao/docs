---
title: "XPath 周起日期时间"
parent: "xpate-constraint-function"
---

## 1 概览

`week-fro-dateTime()` 函数从日期时间属性中提取周数，以便它可以用于比较一个值。 值介于1到53之间(属于哪个星期的值将取决于数据库实现)。

## 2 个示例

此查询返回所有在 `日期属性` 中的周数量为 "2" 的日志(例如，"2011-01-13")：


```java
//Logging.log[周起-日期时间(DateAttribute) = 2]
```
