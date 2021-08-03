---
title: "XPath 日期从日期开始时间"
parent: "xpate-constraint-function"
---

## 1 概览

`day-dateTime()` 函数从日期时间属性中提取天数，以便它可以用于比较一个值。

## 2 个示例

此查询返回所有 `日期属性` 天数为30天的日志(例如，"2011-12-30")：

```java
//Logging.log[day from -dateTime(DateAttribute) = 30]
```
