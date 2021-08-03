---
title: "ブール式"
parent: "表現"
menu_order: 50
tags:
  - "studio pro"
  - "表現"
  - "表現"
  - "Boolean"
---

## 1つの紹介

ブール式は、true または false を返す論理演算を実行するために使用できます。

## 2 と

`と` 演算子は2つのブール式式をチェックし、両方の式が true の場合にのみ `true` を返します。

### 2.1 例

以下の例は、式が返す値を示しています。

* 次の入力を使用する場合:

    ```java
    (6 > 4) and (3 < 5)
    ```

    両方の式が `true` であるため、出力は `true` です。

* 次の入力を使用する場合:

    ```java
    ('hello' = 'hallo') and (3 < 5)
    ```

    出力は `false`です。なぜなら、2 番目の式だけが `true` だからです。

## 3 または

`または` 演算子は2つのブール式を組み合わせ、式の少なくとも1つが真の場合は `true` を返します。

### 3.1 例

以下の例は、式が返す値を示しています。

* 整数型の *price* 属性を持つ *product* というエンティティがあります。 *price* 属性は 3 に等しく、 *recommendedPrice* と呼ばれる別の属性があります。

    次の入力を使用する場合:

    ```java
    ($product/price < $product/recommendedPrice : 2) or ($product/price     > 0)
    ```

    式は `true` を返します。式の少なくとも 1 つが true (2 番目のもの) であるためです。 両方の文が true の場合、式は `true` を返すことに注意してください。

* 次の入力を使用する場合:

    ```java
    ('hello' = 'nothello') または ('bye' = 'stillnotbye')
    ```

    式は `false`を返します。

## 4 not

`ではない` 演算子は指定された Boolean 式を否定します。

### 4.1 Input

Boolean型の式。

### 4.2 出力

指定した式の否定を返します。 式が `true`と評価された場合、 `false`を返します。

### 4.3 例

以下の例は、式が返す値を示しています。

* 次の入力を使用する場合:

    ```java
    not('hello' = 'hallo')

    ```

    式は `true` を返します。


* 次の入力を使用する場合:

    ```java
    not(true)
    ```

    式は `false` を返します。



