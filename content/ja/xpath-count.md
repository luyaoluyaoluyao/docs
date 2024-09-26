---
title: "XPath カウント"
parent: "xpath-query-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-count.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`count()` 関数は、囲まれたクエリで取得したすべてのオブジェクトをカウントし、値を整数として返します。

## 2つの例

このクエリは、すべての注文数を返します:

```java
count(//Sales.Order)
```

このクエリは、「Jansen」という名前の顧客によって発注されたすべての注文の数を返します。

```java
count(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen'])
```
