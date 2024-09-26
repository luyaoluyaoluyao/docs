---
title: "シーケンスフロー"
parent: "application-logic"
menu_order: 30
tags:
  - "studio pro"
  - "シーケンス フロー"
  - "マイクロフロー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/sequence-flow.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

シーケンスフローは、要素(イベント、アクティビティ、決定など)を相互にリンクする矢印を表示するフローです。 ここで、実行の順序を定義します。 フローは常に一方向に流れ、要素が次々に続く。 決定は常に一方向につながるので、複数のフローを同時に行うことはできません。

リンクしたい2つのアクティビティがある場合は、シーケンスフローが使用されます。

![](attachments/sequence-flow/sequence-flow.png)

## 2 条件値

**条件** の値は、 [決定](decision) または [オブジェクト タイプ 決定](object-type-decision) の結果に基づいて、どの方向に従うべきかを記述します。