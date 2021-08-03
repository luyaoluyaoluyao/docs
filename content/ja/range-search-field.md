---
title: "範囲検索フィールド"
parent: "検索バー"
---


範囲を含むエンティティを指定すると、範囲が指定された値と重複するすべてのエンティティを検索するために使用されます。

例: 「開始」と「終了」の日付を持つエンティティ「フェスティバル」を与えられ、フェスティバルはX日に開催されますか？

この検索フィールドでサポートされているデータ型は、整数、通貨、小数、日付時間、浮動小数点数、自動番号、長さです。

範囲境界を含めるか、排他するかを、下限と上限の境界演算子を使用して指定できます。

## 共通のプロパティ

{{% snippet file="refguide7/Search+Field+Caption+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Type+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Default+Value+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Custom+Date+Format+Property.md" %}}

{{% snippet file="refguide7/Custom+Date+Format+Tokens.md" %}}

{{% snippet file="refguide7/Search+Field+Placeholder+Property.md" %}}

## 一般プロパティ

### 下側のバウンド

この属性 (path) は範囲の下限を決定します。

### 低バウンド演算子

The lower bound operator determines whether the comparison with the lower bound is inclusive (>=) or not (>). それは 'Greater' または 'Greater or or equal' のいずれかになります。

_デフォルト値_: 大きい。

### 上側のバウンド

この属性 (path) は範囲の上限を決定します。

### 上位バウンド演算子

The upper bound operator determines whether the comparison with the upper bound is inclusive (<=) or not (<). 「Smaller」または「Smaller」または「Smaller」のいずれかです。

_デフォルト値_: 小さく
