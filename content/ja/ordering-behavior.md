---
title: "行動順にソート"
parent: "データストレージ"
tags:
  - "studio pro"
menu_order: 20
---

## 1つの紹介

`ORDER BY` 節では、結果セットに表示される行の順序を指定することができます。 例えば、 データグリッド内の列をソートすると、列のデータが昇順(最も小さい値)または降順 (最も大きい値が最初) 順序でソートされます。 デフォルトの順序は昇順です。

ただし、場合によっては、ユースケースまたはデータベースエンジン自体によって動作が若干異なります。

## 2参照セットオーダーの動作

列を使用して、多対多の関連付けによって関連付けられたエンティティの属性を表示する場合。 並べ替えは SQL `MIN()` 関数に依存し、 `MIN(属性)` の値を決定し、表示されるテキストの代わりに使用します。

以下は、 `Order` と `Product` エンティティを使用する例です。 データ グリッドの **** 列には、関連する商品の名前が順序ごとに表示されます。

![](attachments/runtime/sorting-reference-sets.png)

**** 列を並べ替えると、下線付きの値が使用され、表示されるテキストは使用されません。 これらの値は、各注文の `MIN(productName)` の結果です。

## 3 NULL値 注文の動作 {#null-ordering-behavior}

SQL では、 `NULL` はデータベースにデータ値が存在しないことを示す特別なマーカーです。 If a sort is applied on a column that contains `NULL` values, the decision whether the `NULLs` should come first or last varies per database type.

### 3.1 NULLデータベースエンジンによるNULLオーダー動作

#### 3.1.1 HSQLDB

If you specify the `ORDER BY` clause, a `NULL` value always comes first before any non-`NULL` value, irrespective of the sort order.

#### 3.1.2 MARIADB, MYSQL, SAP HANA & SQLSERVER

If you specify the `ORDER BY` clause, `NULL` values by default are ordered as less than values that are not `NULL`. `ASC` オーダーを使用すると、 `NULL` の値は、任意のnon-`NULL` の値の前になります。 `DESC` 注文を使用すると、 `NULL` が最後になります。

#### 3.1.3 DB2, ORACLE & POSTGRESQL

If you specify the `ORDER BY` clause, `NULL` values by default are ordered as more than values that are not `NULL`. `ASC` オーダーを使用すると、 `NULL` の値はNULL`NULL` 以外の値の後になります。 `DESC` 注文を使用すると、 `NULL` が最初に表示されます。

### 3.2 デフォルトNULLソート順の概要

この表は、異なるデータベースタイプによって提供される `NULLs` のデフォルトソート順序を示しています。

| NULL順序の動作/データベースタイプ | DB2 | HSQLDB | MARIADB/ MYSQL | 配置 | POSTGRESQL | SAP HANA | SQL サーバー |
| -------------------:|:---:|:------:|:--------------:|:--:|:----------:|:--------:|:--------:|
|     **ASCNULLS最初の** |     |   ✔    |       ✔        |    |            |    ✔     |    ✔     |
|  **ASC NULLS LAST** |  ✔  |        |                | ✔  |     ✔      |          |          |
|    **最初のDESC NULS** |  ✔  |   ✔    |                | ✔  |     ✔      |          |          |
| **DESC NULLS LAST** |     |        |       ✔        |    |            |    ✔     |    ✔     |
