---
title: "XPath 时间从日期开始"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`小时-日期时间()` 函数从 **日期和时间取出小时值** 属性，以便它可以用于比较一个值。

## 2 个示例

此查询返回 `日期属性` 小时部分为8 的所有日志(例如，"2011-12-30 08:00:00")：

```java
//Logging.log[小时-日期时间(DateAttribute) = 8]
```
