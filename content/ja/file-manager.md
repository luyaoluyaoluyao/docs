---
title: "ファイルマネージャー"
parent: "file-widgets"
---


ファイルマネージャーはファイルのアップロードやダウンロードに使用されます。

{{% alert type="info" %}}

![](attachments/pages/file-manager.png)

{{% /alert %}}

エンティティSystem.FileDocument に接続されたデータビューまたはそれらの特殊化内に配置する必要があります。

## 一般プロパティ

### タイプ

このプロパティは、エンドユーザーがファイルマネージャと対話できる方法を示します。

| 値      | 説明                                     |
| ------ | -------------------------------------- |
| アップロード | ファイルマネージャは、ファイルのアップロードにのみ使用できます。       |
| ダウンロード | ファイルマネージャは、ファイルのダウンロードにのみ使用できます。       |
| 両方とも   | ファイルマネージャーは、アップロードやファイルのダウンロードに使用できます。 |

_デフォルト値:_ 両方

### 最大ファイルサイズ (MB)

このプロパティは、アップロード可能なファイルの最大サイズ(メガバイト単位)を決定します。

_デフォルト値:_ 5

### 許可されるエクステンション

アップロードできるファイル拡張子を指定できます。 拡張子が指定されていない場合は、すべてのファイル拡張子が許可されます。 複数の拡張をセミコロンで区切ってください。例えば、 `txt;doc`

許可されていない拡張子のファイルが選択されている場合。 システムテキスト (ファイルマネージャー > ファイル拡張子が正しくありません) がファイルマネージャの下に表示されます。

### ブラウザにファイルを表示

このプロパティは、ファイルをダウンロードするのではなく、ブラウザに表示するかどうかを示します。

_デフォルト値:_ False

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
