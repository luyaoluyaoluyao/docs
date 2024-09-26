---
title: "ループ"
parent: "application-logic"
menu_order: 80
tags:
  - "studio pro"
  - "ループ"
  - "繰り返します。"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/loop.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

ループはオブジェクトのリストを反復処理するために使用され、フレームとして視覚化されます。 オブジェクトごとに、ループ内のフローが実行されます。 引数と同じように見えるiteratorは、繰り返しごとにリスト内の現在のオブジェクトを表します。 オブジェクトの名前は黒で表示され、オブジェクトのエンティティタイプは青で表示されます。

例えば、 If you have a list of objects of the *OrderLine* entity and you want to set the purchase date for every object 購入日を設定する変更アクティビティを含むループを使用できます。

![](attachments/loop/loop.png)

ループには、開始イベントと終了イベントを除く、マイクロフローで使用されるすべてのタイプの要素を含めることができます。 ループのみが [ブレークイベント](break-event) と [継続イベント](continue-event)を含めることができます。

## 2つの入力プロパティ

### 2.1 上に反復させる

ループするアイテムのリストである変数。

## 3 アクションプロパティ

### 3.1 ループオブジェクト名

**Loop object name** は現在作業中のリスト項目の名前です。 ループ内のフローはリスト内の各オブジェクトに対して実行され、オブジェクトは常にこの名前を持ちます。 For example, if the list over which the loop iterates is of type *List of Order*, the iterator object will be of type *Order*.