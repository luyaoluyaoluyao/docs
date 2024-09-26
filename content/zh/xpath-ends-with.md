---
title: "XPath 端口为"
parent: "xpate-constraint-function"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-ends-with.pdf)。
{{% /报警 %}}

## 1 概览

`结束-with()` 函数检查字符串属性是否以特定字符串(大小写不敏感)作为子字符串。

## 2 个示例

此查询返回名称以子字符串 `sen` 结尾的所有客户：

```java
//Sales.Customer[ends-with(名称, 'sen')]
```

名称为“Jansen”或“Isaacsen”的客户将被退回，例如，这两个名称都以“sen.”结尾。

