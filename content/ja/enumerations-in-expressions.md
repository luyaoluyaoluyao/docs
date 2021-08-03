---
title: "式内の列挙数"
parent: "表現"
---


列挙型が参照されています <modulename>.<enumerationname>.<enumerationvalue>

"OrderProcessing" モジュールを仮定して、列挙型の "Status" が、"started" と "completed" の 2 つの可能な値で定義されているとします。 変更アクション内の属性の値を "completed" に設定するには、次のコードを使用します。

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

## getCaption

列挙値を取得し、この値のキャプションを返します。 キャプションは翻訳可能な文字列で、この関数の結果は現在の言語に依存します。

### 入力パラメータ

*   列挙値 型: 任意の列挙値

### 出力

現在の言語での列挙値のキャプション。 タイプ: 文字列

```java
getCaption($NewEntity/TestEnum)
```

## getKey

列挙値を取得し、この値のキー(「モデラーの名前」と呼ばれる)を返します。 キーは、列挙値の技術的な名前であり、言語に依存しません。 [列挙値](enumeration-values) も参照してください。

### 入力パラメータ

*   列挙値 型: 任意の列挙値

### 出力

列挙値のキー/名前 型: String

```java
getKey($NewEntity/TestEnum)
```
