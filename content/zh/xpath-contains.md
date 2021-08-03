---
title: "XPath 包含"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`contains()` 函数测试字符串属性是否包含一个特定的字符串 (大小写不敏感) 作为子字符串。

## 2 个示例

此查询返回包含字符串 `一个` 的所有客户：

```java
//Sales.Customer[contains(name, 'an')]
```

名称为“Andy”或“Jan”的客户将被退回，例如，“an”是这些名字的一部分。