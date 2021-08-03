---
title: "XPath 式"
parent: "\"xpath-constraints\"#"
---

## 1つの概要

式は制約の中で使用され、true の値を生成します。

制約に使用できる式には3種類あります。

* 演算子との比較
* 関数
* 存在する表現

## 2つの比較

A comparison expression consists of two attributes or values separated by a comparison [operator](xpath-operators) like `=`, `<=,` and `>`.

### 2.1 例

例えば、このクエリでは、名前が "Jansen" のすべての顧客を取得します。

```java
//Sales.Customer[Name = 'Jansen']
```

このクエリは、合計価格が50.00ユーロ未満のすべての注文を取得します。

```java
//Sales.Order[TotalPrice < 50.00]
```

このクエリは、少なくとも1つの未払い注文を持っているすべての顧客を取得します:

```java
//Sales.Customer[Sales.Customer_Order/Sales.Order/HasPayed = false()]
```

このクエリは、住んでいる都市と同じ名前を持つすべての顧客を取得します:

```java
//Sales.Customer[Name = City]
```

このクエリは、指定された一意の識別番号で注文を行った顧客を取得します:

```java
//Sales.Customer[Sales.Customer_Order = 'ID_124123512341']
```

次のクエリを実行すると、同じ結果を取得できます。

```java
//Sales.Customer[Sales.Customer_Order/Sales.Order/ID = 'ID_124123512341']
```

ただし、上記の表記は使用しないことを強くお勧めします。 これは、その実行が非効率であり、データベースによって処理される方法によってパフォーマンスが低下するためです。

## 3つの機能

使用可能な関数については、 [XPath 制約関数](xpath-constraint-functions) を参照してください。

## 4 つの式が存在します

式の最後のタイプは、特定の関連付けが満たされているかどうかを確認するために使用できる exist-expression です。

### 4.1 例

このクエリは、少なくとも 1 つの注文を行ったすべての顧客を取得します。

```java
//Sales.Customer[Sales.Customer_Order/Sales.Order]
```

このクエリは、注文を行っていないすべての顧客を取得します:

```java
//Sales.Customer[not(Sales.Customer_Order/Sales.Order)]
```
