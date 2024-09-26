---
title: "ファイルマネージャー"
parent: "file-widgets"
tags:
  - "studio pro"
  - "ファイルマネージャー"
  - "ファイルウィジェット"
  - "ウィジェット"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/file-manager.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}ファイルマネージャウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

ファイルマネージャーはファイルのアップロードやダウンロードに使用されます。

![ファイルマネージャー](attachments/file-widgets/file-manager.png)

エンティティSystem.FileDocument に接続されたデータビューまたはそれらの特殊化内に配置する必要があります。

{{% alert type="info" %}}
ファイルマネージャからファイルをアップロードすると、FileDocument オブジェクトは直ちに反映されます。
{{% /alert %}}

## 2つのプロパティ

以下の画像にファイルマネージャのプロパティの例を示します。

{{% image_container width="250" %}}![ファイルマネージャーのプロパティ](attachments/file-widgets/file-manager-properties.png)
{{% /image_container %}}

ファイルマネージャのプロパティは以下のセクションで構成されています:

* [一般的な](#common)

* [デザインプロパティ](#design-properties)

* [編集可能](#editability)

* [全般](#general)

* [ラベル](#label)

* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 編集可能セクション {#editability}

{{% snippet file="refguide8/editability-section-link.md" %}}

### 2.4 一般セクション {#general}

#### 2.4.1 Type

**Type** プロパティは、エンドユーザーがどのようにファイルマネージャを使用できるかを示します。

| 値              | 説明                                       |
| -------------- | ---------------------------------------- |
| アップロード         | ファイルマネージャは、ファイルのアップロードにのみ使用できます。         |
| ダウンロード         | ファイルマネージャは、ファイルのダウンロードにのみ使用できます。         |
| 両方とも *(デフォルト)* | ファイルマネージャは、ファイルのアップロードとダウンロードの両方に使用できます。 |

#### 2.4.2 最大ファイル サイズ (MB)

**最大ファイルサイズ (MB)** アップロード可能なファイルの最大サイズを指定します。

デフォルト: *5*

#### 2.4.3 使用可能なエクステンション

ユーザがアップロードできるファイル拡張子を指定できます。 拡張子が指定されていない場合、すべてのファイル拡張子が許可されます。 複数の拡張をセミコロンで区切ってください。例えば、 `txt;doc`

許可されていない拡張子のファイルが選択されている場合。 [システムテキスト](system-texts) **ファイルマネージャ/画像ビューアー** > **エラー: ファイル拡張子** がファイルマネージャの下に表示されます。

#### 2.4.4 ブラウザにファイルを表示

**ブラウザにファイルを表示する** は、ファイルをダウンロードする代わりにブラウザに表示するかどうかを示します。

デフォルト: *False*

### 2.5 ラベルセクション {#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.6 表示セクション {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [ファイルウィジェット](file-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
* [システムテキスト](system-texts)
