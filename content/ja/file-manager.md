---
title: "ファイルマネージャー"
parent: "file-widgets"
tags:
  - "studio pro"
  - "ファイルマネージャー"
  - "ファイルウィジェット"
  - "ウィジェット"
---

{{% alert type="warning" %}}ファイルマネージャウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

ファイルマネージャーはファイルのアップロードやダウンロードに使用されます。

![ファイルマネージャー](attachments/file-widgets/file-manager.png)

A file manager must be placed inside a data view connected to the entity that is either a **System.FileDocument** (or a specialization) or an [external entity](external-entities) with a `Contents` binary attribute.

{{% alert type="info" %}}
外部エンティティをファイルソースとして使用するには、対応する OData サービス内でメディア要素として定義する必要があります。 このような要素は、メタデータで `HasStream` 属性を `true` に設定することで認識できます。
{{% /alert %}}

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

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 編集可能セクション {#editability}

{{% snippet file="refguide/editability-section-link.md" %}}

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

{{% snippet file="refguide/label-section-link.md" %}}

### 2.6 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [ファイルウィジェット](file-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
* [システムテキスト](system-texts)
