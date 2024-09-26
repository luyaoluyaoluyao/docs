---
title: "XPath 演算子"
parent: "xpath-constraints"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-operators.pdf) をクリックしてください。
{{% /alert %}}

## 1 XPath クエリ制約の場合

以下の演算子は、Studio Pro および Java コード内の XPath クエリ制約内で使用することができます。

| 演算子     | 説明    | 例                              | 戻り値                                                                                         |
| ------- | ----- | ------------------------------ | ------------------------------------------------------------------------------------------- |
| `=`     | 等しい   | `price = 9.80`                 | true、値段が9.80、値段が9.90の場合はfalse、                                                              |
| `!=`    | 等しくない | `price != 9.80`                | true 値が 9.90 の場合、価格が 9.80 の場合は false                                                        |
| `<`  | 以下    | `価格 < 9.80`                 | true。価格が9.70の場合、価格が9.80の場合はfalse。                                                           |
| `<=` | 以下    | `price <= 9.80`             | true、値段が9.80、値段が9.90の場合はfalse、                                                              |
| `>`  | より大きい | `価格 > 9.80`                 | true 値が 9.90 の場合、価格が 9.80 の場合は false                                                        |
| `>=` | 以上    | `price >= 9.80`             | 価格が9.80の場合はtrue、価格が9.70の場合はfalse、                                                           |
| `または`   | または   | `price = 9.80 or price = 9.70` | true、価格が9.80、価格が9.60の場合はfalse、                                                              |
| `と`     | そして、  | `price = 9.80 and amount = 1`  | 価格が9.80で金額が1の場合はtrue、価格が9の場合はfalse。 0と金額が1、価格が9.80、金額が2の場合はfalse、価格が9.70、金額が2の場合はfalseとなります |

## 2 Java コード用

また、以下の演算子は Java コードのみでサポートされています。

| 演算子   | 説明       | 例         | 戻り値 |
| ----- | -------- | --------- | --- |
| `+`   | 追加       | `6 + 4`   | 10  |
| `-`   | 減算       | `6 - 4`   | 2   |
| `*`   | かけ算      | `6 * 4`   | 24  |
| `div` | Division | `8 div 4` | 2   |
