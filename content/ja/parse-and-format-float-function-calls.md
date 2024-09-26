---
title: "Parse & Format Float Function Calls"
parent: "表現"
---

{{% alert type="warning" %}}

これらの関数は Float 型とともに非推奨となります。 代わりに高精度の小数タイプと関連する関数を使用します。

{{% /alert %}}

すべてのパターンの可能性については [http://docs.oracle.com/javase/7/docs/api/java/DecimalFormat.html](http://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html) を参照してください。

## parseFloat

文字列の値をFloat値に解析します。 書式とデフォルト値のオプションパラメータを取得します。

### 入力パラメータ

*   value to parse Type: String
*   pattern to match on (任意) Type: String
*   default value (optional) Type: Float

### 出力

入力文字列値に一致する浮動小数点値。 値を解析できない場合 (書式パラメータと一致しないか、不正な文字が含まれている場合)、デフォルト値が返されます。 デフォルト値が指定されていない場合、エラーが発生します。

```java
parseFloat('3.45')
```

戻り値:

```java
3.45
```

のデフォルト値を指定します。

```java
parseFloat('noFloat',5.05)
```

戻り値:

```java
5.05
```

書式パラメータ:

```java
parseFloat('$3.33', '$#.##')
```

戻り値:

```java
3.33
```
## formatFloat

指定された書式に従って、Float値を文字列値に変換します。

### 入力パラメータ

*   変換する値 タイプ: Float
*   format that the result should be in Type: String

### 出力

浮動小数点数の文字列表現。'format' パラメータで指定された形式。 タイプ: 文字列

```java
formatFloat(1234.56, '#,###')
```

戻り値:

```java
'1,234.5'
```
