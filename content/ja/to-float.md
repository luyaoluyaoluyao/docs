---
title: "フロートする"
parent: "表現"
---


10 進数型の値を Float 型に変換します。

{{% alert type="warning" %}}

この関数は Float 型とともに非推奨となります。 代わりに高精度の小数タイプを使用します。

{{% /alert %}}

## toFloat

指定された小数値をFloat型に変換します。

### 入力パラメータ

*   浮動小数点数に変換する10進数の値。

```java
toFloat(parseDecimal('123.456'))
```

戻り値:

```java
123.456
```
