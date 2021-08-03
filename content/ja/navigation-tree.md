---
title: "ナビゲーションツリー"
parent: "menu-widgets"
menu_order: 3
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/navigation-tree.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}ナビゲーションツリーウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

ナビゲーションツリーには、 [ナビゲーション プロファイル](navigation#profiles) または [メニュー](menu) ドキュメントのメニュー アイテムがツリー形式で表示されます。 これらのアイテムは [メニューソース](#menu-source) によって決定され、 [ナビゲーション](navigation) または [メニュー](menu)で構成されます。

ナビゲーションツリーのメニュー構造は、3 つのレベルを持つことができます。つまり、メニュー アイテムはサブアイテムを持つことができます。 メニュー項目とそのプロパティの詳細については、 [メニュー](menu) を参照してください。

![ナビゲーションツリー](attachments/menu-widgets/navigation-tree.png)

## 2つのプロパティ

ナビゲーションツリーのプロパティの例を以下の画像に示します。

{{% image_container width="250" %}}![ナビゲーションツリーのプロパティ](attachments/menu-widgets/navigation-tree-properties.png)
{{% /image_container %}}

ナビゲーション ツリー プロパティは次のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design)
* [全般](#general)

### 2.1 共通セクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般セクション {#general}

#### 2.3.1 メニュー ソース {#menu-source}

メニュー ウィジェットに表示されているアイテムは **メニュー ソース** によって決定されます。 可能なメニューソースは以下の表に記載されています:

| 値                       | 説明                                                           |
| ----------------------- | ------------------------------------------------------------ |
| プロジェクトナビゲーション *(デフォルト)* | メニュー アイテムは、 [ナビゲーション](navigation) で定義されたプロファイルのいずれかから取得されます。 |
| メニュードキュメント              | メニュー項目は [メニュー](menu) ドキュメントから取得されます。                         |

#### 2.3.2 プロファイル

[メニュー ソース](#menu-source) が **プロジェクト ナビゲーション** に設定されている場合にのみ使用できます。 **Profile** プロパティは、ウィジェットに使用する [ナビゲーション プロファイル](navigation#profiles) を指定します。

デフォルト: *レスポンシブ*

#### 2.3.3 メニュー

[メニュー ソース](#menu-source) が **メニュー ドキュメント** に設定されている場合にのみ使用できます。 **メニュー** プロパティは、ウィジェットに使用される [メニュー](menu) ドキュメントを指定します。

## 3 続きを読む

* [ページ](page)
* [メニューウィジェット](menu-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
