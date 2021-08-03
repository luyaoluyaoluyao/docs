---
title: "文字列へ"
parent: "表現"
---


様々なデータ型の値を文字列に変換するための基本関数です。

## toString

指定した値を文字列表現に変換します。

出力フォーマットを完全に制御する必要がある場合は、データ型固有のフォーマット関数を使用することを検討してください。 例えば、10 進数の場合、 [formatDecimal](parse-and-format-decimal-function-calls) を使用します。

### 入力パラメータ

文字列に変換する値。 サポートされている [types](data-types): Integer/Long, Decimal, Float (deprecated), DateTime, and Enumeration 列挙型の場合は、キャプションではなく列挙値のキーを返します。 See also [式](enumerations-in-expressions) の列挙.

```java
toString(1.4)
```

戻り値:

```java
'1.4'
```

日付時間:

```java
toString(dateTime(2007))
```

戻り値:

```java
'Mon Jan 01 00:00:00 CET 2007'
```
