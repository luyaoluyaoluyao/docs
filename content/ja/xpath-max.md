---
title: "XPath 最大"
parent: "xpath-query-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-max.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`max()` 関数は、引数の最大値を返します。

関数は引数として XPath クエリを必要とします。

関数は、集計するクエリ内の列を指定する必要があります。

クエリは数値型の属性を指定する必要があります。

## 2つの例

このクエリは、任意のオブジェクトで見つかった合計金額の最高値を返します:

```java
max(//Sales.Order/TotalPrice)
```

このクエリは、「Jansen」という名前の顧客によって発注された注文の最高合計価格を返します。

```java
max(//Sales.Order[Sales.Customer_Order/Sales.Customer/Name = 'Jansen']/TotalPrice)
```
