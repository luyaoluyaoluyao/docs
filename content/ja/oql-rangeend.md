---
title: "OQL RANGEEND"
parent: "oql-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-rangeend.pdf) をクリックしてください。
{{% /alert %}}

## 1つの説明

`RANGEEND` 関数は、範囲パラメータの終了値を抽出します。

構文は以下の通りです:

```
RANGEEND ( $range )
```

`$range` は範囲パラメータを指定する。

## 2つの例

[RANGEBEGIN](oql-rangebegin) と `RANGEEND` は、パラメータを使用する OQL 関数です。 OQL パラメータは、レポートの生成に使用されるデータセットでのみ使用できます。 ページを作成し、データセットがあるレポートを追加する場合 そのデータセットに `RANGEBEGIN` と `RANGEEND` を使用できます。

これは、OQL の範囲を使用している例です。 `$range` は先週設定されています。 先週生まれたお客様には次のようなものがあります

```java
FirstNameとしてFirstNameをLast、Nameとして名前、BDayとして誕生日、CustomerTypeとしてSales.Customer
Birthday IN ($rangeLastWeek)
```

この例では、where-句の `RANGEEND` 関数を使用しています。これは先週末以降に生まれたすべての顧客を提供します。

```java
FirstNameとしてFirstNameをLastとして、Nameとして名前をBDayとして、CustomerTypeをSalesから選択します。Customer
Birthday > RANGEEND($rangeLastWeek)
```
