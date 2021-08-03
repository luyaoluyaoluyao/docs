---
title: "OQL RANGEEND"
parent: "oql-functions"
tags:
  - "studio pro"
---

## 1つの説明

`RANGEEND` 関数は、範囲パラメータの終了値を抽出します。

[RANGEBEGIN](oql-rangebegin) and `RANGEEND` are OQL functions that use a parameter, and OQL parameters are only available in [datasets](data-sets) (which are used for generating a report). ページを作成し、データセットがあるレポートを追加する場合 そのデータセットに `RANGEBEGIN` と `RANGEEND` を使用できます。

## 2つの構文

構文は以下の通りです:

```sql
RANGEEND ( $range )
```

`$range` は範囲パラメータを指定する。

## 3つの例

これは、OQL の範囲を使用している例です。 `$range` は先週設定されています。 先週生まれたお客様には次のようなものがあります

```sql
姓として最初に姓として、姓として、名前として、名前として、誕生日として、誕生日として、お客様として、FROMセールスを入力してください。
誕生日は ($rangeLastWeek)
```

この例では、 `WHERE` 節の `RANGEEND` 関数を使用します。 先週末から生まれてきたお客様には次のようなものがあります

```sql
First, LastName as Last, Name AS Name, Birthday AS BDay, CustomerType AS Type FROM Sales.Customer
Where誕生日 > RANGEEND($rangeLastWeek)
```
