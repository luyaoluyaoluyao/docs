---
title: "XPath の長さ"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-length.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`length()` 関数は、文字列属性または値の長さを返します。

## 2つの例

このクエリは、5文字以上の `FirstName` を持つすべての顧客を返します。

```java
//Sales.Customer[length(FirstName) >= 5]
```
