---
title: "画像ビューアー"
parent: "file-widgets"
---


画像ビューアは、画像やサムネイルを表示するために使用できます。

{{% alert type="info" %}}

![](attachments/pages/image-viewer.png) この画像ビューアは製品画像を表示します。

{{% /alert %}}

イメージ ビューアーはデータ ビューまたはテンプレート グリッドに配置する必要があります。

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## データソースのプロパティ

### エンティティ (パス)

エンティティ (path) プロパティは、イメージ ビューアに表示されるエンティティを指定します。 これは、データビューエンティティから始まり、System.Imageまたはそれの専門化で終了する必要があります。 データビューエンティティ自体がSystem.Imageの(専門化された)場合、このエンティティをイメージビューア上でも使用できます。

## イベント

### クリック時

このプロパティは、画像をクリックしたときに何が起こるかを指定します:

| 値     | 意味                  |
| ----- | ------------------- |
| 何もしない | 何も起こらない。            |
| 僅用於中文 | 指定したマイクロフローが実行されます。 |
| 拡大    | 画像はフルサイズで表示されます。    |

_デフォルト値:_ 何もしない

### マイクロフロー (「コールマイクロフロー」の場合)

このプロパティは、画像をクリックしたときに実行されるマイクロフローを指定します。

### マイクロフローの設定（場合は「マイクロフローの呼び出し」）

クリック設定では、マイクロフローに渡すパラメータを指定します。進捗バーを表示するかどうか、その他。

[マイクロフローの開始](starting-microflows) を参照してください。

## 一般プロパティ

### デフォルトの画像

これは画像がアップロードされない場合に表示される画像です。

{{% snippet file="refguide7/Image+Width+Unit.md" %}}

_デフォルト値_: 割合

{{% snippet file="refguide7/Image+Width.md" %}}

_デフォルト値_: 100

{{% snippet file="refguide7/Image+Height+Unit.md" %}}

_デフォルト値_: 自動

{{% snippet file="refguide7/Image+Height.md" %}}

_デフォルト値_: 該当しない

{{% snippet file="refguide7/Image+Responsive.md" %}}

### 表示

このプロパティは、生成されたサムネイルが表示されているか、画像全体が表示されているかを示します。

_デフォルト値:_ サムネイル画像

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 関連記事

*   [データビュー](data-view)
*   [エンティティ](エンティティ)
