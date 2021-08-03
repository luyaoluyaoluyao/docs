---
title: "シンプルなメニューバー"
parent: "menu-widgets"
---


シンプルなメニューバーウィジェットには、画像とキャプション付きの水平または垂直方向のバーの形で設定されたメニューが表示されます。 アイテムはサブアイテムを持つことはできません。メニュー構造は1つのレベルしか持つことができません。 [メニュー アイテム](menu-item) は、アイテムがクリックされたときに開かれたり開始されたりするページまたはマイクロフローを指しています。

{{% alert type="info" %}}

![](attachments/pages/simple-menu-bar-horizontal.png)

{{% /alert %}}{{% alert type="info" %}}

![](attachments/pages/simple-menu-bar-vertical.png)

{{% /alert %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 一般プロパティ

{{% snippet file="refguide7/Menu+Source+Properties.md" %}}

### 方向

このプロパティは、単純なメニュー バーのレイアウト方法を決定します。

| 方向   | 説明                                |
| ---- | --------------------------------- |
| 水平方向 | メニュー項目は隣接しており、画像はキャプションの上にあります。   |
| 垂直方向 | メニュー項目はお互いの下にあり、画像はキャプションの横にあります。 |

_デフォルト値:_ 水平方向
