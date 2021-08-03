---
title: "算術式"
parent: "表現"
menu_order: 20
tags:
  - "studio pro"
  - "表現"
  - "算術式"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/arithmetic-expressions.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、式でサポートされている算術演算子について説明します。 これらはすべて、数値データ型(Integer/Long and Decimal)で動作します。

## 2 かけ算

２つの数をかけます。

### 2.1 入力パラメータ

入力パラメータは以下の表に記載されています:

| 値      | タイプ                   |
| ------ | --------------------- |
| 最初の番号  | Integer/Long, Decimal |
| 2番目の番号 | Integer/Long, Decimal |

### 2.2 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型です。

### 2.3 例

次の入力を使用する場合:


```java
2*3
```
出力は:

```java
6
```

## 3 Division

２つの数を除算します。 以下の例のように、 `div` または colon ( `:` ) 構文を使用できます。 コロン( `:` ) の構文は、分割記号 `÷` に触発されます。 従来のスラッシュ( / )構文は、オブジェクトとメンバの分離に使用されるスラッシュと矛盾するため、使用できません。

### 3.1 入力パラメータ

入力パラメータは以下の表に記載されています:

| 値      | タイプ                   |
| ------ | --------------------- |
| 最初の番号  | Integer/Long, Decimal |
| 2番目の番号 | Integer/Long, Decimal |

### 3.2 出力

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型です。

### 3.3 例

使用例を以下に示します。

* `div` 構文の例: 次の入力を使用する場合:

  ```java
  3 div 5
  ```

  出力は:

  ```java
  0.6
  ```

* `:` 構文例: 以下の入力を使用する場合:

  ```java
  12 : 3
  ```

  出力は:

  ```java
  4.0
  ```

### 3.4 備考

除算の結果は、無限の十進展がある場合の近似に過ぎません。 以下の2つの例は、この近似を示しています。

* 次の入力を使用する場合:

    ```java
    3 : 7
    ```

    出力は

    ```java
    0.4285714285714285714285714285714286
    ```

    分割の結果をもとに計算を続けると、予期せぬ結果になる可能性があります。 次の入力:

    ```java
    (3 : 7) * 7
    ```

    結果は以下のようになります。

    ```java
    3.0000000000000000000000000000000002
    ```

* 次の入力を使用する場合:

    ```java
    天井((3:7)*7)
    ```

    出力は

    ```java
    4
    ```

したがって、最後に分割操作を行うことをお勧めします。

## 4 Modulo

ある数値の除算の残りを別の数値で計算します。 In other words, `m` modulo `n` corresponds to: `m = p + k*n`, where `p` is the result of the operation `m` modulo `n`.

### 4.1 入力パラメータ

入力パラメータは以下の表に記載されています:

| 値      | タイプ                   |
| ------ | --------------------- |
| 最初の番号  | Integer/Long, Decimal |
| 2番目の番号 | Integer/Long, Decimal |

### 4.2 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型です。

### 4.3 例

次の入力を使用する場合:

```java
23 mod 5
```

出力は

```java
3
```
## 5つの追加

2 つの数字を追加します。

文字列連結の追加記号を使用するには、 [String 関数呼び出し](string-function-calls) を参照してください。

### 5.1 入力パラメータ

入力パラメータは以下の表に記載されています:

| 値      | タイプ                   |
| ------ | --------------------- |
| 最初の番号  | Integer/Long, Decimal |
| 2番目の番号 | Integer/Long, Decimal |

### 5.2 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型です。

### 5.3 例

次の入力を使用する場合:

```java
-3 + 4
```

出力は

```java
1
```

## 6 ひき算

最初から2つ目の入力を減算します。

### 6.1 入力パラメータ

入力パラメータは以下の表に記載されています:

| 値      | タイプ                   |
| ------ | --------------------- |
| 最初の番号  | Integer/Long, Decimal |
| 2番目の番号 | Integer/Long, Decimal |

### 6.2 出力

2つの入力が両方ともInteger/Long型の場合、結果はInteger/Long型になります。

2 つの入力のいずれかが Decimal 型の場合、結果は Decimal 型です。

### 6.3 例

次の入力を使用する場合:

```java
5 - 4
```

出力は

```java
1
```
