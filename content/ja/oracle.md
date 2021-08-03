---
title: "Oracle"
parent: "データストレージ"
menu_order: 60
---

## 1つの紹介

Oracleデータベースを使用するMendixの動作には、PostgreSQLデータベースの使用と比較して若干の違いがあります。 これらの違いは以下に記載されています。

## 2 無制限の動作 & 非常に長い文字列

### 2.1 比較関数

Oracle does not support unlimited strings or strings with a specified size greater than 2000 characters when using the equal (`=`) or not equal (`!=`) operators in XPath constraints. しかし、 `contains()`、 `starts-with()`、 および `ends-with()` を含む関数をサポートしています。

### 2.2 並べ替え、グループ化 & 集計化

ソート、グループ化はできません または、 `count()` のような無制限の文字列や、2000文字を超える指定された長さの文字列に対して集計関数を使用します。 これは、このような長い文字列または無制限の文字列が CLOB データ型で実装されているためです。 文字列属性の長さを減らすか、データグリッドから削除することを検討してください。

### 2.3 DISTINCT 属性の選択

2000文字を超える文字列タイプのDISTINCT属性を選択することは、CLOBデータ型を持つDISTINCTカラムを選択するというOracleの既知の制限により、Mendixではサポートされていません。 この制限に遭遇した場合 次のようなメッセージを含むログに例外が発生することがあります: **Error Msg = ORA-06502: PL/SQL: 数値または値エラー: 文字列バッファが小さすぎます**.
