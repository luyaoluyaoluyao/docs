---
title: "XPath True"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

函数 `true()` 返回布尔值 `true`

在 XPath 查询中使用值 `true` 或 `fals` 需要调用 `true()` 或 `false()` 函数。 或在引号中附上值。

## 2 个示例

此查询返回分类为“gold customers”的所有客户：

```java
//Sales.Customer[IsGoldCustomer = true()]
```

