---
title: "OQL範囲"
parent: "oql-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-rangebin.pdf) をクリックしてください。
{{% /alert %}}

## 1つの説明

`RANGEBEGIN` 関数は、範囲パラメータの初期値を抽出します。

構文は以下の通りです:

```
RANGEBEGIN( $range)
```

`$range` は範囲パラメータを指定する。

## 2つの例

`RANGEBEGIN` と [RANGEEND](oql-rangeend) は、パラメータを使用する OQL 関数です。 OQL パラメータは、レポートの生成に使用されるデータセットでのみ使用できます。 ページを作成し、データセットがあるレポートを追加する場合 そのデータセットに `RANGEBEGIN` と `RANGEEND` を使用できます。

これは、OQL の範囲を使用している例です。 `$range` は先週設定されています。 先週生まれたお客様には次のようなものがあります

```java
FirstNameとしてFirstNameをLast、Nameとして名前、BDayとして誕生日、CustomerTypeとしてSales.Customer
Birthday IN ($rangeLastWeek)
```

この例では、where-節の `RANGEBEGIN` 関数を使用しています。これは先週初めから生まれたすべての顧客を提供します。

```java
First, LastName as Last, Name as Name, Birthday as BDay, CustomerType as Type from Sales.Customer
where Birthday > RANGEBEGIN($rangeLastWeek)
```
