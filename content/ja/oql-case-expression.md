---
title: "OQLケース式"
parent: "oql演算子"
tags:
  - "studio pro"
---

## 1つの説明

`CASE` 式は、他のプログラミング言語の if/else ステートメントと同様の条件式です。 各条件は、ブール値の結果を返す式です。 If the condition's result is true, the value of the `CASE` expression is the result that follows the condition, and the remainder of the `CASE` expression is not processed. 条件の結果が true でない場合は、後続の `WHEN` 節も同じ方法で調べられます。 `WHEN` 条件が true の場合、 `CASE` 式の値は `ELSE` 句の結果です。 `ELSE` 節が省略され、条件が true でない場合、結果は null になります。

## 2つの使い方

`CASE` の式は、2つの方法で使うことができます。

```sql
    CASE input_expression
    When when_expression THEN result_expression [ ...n ]
    ELSE else_result_expression
    END
```

または拡張:

```sql
    CASE
    WhEN boolean_expression THEN result_expression [ ...n ] 
    ELSE else_result_expression
    END
```

## 3つの構文

### 3.1 input_expression

`input_expression` が `when_expression` と比較されます。 If  `input_expression` matches  `when_expression`, the result of the whole `CASE` expression will be `result_expression` given after `THEN`.

### 3.2 when_expression

`when_expression` が `input_expression` と比較されます。 When `input_expression` matches this `when_expression`, the result of the whole `CASE` expression will be `result_expression` given after `THEN`.

### 3.3 boolean_expression

`boolean_expression` はブール値でなければなりません。 この式が true を返す場合、 `CASE` 式全体の結果は `THEN` の後に与えられる `result_expression` になります。

### 3.4 result_expression

`result_expression` は、 `CASE` 式全体の可能な結果です。

### 3.5 else_result_expression

`else_result_expression` は `CASE` 式全体の結果で、 `result_expression` が使用できない場合に使用されます。
