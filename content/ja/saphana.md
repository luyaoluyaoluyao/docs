---
title: "SAP HANA"
parent: "データストレージ"
menu_order: 70
tags:
  - "studio pro"
---

## 1つの紹介

SAP HANA データベースを使用した Mendix の動作には、PostgreSQL データベースと比較して若干の違いがあります。 これらの違いは以下に記載されています。

## 2関連属性の順序

いずれかの関連エンティティの属性でソートされたエンティティの取得は SAP HANA ではサポートされていません。

例えば、 あなたには、 **Person** と **Address** という 2 つの関連するエンティティがあり、それらは **name** と **street** 属性を持っています。 を選択します。 `Person_Address/Address/street` でソートされた `Person` オブジェクトを取得できません。

## 制限なし & 非常に長い文字列の3つの動作

### 3.1 比較関数

SAP HANA does not support unlimited strings or strings with a specified length greater than 5000 characters when using the equal (`=`) or not equal (`!=`) operators in XPath constraints. しかし、 `contains()`、 `starts-with()`、 および `ends-with()` を含む関数をサポートしています。

[大文字と小文字を区別するデータベースの動作](case-sensitive-database-behavior) も参照してください。

{{% alert type="warning" %}}
Mendix が 8.11.0 以下のバージョンでは、SAP HANA における文字列比較は大文字小文字を区別しました。
{{% /alert %}}

### 3.2 並べ替え, グループ化 & 集計化

ソート、グループ化はできません または、5000文字を超える長さの文字列や文字列に対して `count()` などの集計関数を使用します。 これは、このような長い文字列または無制限の文字列が CLOB データ型で実装されているためです。 文字列属性の長さを減らすか、データグリッドから削除することを検討してください。

### 3.3 DISTINCT属性の選択

5000文字を超える文字列タイプのDISTINCT属性を選択することは、CLOBデータ型でDISTINCTカラムを選択するという既知のSAP HANAの制限により、Mendixではサポートされていません。

## 既知の問題 4

### 4.1 Unicode サポート

現在、 [基本多言語面](https://en.wikipedia.org/wiki/Plane_(Unicode)#Basic_Multilingual_Plane) Unicode 文字のみサポートされています。
