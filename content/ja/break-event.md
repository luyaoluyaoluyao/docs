---
title: "休憩イベント"
parent: "イベント"
menu_order: 5
tags:
  - "studio pro"
  - "休憩イベント"
  - "イベント"
  - "ループ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/break-event.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

{{% alert type="warning" %}}
ブレークイベントは、 [ループ](loop)内でのみ使用できます。
{{% /alert %}}

break イベントは、オブジェクトのリストの反復処理を停止し、残りのフローを続行するために使用されます。 break イベントがなければ、ループは次のオブジェクトの反復を続けます。

たとえば、未払いの注文行をユーザーに通知したい場合は、break イベントを使用できます。 まず、注文に関連付けられている *OrderLine* エンティティのすべてのオブジェクトを取得します。 各注文行が支払われているかどうかを確認します。 注文ラインが支払われている場合、マイクロフローは次の注文ラインに続きます。 ただし、未払いの注文行が見つかった場合、ユーザーに通知され、ループが停止します。 マイクロフローはループから壊れて残りのマイクロフローを継続します 未払いの注文行を見つけたら、注文行の残りの部分を繰り返し続ける必要はありません。

![ブレークイベントの例](attachments/events/break-event-example.png)

## 2 続きを読む

* [ループ](ループ)
* [イベントを続ける](continue-event)