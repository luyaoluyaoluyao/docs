---
title: "XPath 长度"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-length.pdf)。
{{% /报警 %}}

## 1 概览

`length()` 函数返回字符串属性或值的长度。

## 2 个示例

此查询返回所有客户端的 `名字` 个或更多字符：

```java
//Sales.Customer[length(名字) >= 5]
```
