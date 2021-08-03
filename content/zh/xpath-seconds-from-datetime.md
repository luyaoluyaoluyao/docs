---
title: "XPath 秒起日期时间"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`秒-日期时间()` 函数提取 **日期和时间的秒数** 属性用于比较一个值。

## 2 个示例

此查询返回所有 `日期属性` 秒数是 30 的日志(例如，"2011-12-30 08:30")：

```java
//Logging.log[秒-日期时间(DateAttribute) = 30]
```
