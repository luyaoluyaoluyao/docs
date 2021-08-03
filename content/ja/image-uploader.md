---
title: "画像アップローダー"
parent: "file-widgets"
---


画像アップローダーは、サーバーに画像をアップロードするために使用されます。 また、アップロードされた画像のサムネイルも生成します。 アップロードされた画像またはサムネイルは、画像ビューアを使用して表示できます。

{{% alert type="info" %}}

![](attachments/pages/image-uploader.png) イメージアップローダーはここにネストされたデータビューに配置されます。 プロファイルエンティティは、System.Imageの専門分野です。

{{% /alert %}}

画像アップローダーは、エンティティSystem.Imageまたはそれらの特殊化に接続されたデータビューに配置する必要があります。

## 一般プロパティ

### 最大ファイルサイズ (MB)

このプロパティでは、アップロード可能な画像の最大ファイル サイズ (メガバイト単位) を指定できます。

_デフォルト値:_ 5

### 許可されるエクステンション

アップロードできるファイル拡張子を指定できます。 拡張子が指定されていない場合は、すべてのファイル拡張子が許可されます。 複数の拡張子をセミコロンで区切ってください。例えば、 `png;jpg`

許可されていない拡張子のファイルが選択されている場合。 システムテキスト (ファイルマネージャー > ファイル拡張子が正しくありません) がファイルマネージャの下に表示されます。

### サムネイルの幅

このプロパティは、生成されたサムネイルの幅をピクセル単位で決定します。 ただし、サムネイル生成時の画像のアスペクト比は変わりません。

### サムネイルの高さ

このプロパティは、生成されたサムネイルの高さをピクセル単位で決定します。 ただし、サムネイル生成時の画像のアスペクト比は変わりません。

{{% snippet file="refguide7/Label+Property.md" %}}

## 編集可能なプロパティ

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 関連記事

*   [データビュー](data-view)
*   [エンティティ](エンティティ)
*   [関連](関連)
