---
title: "ブーリアン式"
parent: "表現"
---

### ブーリアン式



ブール式は、2つの条件が保持されているかどうかをチェックするなどの論理演算を実行するために使用できます。

## と

2つのブール式式を組み合わせて、両方の式が True に評価された場合にのみ、True を返します。

{{% alert type="info" %}}

```java
(6 > 4) and (3 < 5)
```

両方の式が True であるため、 True に評価されます。

```java
('hello' = 'hallo') and (3 < 5)
```

2番目の式のみが True であるため、 False に評価します。

{{% /alert %}}

## または

2 つの Boolean 式を組み合わせて、少なくとも 1 つの True が評価されている場合に True を返します。

{{% alert type="info" %}}

Given a domain entity instance with name "$product" that has an integer attribute "price" with value "3" and another integer attribute "recommendedPrice" with value "2", the following expression:

```java
($product/price < $product/recommendedPrice : 2) or ($product/price > 0)
```

少なくとも1つの式がTrue(正確には2つ目)に評価されるため、Trueが返されます。 両方の文が True であれば、式は True を返すことに注意してください。

以下の例では False を返します。両方の式は False に評価されるため:

```java
('hello' = 'nothello') または ('bye' = 'stillnotbye')
```

{{% /alert %}}

## いいえ

関数 'not' は指定された Boolean 式を否定します。

### Input

Boolean型の式。

### 出力

指定した式の否定を返します。 式が True と評価されると、False が返されます。そうでなければ、True が返されます。

{{% alert type="info" %}}

```java
not('hello' = 'hallo')

```

戻り値:

```java
true

```

と

```java
not(true)

```

戻り値:

```java
false

```

{{% /alert %}}
