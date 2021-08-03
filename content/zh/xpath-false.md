---
title: "XPath 错误"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

函数 `false()` 返回布尔值 `false`。

在 XPath 查询中使用值 `true` 或 `fals` 需要使用 `true()` 和 `false()` 函数或附上引号中的值。

## 2 个示例

此查询返回所有未被分类为黄金客户的客户：

```java
//Sales.Customer[IsGoldCustomer = false()]
```
