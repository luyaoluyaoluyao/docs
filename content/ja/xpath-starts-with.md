---
title: "XPath で開始"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-starts-with.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`starts-with()` 関数は、文字列属性が特定の文字列 (大文字と小文字を区別しない) で始まるかどうかをテストします。

## 2つの例

このクエリは、名前が文字列「ヤンス」で始まるすべての顧客を返します。

```java
//Sales.Customer[starts-with(Name, 'Jans')]
```

「Jansen」という名前のお客様は、「Jans」という名前で始まるため、例えば「Jansen」という名前のお客様が返されます。
