---
title: "算術式"
parent: "表現"
---


数多くの算術式がサポートされており、数値型(整数/長さ、浮動小数点数、小数点数)で動作します。

## かけ算

２つの数をかけます。

### 入力パラメータ

*   First number Type: Integer/Long, Float or Decimal
*   2番目の数 タイプ: Integer/Long, Float or Decimal

### 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型になります。

2 つの入力の 1 つが Float 型であり、両方ともが Decimal 型でない場合、結果は Float 型になります。

```java
3 * 4
```

検索結果：

```java
12
```

## Division

２つの数を除算します。 以下の例のように、 `div` または colon ( : ) 構文を使用できます。 コロン( : )構文は分割記号 `÷`に触発されます。 オブジェクトやメンバーを分離するために使用するスラッシュと矛盾するため、従来のスラッシュ( / )構文は使用できません。

### 入力パラメータ

*   First number Type: Integer/Long, Float or Decimal
*   2番目の数 タイプ: Integer/Long, Float or Decimal

### 出力

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型になります。 そうでなければ結果は Float 型になります。

"div" syntax:

```java
3 div 5
```

検索結果：

```java
0.6
```

":" 構文:

```java
12 : 3
```

検索結果：

```java
4.0
```

## Modulo

ある数値の除算の残りを別の数値で計算します。 言い換えれば、m モジュロ n は m = p + k*n に対応します。ここで、p は操作 m モジュロ n の結果です。

### 入力パラメータ

*   First number Type: Integer/Long, Float or Decimal
*   2番目の数 タイプ: Integer/Long, Float or Decimal

### 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型になります。

2 つの入力の 1 つが Float 型であり、両方ともが Decimal 型でない場合、結果は Float 型になります。

```java
23 mod 5
```

値を持つ整数/長さになります

```java
3
```

あるいは、

```java
23 mod 5.6
```

結果は値付きの浮動小数点数になります

```java
0.6
```

## 追加

2 つの数字を追加します。

{{% alert type="info" %}}

詳細は [String 関数 calls](string-function-calls) を参照してください。

{{% /alert %}}

### 入力パラメータ

*   First number Type: Integer/Long, Float or Decimal
*   2番目の数 タイプ: Integer/Long, Float or Decimal

### 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型になります。

2 つの入力の 1 つが Float 型であり、両方ともが Decimal 型でない場合、結果は Float 型になります。

```java
-3 + 4
```

値を持つ整数/長さになります

```java
1
```

```java
4.5 + 3
```

結果は値付きの浮動小数点数になります

```java
7.5
```

## 減算

最初から2つ目の入力を減算します。

### 入力パラメータ

*   First number Type: Integer/Long, Float or Decimal
*   2番目の数 タイプ: Integer/Long, Float or Decimal

### 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型になります。

2 つの入力の 1 つが Float 型であり、両方ともが Decimal 型でない場合、結果は Float 型になります。

```java
5 - 4
```

値を持つ整数/長さになります

```java
1
```

```java
34.4 - 3.1
```

結果は値付きの浮動小数点数になります

```java
31.3
```
