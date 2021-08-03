---
title: "OQLケース式"
parent: "oql演算子"
---


CASE 式は、他のプログラミング言語の if/else ステートメントと同様の条件式です。 各条件は、ブール値の結果を返す式です。 条件の結果が true の場合、CASE式の値は条件に従う結果になります。 そして、CASE 式の残りの部分は処理されません。 条件の結果が true でない場合、後続の WHEN 句はすべて同じ方法で調べられます。 WHEN条件が真でない場合、CASE式の値はELSE節の結果です。 ELSE 句が省略され、条件が true でない場合、結果は null になります。

CASE式は2つの方法で使用できます:

_単純な_

```
CASE input_expression
When when_expression THEN result_expression [ ...n ]
ELSE else_result_expression
END
```

_拡張_

```
CASE
WhEN boolean_expression THEN result_expression [ ...n ] 
ELSE else_result_expression
END
```

**input_expression** when_expression と比較される式。 input_expression が when_expression に一致する場合、CASE式全体の結果は THEN の後に与えられた result_expression になります。

**when_expression** input_expression と比較される式。 input_expression が when_expression に一致する場合、CASE式全体の結果は THEN の後に与えられた result_expression になります。

**boolean_expression** 結果がブール値でなければならない式。 この式が true を返した場合、CASE式全体の結果は THEN の後に与えられた result_expression になります。

**result_expression** CASE式全体の可能な結果。

**else_result_expression** result_expression がどれも実行できない場合、CASE式全体の結果は else_result_expression になります。
