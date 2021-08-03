---
title: "XPath 长度"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`length()` 函数返回字符串属性或值的长度。

## 2 个示例

此查询返回所有客户端的 `名字` 个或更多字符：

```java
//Sales.Customer[length(名字) >= 5]
```
