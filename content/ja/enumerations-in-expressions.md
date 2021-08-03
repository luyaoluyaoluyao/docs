---
title: "式内の列挙数"
parent: "表現"
menu_order: 170
tags:
  - "studio pro"
  - "表現"
  - "列挙型"
  - "表現"
---

## 1つの紹介

列挙は `<modulename>.<enumerationname>.<enumerationvalue>` によって参照されます。

For example, you have a module called *OrderProcessing*, in which an enumeration *Status* is defined with two possible values: *started* and *completed*.

変更リスト、オブジェクト、または可変アクティビティの属性の値を *完了*に設定するには、次の入力を使用します。

```java
OrderProcessing.Status.completed
```

条件文も可能です:

```java
if 4>3 then
  OrderProcessing.Status.completed
else
  OrderProcessing.Status.completed
```

## 2 getCaption

`getCaption` 関数は列挙値を取り、この値のキャプションを返します。 *キャプション* は翻訳可能な文字列で、この関数の結果は現在の言語に依存します。

### 2.1 入力パラメータ

入力パラメータとして、任意の列挙の列挙値を使用できます。

### 2.2 出力

出力は以下の表に記載されています:

| 値                  | タイプ |
| ------------------ | --- |
| 現在の言語での列挙値のキャプション。 | 文字列 |

### 2.3 例

次の入力を使用する場合:

```java
getCaption($Customer/dule)
```

出力は以下のようになります:

```java
Gouden
```

## 3 getKey

`getKey` 関数は、列挙値を取得し、この値のキー (Studio Pro で *Name* と呼ばれる) を返します。 キーは、列挙値の技術的な名前であり、言語に依存しません。 詳細については、 [列挙数](enumerations) を参照してください。

### 3.1 入力パラメータ

入力パラメータとして、任意の列挙の列挙値を使用できます。

### 3.2 出力

出力は以下の表に記載されています:

| 値                 | タイプ |
| ----------------- | --- |
| 現在の言語の列挙値のキー(名前)。 | 文字列 |

### 3.3 例

次の入力を使用する場合:

```java
getKey($Customer/dule)
```

出力は以下のようになります:

```java
Golden
```

## 4 続きを読む

* [列挙型](enumerations)