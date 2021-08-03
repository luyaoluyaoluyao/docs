---
title: "式の場合"
parent: "表現"
menu_order: 60
tags:
  - "studio pro"
  - "if expression"
  - "表現"
  - "if ステートメント"
  - "表現"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/if-expressions.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

式で条件アクションを定義するために式を使用することができます。 正しい構文は次のとおりです。

if _`<condition>`_ then _`<a value>`_ else _`<other value>`_

## 2つの例

文字列値の変更変数アクティビティの式として以下の文を使用します。

```java
if 7 > 6 then 'correct' else 'incorrect'
```

は、変数の値を `正しい` に設定します。
