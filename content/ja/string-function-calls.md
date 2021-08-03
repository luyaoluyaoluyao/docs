---
title: "文字列関数コール"
parent: "表現"
description: "Mendix で文字列の変換と検査のための関数を説明します。"
---

## 1つの紹介

これらは [文字列](data-types)を変換して検査する関数です。 これらの関数は文字列自体を変更することはなく、新しい値を返すだけであることに注意してください。

文字列は引用符で囲まれています。 文字列に引用符が含まれている場合は、別の引用符でエスケープする必要があります。 例: `'これは面白くない'`.

## 2 toLowerCase

文字列内のすべての文字を小文字に変換します。

### 2.1 入力パラメータ

* 変換する文字列
* タイプ: 文字列

### 2.2 出力

同じ文字列、すべての小文字のみ。

```java
toLowerCase('thisISmyString')
```

戻り値:

```java
'thisismystring'
```

## 3 toUpperCase

文字列内のすべての文字を大文字に変換します。

### 3.1 入力パラメータ

* 変換する文字列
* タイプ: 文字列

### 3.2 出力

同じ文字列、すべての大文字のみ。

```java
toUpperCase('thisISmyString')
```

戻り値:

```java
'THISISMYSTRING'
```

## 4つの長さ

文字列の長さを決定します。

### 4.1 入力パラメータ

* 文字列
* タイプ: 文字列

### 4.2 出力

* 文字列の長さ
* タイプ: integer

```java
length('thisismystring')
```

戻り値:

```java
14
```

## 5つの部分文字列

文字列の部分文字列を取得します。 Note that the first character of a string is located at position `'0'`, and the last character is located at position `length(string)-1`.

### 5.1 入力パラメータ

* 件名
   * タイプ: 文字列
* 部分文字列の開始位置
   * タイプ: integer
* 結果の望ましい長さ（オプション）
   * タイプ: integer

### 5.2 出力

元の文字列の一部で、希望する長さに等しい長さで開始位置から始まります。 開始位置から始まり、文字列の終わりまでの部分文字列を返します。

* タイプ: 文字列

```java
substring('thisismystring', 6)
```

戻り値:

```java
'mystring'
```

3番目のパラメータが与えられた場合、返される文字数は次のように制限されます:

```java
substring('thisismystring', 6, 2)
```

戻り値:

```java
「私の」
```

この3番目のパラメータが大きすぎると、関数は範囲外というエラーをスローしますので、制限するようにしてください。 これは、length 関数の使用例です。

```java
'substring('thisismystring', 0, min(length('thisismystring') - 1, 20)'
```

## 6件検索

文字列内の部分文字列の最初の発生位置を検索します。

### 6.1 入力パラメータ

* 元の文字列、検索したい文字列
    * タイプ: 文字列
* 検索したい部分文字列
    * タイプ: 文字列
* 検索を開始する場所（オプション）
    * タイプ: integer

### 6.2 出力

元の文字列の部分文字列の最初の位置。 部分文字列が元の文字列の中で全く発生しない場合、 `'-1'` を返します。

* タイプ: integer

```java
find('thisismystring', 'my')
```

戻り値:

```java
6
```

元の文字列にはない部分文字列:

```java
find('thisismystring', 'yourstring')
```

戻り値:

```java
-1
```

3番目のパラメータを指定します。

```java
find('thisismystring', 'i', 5)
```

戻り値:

```java
11
```

## 7 findLast

元の文字列中の部分文字列の最後に現れた位置を検索します。

### 7.1 入力パラメータ

* 元の文字列、検索したい文字列
    * タイプ: 文字列
* 検索したい部分文字列
    * タイプ: 文字列
* 検索される最後の場所 (オプション)
    * タイプ: integer

### 7.2 出力

元の文字列の部分文字列の最初の位置。 部分文字列が元の文字列の中で全く発生しない場合、 `'-1'` を返します。

* タイプ: 整数

```java
findLast('thisismystring', 't')
```

戻り値:

```java
9
```

元の文字列にはない部分文字列:

```java
findLast('thisismystring', 'yourstring')
```

戻り値:

```java
-1
```

3番目のパラメータを指定します。

```java
findLast('thisismystring', 'i', 5)
```

戻り値:

```java
4
```

## 8つに含まれています

元の文字列 (最初のパラメータ) に部分文字列 (2番目のパラメータ) が含まれるかどうかを指定します。

この式:

```java
contains('stringtosearchin', 'stringtosearchfor')
```

は、次の式と同じです。

```java
find('stringtosearchin', 'stringtosearchfor') != -1
```

空の変数または空の文字列を検索しています。 `$param = ''`:

```java
contains('stringtosearchin', $param)
```

真実を返します。

{{% alert type="warning" %}}
この関数は、case-senstiveです。
{{% /alert %}}

### 8.1 入力パラメータ

* 元の文字列、検索したい文字列
    * タイプ: 文字列
* 検索したい部分文字列
    * タイプ: 文字列

### 8.2 出力

元の文字列に部分文字列が含まれているかどうか。

* Type: Boolean

```java
contains('thisismystring', 'my')
```

戻り値:

```java
true
```

## 9 startsWith

文字列が指定された部分文字列で始まるかどうかを決定します。

### 9.1 入力パラメータ

* 元の文字列、検索したい文字列
    * タイプ: 文字列
* 検索したい部分文字列
    * タイプ: 文字列

### 9.2 出力

元の文字列が部分文字列で始まるかどうか。

* Type: Boolean

```java
startsWith('thisismystring', 'this')
```

戻り値:

```java
true
```

## 10 endsWith

文字列が指定された部分文字列で終わるかどうかを指定します。

### 10.1 入力パラメータ

* 元の文字列、検索したい文字列
    * タイプ: 文字列
* 検索したい部分文字列
    * タイプ: 文字列

### 10.2 出力

元の文字列が部分文字列で終わるかどうか。

* Type: Boolean

```java
endsWith('thisismystring', 'ring')
```

戻り値:

```java
true
```

## 11 trim

文字列の先頭と末尾の空白をすべて削除します。

### 11.1 入力パラメータ

* 文字列
* タイプ: 文字列

### 11.2 出力

同じ文字列ですが、先頭と末尾にスペースがありません。

* タイプ: 文字列

```java
trim(' this is my string ')
```

戻り値:

```java
「これは私の糸です」
```

## 12 isMatch

文字列が与えられた正規表現に一致するかどうかを確認します。

### 12.1 入力パラメータ

* 試してみて一致する文字列
    * タイプ: 文字列
* 一致する正規表現
    * タイプ: 文字列

{{% alert type="warning" %}}

この関数呼び出しは、現在のプラットフォームが提供する正規表現言語を使用していることに注意してください:

* [microflow](microflow) 内で使用する場合 – Java の正規表現 (詳細については、 [Class Pattern documentation](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html) を参照してください)
* [条件付き書式設定](conditions) – JavaScript の正規表現 (詳細については、 [正規表現 ドキュメント](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) を参照してください)

{{% /alert %}}

### 12.2 出力

文字列が一致するかどうか。

* Type: Boolean

この例では、文字列に数字のみが含まれているかどうかをテストします

```java
isMatch('234hello6432', '^([0-9]+)$')
```

戻り値:

```java
False
```

`isMatch()`では、regex は `^` と `$` に暗黙的にアンカーされます。

例:

* `isMatch('NLG 123.45', '[0-9]')` は false を返します
* `isMatch('NLG 123.45', '.*[0-9].*')` は true を返す

NBは空の文字列を検索しています:

* `isMatch('', '.*[0-9].*')` は false を返します

## 13 replaceAll

正規表現のすべての出現を別の文字列に置き換えます。

### 13.1 入力パラメータ

* 検索する文字列
    * タイプ: 文字列
* 一致する正規表現
    * タイプ: 文字列
* 置換値
    * タイプ: 文字列

{{% alert type="warning" %}}

この関数呼び出しは、現在のプラットフォームが提供する正規表現言語を使用していることに注意してください:

* [microflow](microflows) 内で使用する場合 – Java の正規表現 (詳細については、 [Class Pattern](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html) を参照してください)
* [条件付き書式設定](conditions) – JavaScript の正規表現 (詳細については [正規表現](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) を参照)

{{% /alert %}}

### 13.2 出力

元の文字列で、正規表現のすべての出現が置換文字列に置き換えられます。 文字列内で正規表現が発生しない場合、元の式が返されます。

* タイプ: 文字列

```java
replaceAll('this is a string with 75 some number 234 throwed in', '([0-9])', 'NUMBER')
```

戻り値:

```java
'この文字列は NUMBERNUMBERNUMBER いくつかの数値NUMBERNUMBERNUMBERNUMBERNUMBERNUMBER がスローされます'
```

一致しません:

```java
replaceAll('this is a string with no numbers throw in', '([0-9])', 'NUMBER')
```

戻り値:

```java
'これは数字が投げられていない文字列
```

## 14 replaceFirst

正規表現の最初の発生を置換文字列に置き換えます。

### 14.1 パラメータの入力

* 検索する文字列
    * タイプ: 文字列
* 一致する正規表現
    * タイプ: 文字列
* 置換値
    * タイプ: 文字列

{{% alert type="warning" %}}

この関数呼び出しは、現在のプラットフォームが提供する正規表現言語を使用していることに注意してください:

* [microflow](microflow) 内で使用する場合 – Java の正規表現 (詳細については、 [Class Pattern documentation](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html) を参照してください)
* [条件付き書式設定](conditions) – JavaScript の正規表現 (詳細については、 [正規表現 ドキュメント](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) を参照してください)

{{% /alert %}}

### 14.2 出力

元の文字列で、正規表現のすべての出現が置換文字列に置き換えられます。 文字列内で正規表現が発生しない場合、元の式が返されます。

* タイプ: 文字列

```java
replaceFirst('this is a string with 75 some number 234 throwed in', '([0-9])', 'NUMBER')
```

戻り値:

```java
'this is a string with NUMBER5 some number 234 throwed in'
```

## 15 文字列結合 ( + )

`+` 演算子は、2つの文字列または1つの文字列と数を連結するために使用できます。

### 15.1 入力パラメータ

* 最初のパラメータ
    * Type: string, integer/long, float, decimal
* 2番目のパラメータ
    * Type: string, integer/long, float, decimal

少なくとも一つのパラメータは文字列型でなければなりません。

### 15.2 出力

2つの入力パラメータのリテラル連結である新しい文字列。

* タイプ: 文字列

2 つの文字列を組み合わせるには:

```java
'foo' + 'bar'
```

戻り値:

```java
'foobar'
```

文字列と数値を組み合わせるには:

```java
4.73 + ' km
```

戻り値:

```java
'4.73km
```

## 16 <a name="urlEncode"></a>urlEncode

URL で使用する文字列を変換します。 この関数は、URL の一部として文字列を使用する場合に便利です。

例:

```java
'http://google.com/search?q=' + urlEncode($myQuery)
```

### 16.1 入力パラメータ

* 変換する文字列
* タイプ: 文字列

### 16.2 出力

文字列、URLエンコード。

```java
urlEncode('Hello, world!')
```

戻り値:

```java
'Hello%2C+world%21'
```

## 17 urlDecode

URL から文字列を変換します。 [urlEncode](#urlEncode) の反対。

### 17.1 入力パラメータ

* 変換する URL エンコードされた文字列
* タイプ: 文字列

### 17.2 出力

文字列、URLデコード。

```java
urlDecode('Hello%2C+world%21')
```

戻り値:

```java
'Hello, world!'
```
