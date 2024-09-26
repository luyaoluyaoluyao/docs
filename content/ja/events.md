---
title: "イベント"
parent: "application-logic"
menu_order: 90
tags:
  - "studio pro"
  - "イベント"
  - "イベント"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/events.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

イベントは、マイクロフローのフローに円として表示され、通常はフローの終わりまたは始めに配置されます。

{{% image_container width="200" %}}
![](attachments/events/events.png)
{{% /image_container %}}

たとえば、これらはマイクロフローの開始または終了に使用され、ループ内の反復を壊します。 またはイベントの種類に応じてこの反復を続行します。 エラーイベントを除き、すべてのイベントはマイクロフローまたはナノフローの両方で使用できます。

フローに次のイベントを追加できます。

* [開始イベント](start-event) - マイクロフローまたはナノフローの始まりを示します

* [終了イベント](end-event) - フローが停止する場所を定義する

* [Error Event](error-event) - マイクロフローが停止し、エラーを投げる場所を定義する

* [Continue Event](continue-event) - 現在の反復を停止し、次のオブジェクトの反復を開始するためのループで使用

* [Break Event](break-event) - ループを終了し、残りのフローを継続するためのループで使用