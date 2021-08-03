---
title: "XPath 周日-日期时间"
parent: "xpate-constraint-function"
---

## 1 概览

`周日-dateTime()` 函数从日期时间属性中提取天数(周数)，这样它就可以用来比较一个值。 值介于1到7之间(1=星期日，7=星期六)。

## 2 个示例

此查询返回所有在 `日期属性` 中的工作日数量为 6 的日志(例如，"星期五2011-12-30")：

```java
//Logging.log[日从日期时间(DateAttribute) = 6]
```
