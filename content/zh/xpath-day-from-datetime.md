---
title: "XPath 日期从日期开始"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`day-dateTime()` 函数从一个 **日期和时间摘取月份值的一天** 属性，以便它可以用来比较一个值。

## 2 个示例

此查询返回所有 `日期属性` 是月份第30天的日志(例如，"2011-12-30")：

```java
//Logging.log[day from -dateTime(DateAttribute) = 30]
```
