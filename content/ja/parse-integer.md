---
title: "整数の解析"
parent: "表現"
menu_order: 140
description: "Mendix で文字列から整数を解析する関数を説明します。"
tags:
  - "studio pro"
  - "表現"
  - "parse"
  - "integer"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/parse-integer.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

この文書では、文字列を整数に変換する関数について説明します。

## 2 parseInteger

文字列を取得して整数に解析します。

### 2.1 入力パラメータ

入力パラメータは以下の表に記載されています:

| 値               | タイプ |
| --------------- | --- |
| 解析する文字列         | 文字列 |
| デフォルト値 **(任意)** | 整数  |

### 2.2 出力

出力は以下の表に記載されています:

| 値                                                                        | タイプ |
| ------------------------------------------------------------------------ | --- |
| 文字列から解析できる整数。 文字列を整数に解析できない場合、デフォルト値が返されます。 デフォルト値が指定されていない場合、エラーが発生します。 | 整数  |

### 2.3 例

以下の例は、式が返す値を示しています。

* 次の入力を使用する場合:

    ```java
    parseInteger('42')
    ```

    出力は

    ```java
    42
    ```

* 次の入力を使用する場合:

    ```java
    parseInteger('not_an_integer', 42)
    ```

    出力は

    ```java
    42
    ```
