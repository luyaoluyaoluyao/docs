---
title: "XPath を含む"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-contains.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`contains()` 関数は、string 属性に特定の文字列 (大文字と小文字を区別しない) が含まれているかどうかをテストします。

## 2つの例

このクエリは、名前が文字列 `an` を含むすべての顧客を返します:

```java
//Sales.Customer[contains(Name, 'an')]
```

"andy" や "Jan" という名前のお客様は、"an" がその名前の一部であるため、例えば返却されます。