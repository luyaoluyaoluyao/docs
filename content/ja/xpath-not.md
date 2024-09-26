---
title: "XPath ではありません"
parent: "xpath-constraint-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-not.pdf) をクリックしてください。
{{% /alert %}}

## 1つの概要

`not()` 関数は引数の意味(そしてその結果)を反転させます。

{{% alert type="info" %}}
これは逆比較とは異なる結果を持つことができます(例 `! <code> =` の負の値として XPath が1対多の関係を超えている場合には、 `=`になります。 詳細は以下の例をご覧ください。
{{% /alert %}}

## 2つの例

このクエリは、 *の名前が* "Jansen" と等しくない format@@2 すべての顧客を返します。

```java
//Sales.Customer[not(Name = 'Jansen')]
```

この場合、上記のクエリは次のクエリと同じ結果を返します。

```java
//Sales.Customer[Name != 'Jansen']
```

次のクエリは、少なくとも 1 つの注文を行っていないすべての顧客を返します:

```java
//Sales.Customer[not(Sales.Customer_Order/Sales.Order)]
```

次のクエリは、 ** 注文が `合計価格` が *以上* 30 のすべての顧客を返します。 注文をしていない人も含めて00:

```java
//Sales.Customer[not(Sales.Customer_Order/Sales.Order/TotalPrice > 30000)]
```

The query above does not return the same result as the one below, which returns all the customers who have placed *at least one* order with a `TotalPrice` of *less than* 30,000, regardless of the number of orders they have placed worth more than 30,000:

```java
//Sales.Customer[Sales.Customer_Order/Sales.Order/TotalPrice <= 300000]
```
たとえば、顧客が2つの注文を行った場合、1つは15,000、1つは35です。 00 — このクエリはこの顧客を返しますが、 *not* クエリは返しません。 注文を行っていない顧客は、このクエリによって返されません。
