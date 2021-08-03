---
title: "XPath 启动"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

## 1 概览

`起始于()` 函数测试字符串属性是否以特定字符串(大小写不敏感)作为子字符串开始。

## 2 个示例

此查询返回名称以字符串"Jans"开头的所有客户：

```java
//Sales.Customer[starts-with(Name, 'Jans')]
```

名称为“Jansen”的客户将会被退回，比如，因为名称开头是“Jans.”。
