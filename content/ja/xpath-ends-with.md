---
title: "XPath で終了"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-ends-with.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`ends-with()` 関数は、文字列属性が特定の文字列 (大文字と小文字を区別しない) で終わるかどうかをチェックします。

## 2つの例

このクエリは、サブ文字列 `sen` で終わるすべての顧客を返します。

```java
//Sales.Customer[ends-with(Name, 'sen')]
```

「ヤンセン」または「イサクセン」という名前のお客様は、どちらも「せん」で終わるので返却されます。

