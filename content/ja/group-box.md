---
title: "グループボックス"
parent: "container-widgets"
menu_order: 30
tags:
  - "studio pro"
  - "グループボックス"
  - "コンテナウィジェット"
  - "ウィジェット"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/group-box.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}グループボックスウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

グループ ボックスを使用して、関連ウィジェットを視覚的にグループ化できます。 グループボックスは、ネストされたウィジェットの周りのフレームとして任意のヘッダーで表示されます。 グループボックスは、動的に折りたたんだり展開したりするように構成できます。

![](attachments/container-widgets/group-box.jpg)

## 2つのプロパティ

グループ ボックス プロパティの例を以下の画像に示します。

{{% image_container width="300" %}}![グループボックスのプロパティ](attachments/container-widgets/group-box-properties.png)
{{% /image_container %}}

グループ ボックス プロパティは、次のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般セクション {#general}

#### 2.3.1 ヘッダーの表示

**ヘッダの表示** は、ヘッダがグループボックスの上に表示されるかどうかを定義します。

デフォルト: *True*

#### 2.3.2 図表番号

このプロパティは、 **ヘッダーの表示** オプションが有効な場合にのみ表示されます。 ヘッダーに表示されるキャプションを定義します。

デフォルト: *グループボックス*

#### 2.3.3 折りたたみ可能

このプロパティは、ヘッダーをクリックすることでグループボックスを折りたたむことができるかどうかを指定します。 このプロパティは、 **Show Header** が有効な場合にのみ表示されます。

このプロパティの可能な値は次のとおりです。

* **はい (展開開始)**  *(デフォルト)* - グループボックス内の要素は最初に表示され、ユーザーがヘッダーのマイナスアイコンをクリックすると折りたたむことができます
* **はい (折りたたみ開始)** - ユーザーがヘッダーのプラスアイコンをクリックすると、グループボックス内の要素は最初に非表示になり、拡張することができます
* **いいえ** - グループボックス要素は常に表示され、グループボックスを折りたたむことはできません

### 2.4 表示セクション {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [コンテナウィジェット](container-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)


