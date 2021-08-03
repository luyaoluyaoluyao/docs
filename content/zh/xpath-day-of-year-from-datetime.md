---
title: "XPath 年从日期开始"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`从-dateTime()` 函数从当年的一个 **日期和时间摘取当天** 属性，以便它可以用来比较一个值。 数值从1月1日到366日不等（因为跳跃年份）。

## 2 个示例

此查询函数返回所有年份在 `日期属性` 中的日子是 30 的日志(例如，"2011-01-30" 和 "2012-01-30")：

```java
//Logging.log[日从日期时间(DateAttribute) = 30]
```
