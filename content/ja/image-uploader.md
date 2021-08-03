---
title: "画像アップロード"
parent: "file-widgets"
tags:
  - "studio pro"
  - "画像アップローダー"
  - "ファイルウィジェット"
  - "ウィジェット"
---

{{% alert type="warning" %}}画像アップローダーウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

画像アップローダーは、サーバーに画像をアップロードするために使用されます。 また、アップロードされた画像のサムネイルも生成します。 アップロードされた画像またはサムネイルは、画像ビューアで表示できます。 エンティティシステムに接続されたデータビューの中に配置する必要があります。

以下の例では、イメージアップローダーがネストされたデータビューに配置されます ( *プロファイル* エンティティは System.Imageの専門化です):

![画像アップロード](attachments/file-widgets/image-uploader.png)

## 2つのプロパティ

以下の画像では、画像アップローダーのプロパティの例を示します。

{{% image_container width="250" %}}![画像アップローダーのプロパティ](attachments/file-widgets/image-uploader-properties.png)
{{% /image_container %}}

画像アップローダーのプロパティは以下のセクションで構成されています:

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

#### 2.4.1 最大ファイルサイズ (MB)

**最大ファイルサイズ (MB)** アップロード可能なファイルの最大サイズを指定します。

デフォルト: *5*

#### 2.4.2 許可されたエクステンション {#allowed-extensions}

ユーザがアップロードできるファイル拡張子を指定できます。 拡張子が指定されていない場合、すべてのファイル拡張子が許可されます。 複数の拡張をセミコロンで区切ってください (例: `txt;doc`)。

許可されていない拡張子のファイルが選択されている場合。 [システムテキスト](system-texts) **ファイルマネージャ/画像ビューアー** > **エラー: ファイル拡張子** がファイルマネージャの下に表示されます。

#### 2.4.3 サムネイル幅

**サムネイルの幅** はピクセル単位で生成されるサムネイルの幅を決定します。 ただし、サムネイル生成時の画像のアスペクト比は変わりません。

#### 2.4.4 サムネイル高さ

**サムネイルの高さ** はピクセル単位で生成されたサムネイルの高さを決定します。 ただし、サムネイル生成時の画像のアスペクト比は変わりません。

### 2.5 ラベルセクション {#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.6 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [ファイルウィジェット](file-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
