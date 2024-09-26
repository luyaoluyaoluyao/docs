---
title: "正規表現"
parent: "リソース"
menu_order: 70
tags:
  - "studio pro"
  - "正規表現"
  - "正規表現"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/regular-expressions.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

正規表現リソースドキュメントは、文字列が一致しなければならない一連の条件を記述するためにエンティティの [検証ルール](validation-rules) で使用されます。

正規表現には以下のプロパティがあります。

## コモン2個

### 2.1 名前

名前は、エンティティの [バリデーションルール](validation-rules) から正規表現を参照するために使用できます。

### 2.2 ドキュメント

これはドキュメントの目的のみに使用されます。モデリングを行っているエンドユーザーアプリケーションには表示されません。

## 3 式{#expression}

この式は、文字列を [形式の国際的に標準化された正規表現言語](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html) でチェックすべき基準を定義しています。

{{% alert type="info" %}}

例えば、オランダの郵便番号をチェックする式は次のようになります: `[1-9][0-9][0-9][0-9] ?[A-Za-z][A-Za-z]`.

以下に2つの郵便番号例を示します: **3072AP** と **7500 AH**.

以下は基準です：

* 最初の文字は1から9の範囲の数字です
* 2 番目、3 番目、4 番目の文字は 0 から 9 の桁数です。
* 最後の2文字は、最後の2つの部分式 [A-Za-z]で表される文字です。 最後の2文字がA-Zまたは範囲a-zであることを示します。
* 数字と文字の間にスペースがあります。スペースと疑問符で構成される部分式で表されるように、スペースがあります。 疑問符は空間がオプションであることを示します

{{% /alert %}}

次のセクションでは、Mendix で使用できる正規表現の概要を示します。 この説明は、 *isMatch()* などの関数で使用される正規表現文字列にも適用されます。

### 3.1 Subexpressions

正規表現は、一連の部分式で構成されます。 文字列のすべての部分が同じ順序でこれらの部分式に一致する場合、文字列は正規表現にマッチします。

正規表現には、次の種類の部分式を含めることができます。

* `[ ]` – 括弧内で示される単一の文字と一致します。例:
    * `[abc]` matches "_a_", "_b_", or "_c_"
    * `[a-z]` は、"_a_" から "_z_ " の小文字に一致する範囲を指定します。

    {{% alert type="info" %}}These forms can be mixed: `[abcx-z]` matches "_a_", "_b_", "_c_", "_x_", "_y_", or "_z_", and is equivalent to `[a-cx-z]`. The `-` character is treated as a literal character if it is the last or the first character within the brackets, or if it is escaped with a backslash (`\`).
    {{% /alert %}}

* `[^ ]` – 括弧内に含まれていない単一の文字に一致します。例えば:
    * `[^abc]` は "a", "b", "c" 以外の任意の文字に一致します
    * `[^a-z]` は "a" から "z" までの小文字でない単一文字に一致します

    {{% alert type="info" %}}上記のように、リテラル文字と範囲を混在させることができます。
    {{% /alert %}}

* `{m,n}` – 先行する要素の少なくとも _m_ に一致し、 _n_ 回以下に一致します。例:

    * `{3,5}` は "_aaa_", "_aaaaaa_", および "_aaaaa_ " のみ一致します。
* `{n}` - 前の要素に正確にn回マッチします。例:

    * `[1-9][0-9]{3} ?[A-Za-z]{2}` is an alternative way to write the expression for checking the Dutch post code in the example above
* `.` – a dot matches any single character; if you want to match a dot, you can escape it by prefixing it with a `\` (backslash)
* A literal character – this is a character that does not have a special meaning in the regular expression language and it matches itself; this is effectively any character except `\[](){}^-$?*+|.`, for example:
    * オランダ語の郵便番号の例の *`スペース`* は文字列で、それ自体に一致するだけです。

    {{% alert type="info" %}}If you need to match one of the characters which is not a literal, prefix it with a backslash (`\`).
    {{% /alert %}}

* `\w` – 単語：文字、数字、またはアンダースコア。 `\w` は `[A-Za-z0-9_]の略語です`
* `\d` - `[0-9]の略語`

### 3.2 クオンティファイア

文字列内でサブ式が発生する回数は、サブ式の後にクオンタイファで示されます。 quantifier が存在しない場合、サブ式は一度だけ発生する必要があります。

以下のクオンタイファイアを使用できます：

| Quantifier | 説明                                 |
| ---------- | ---------------------------------- |
| ?          | 前のサブ式は、起こらない、または一度起こらないでください。      |
| *          | 前のサブ式は、任意の回数で発生します。                |
| +          | 前のサブ式は1回以上でなければなりません。              |
|            | クオンタイファーは、前のサブ式が一度だけ発生することを意味しません。 |

## 4 続きを読む

* [Class Pattern](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html#matches-java.lang.String-java.lang.CharSequence-) – Oracle Java SEドキュメントからの情報
* [Using Regular Expressions in Java](http://www.regular-expressions.info/java.html)  – *Regular-Expressions.info* website
