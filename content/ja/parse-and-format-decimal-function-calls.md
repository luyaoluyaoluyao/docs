---
title: "小数点関数呼び出しの解析と書式設定"
parent: "表現"
---

すべてのパターンの可能性についての詳細は、 [Class DecimalFormat](http://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html) を参照してください。

## parseDecimal

文字列の値を小数値に変換します。 書式とデフォルト値のオプションパラメータを取得します。

### 入力パラメータ

* 解析する値
    * タイプ: 文字列
* デフォルト値 (省略可能)
    * 種類: decimal or empty

### 出力

入力された文字列値に一致する小数値。 値が解析できない場合 (意味、フォーマットパラメータと一致しないか、不正な文字が含まれています)、デフォルト値が返されます。 デフォルト値が指定されていない場合、エラーが発生します。

* `parseDecimal ('3.45')` は、 3.45 を返します。
* `parseDecimal('noDecimal', 5.05)` returns 5.05
* `parseDecimal('noDecimal', empty)` は空を返す。

## formatDecimal

小数を文字列値に指定された書式に従って変換します。

### 入力パラメータ

* 変換する値
    * 種類: decimal
* Java ライブラリに基づく結果のフォーマット `DecimalFormat` (詳細については、 [Class DecimalFormat](https://docs.oracle.com/javase/8/docs/api/java/text/DecimalFormat.html) を参照してください)
    * タイプ: 文字列
* 結果をフォーマットするロケール（オプション）
   * サポートされている値については、 [forLanguageTag](https://docs.oracle.com/javase/8/docs/api/java/util/Locale.html#forLanguageTag-java.lang.String-) を参照してください。
   * 省略された場合、ユーザーが設定したロケールが使用されます
   * Mendix 7.3からサポート
   * タイプ: 文字列

### 出力

`format` パラメータで指定された形式の小数の文字列表現。

* タイプ: 文字列

```java
formatDecimal(1234.56, '#,###.#')
```

を返します。

```java
'1,234.5' または '1.234,5'
```

```java
formatDecimal(1234.56, '¤ #,##0.00')
```

を返します。

```java
'€ 1.234,50' または '$ 1,234.50'
```

```java
formatDecimal(0.56, '% ##0')
```

戻り値:

```java
'% 56' 
```
