---
title: "サイドバー切り替えボタン"
parent: "layout-widgets"
---


サイドバーのトグルは、押すと [スクロールコンテナ](scroll-container) のリージョンを表示または消去するボタンです。 これにより、サイドバーを作成することができます。 例えば、デフォルトで非表示になっている携帯電話のメニューは、ボタンをクリックすることで表示できます。 サイドバー切り替えを使用したレイアウト例については、画像を参照してください。

![](attachments/pages/sidebar-toggle-button.png)

## ボタンのプロパティ

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Render+Mode+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 一般プロパティ

### 地域

このボタンをクリックして折りたたみ/展開する領域を選択します。

| 地域 | 効果                       |
| -- | ------------------------ |
| 左  | レイアウトコンテナの左側の領域が切り替わります。 |
| 右  | レイアウトコンテナの右側の領域が切り替わります。 |

{{% alert type="info" %}}

サイドバーの切り替えは右から左への切り替え(RTL)で、RTL言語で「Left」を選択するとサイドバーが右からスライドすることを意味します。

{{% /alert %}}

_デフォルト値:_ 左

### モード

リージョンの切り替え方法を指定します。

| モード            | 効果                                                      |
| -------------- | ------------------------------------------------------- |
| コンテンツを脇にプッシュする | サイドバーは、コンテンツの残りの部分を画面オフに移動します(Mendix 5.17以降でのみ使用可能モード)。 |
| 内容の上にスライド      | サイドバーはコンテンツの上に移動します。                                    |
| コンテンツを縮小する     | コンテンツが縮小してサイドバーのスペースを確保します。                             |

### 最初に開く

モードが「コンテンツを縮小」の場合にのみ適用されます。

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Extended.md" %}}
