---
title: "数学関数の呼び出し"
parent: "表現"
---


## 最大

指定した引数から最大値を返します。

### 入力パラメータ

*   日付と時刻のいずれかまたは数値の型(整数/ロング、浮動小数点または小数)のいずれかの値のいずれかです。

### 出力

指定した引数から最大値を返します。 引数が日付と時刻の型の場合、結果は日付と時刻の型でもあります。 引数が数値の場合、結果は最も正確な型になります。 例えば、Integer/Long と Decimal の両方の引数が指定された場合、結果は Decimal 型になります。

Type: Integer/Long または Decimal

```java
max(5, 1, 5, 6.7)
```

戻り値:

```java
6.7
```

を指定します。

## 分

指定した引数から最小値を返します。

### Input

日付と時刻のいずれかまたは数値の型(整数/ロング、浮動小数点または小数)のいずれかの値のいずれかです。

### 出力

指定した引数から最小値を返します。 引数が日付と時刻の型の場合、結果は日付と時刻の型でもあります。 引数が数値の場合、結果は最も正確な型になります。 例えば、Integer/Long と Decimal の両方の引数が指定された場合、結果は Decimal 型になります。

Type: Integer/Long または Decimal

```java
min(5, 1, 5, 6.7)
```

戻り値:

```java
1
```

型"10進数"

## ラウンド

数値を特定の精度に丸めます。

### Input

*   a number Type: Integer/Long, Float or Decimal

*   精度 (任意) タイプ: Integer/Long

### 出力

**設定**では、 **ラウンド番号** のオプションを設定できます。
*   **ゼロ** オプション(「商用丸め」とも呼ばれます)から半分離れた場合、+2.5は+3、-1.5は-2になります。
*   **最も近い偶数** オプションの半分（「バンカーの丸め」とも呼ばれます）は、  [IEEE 754](http://en.wikipedia.org/wiki/IEEE_floating_point "IEEE floating point") コンピューティング関数と演算子で使用されるデフォルトの丸めモードです。 例えば+23です は+24、+24.5、-22.5は-22、-21.5と同様に+24になります。

2 番目のオプションパラメータは、丸めの精度を決定します。 デフォルト値は 0 です。 結果は、可能な限り最も正確なタイプになります。 精度が 0 の場合、結果は integer/long 型になります。 そして、その他のすべての精度値では、結果は 10 進型になります。

Type: Integer/Long または Decimal

```java
round(3.5)
```

戻り値:

```java
4
```

型"Integer/Long"

と

```java
round(88.725,2)
```

戻り値:

```java
88.72
```

10進数の型

## random

乱数を生成する >= 0.0 と < 1.0

### 出力

0.0と1.0の間の乱数 タイプ: 数値

```java
random()
```

## 床

整数に丸められます (入力以下の最大の整数を返します)。

### Input

*   a number Type: Integer/Long, Float or Decimal

### 出力

入力値は、最も近い整数に切り下げられます。

Type: Integer/Long

```java
floor(3.9)
```

戻り値:

```java
3
```

と

```java
床(-1.2)
```

戻り値:

```java
-2
```

## ceil

最大の整数まで丸めます (入力以上の最小の整数を返します)。

### Input

*   a number Type: Integer/Long, Float or Decimal

### 出力

入力値は最も近い整数に切り上げられます。

Type: Integer/Long

```java
天井(3.2)
```

戻り値:

```java
4
```

と

```java
ceil(-1.9)
```

戻り値:

```java
-1
```

## pow

指数関数を返します。

### Input

*   a number Type: Integer/Long, Float or Decimal
*   a power Type: Integer/Long, Float or Decimal

### 出力

n^pのように、パワーへの数。 その結果、最も正確なタイプが必要になります。

Type: Integer/Long または Decimal

```java
pow(2, 3)
```

戻り値:

```java
8
```

型"Integer/Long"

と

```java
pow(2.5, 3)
```

戻り値:

```java
15.625
```

型"10進数"

標準Javaライブラリはこれらの計算を高精度でサポートしていないため、小数指数による「pow」の計算は精度が低い場合があります。 この場合、高精度が必要な場合は、カスタム Java アクションに専用ライブラリを使用します。

## abs

数値の絶対値を返します(すなわち、負ではありません)。

### Input

*   a number Type: Integer/Long, Float or Decimal

### 出力

入力の絶対値。負になることはありません。 正方形をとってから、正方形の根に相当します。

Type: Integer/Long または Decimal

```java
abs(-5)
```

と

```java
abs(5)
```

両方のリターン:

```java
5
```
## floatsEqual

小数点pに2つの数字を比較します。これは正確さに等しい値です。

{{% alert type="warning" %}}

この関数は Float 型とともに非推奨となります。 代わりに高精度の小数タイプを使用します。

{{% /alert %}}

### Input

*   a number Type: Integer/Long or Float
*   別の数値 タイプ: Integer/Long or Float
*   精度 タイプ: Integer/Long

### 出力

指定された精度を与えられた2つの数値が等しいかを示す値。

Type: Boolean

```java
floatsEqual(0.51, 0.50, 1)
```

戻り値:

```java
true
```

と

```java
floatsEqual(0.51, 0.50, 2)
```

戻り値:

```java
false
```

## 通貨Equal

floatsEqual を参照してください。

{{% alert type="warning" %}}

この関数は Float 型とともに非推奨となります。 代わりに高精度の小数タイプを使用します。

{{% /alert %}}
