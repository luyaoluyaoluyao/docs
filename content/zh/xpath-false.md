---
title: "XPath 错误"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-false.pdf)。
{{% /报警 %}}

## 1 概览

函数 `false()` 返回布尔值 `false`。

在 XPath 查询中使用值 `true` 或 `fals` 需要使用 `true()` 和 `false()` 函数或附上引号中的值。

## 2 个示例

此查询返回所有未被分类为黄金客户的客户：

```java
//Sales.Customer[IsGoldCustomer = false()]
```
