---
title: "シンプルなメニューバー"
parent: "menu-widgets"
menu_order: 2
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/simple-menu-bar.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}シンプルなメニューバーウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

単純なメニューバーには、 [ナビゲーション プロファイル](navigation#profiles) または [メニュー](menu) のメニュー項目が、水平または垂直バーの形式で表示されます。 これらのアイテムは [メニューソース](#menu-source) によって決定され、 [ナビゲーション](navigation) または [メニュー](menu)で構成されます。

メニュー項目のサブ項目は、このウィジェットでは表示されません。つまり、メニュー構造は1つのレベルしか持つことができません。 メニュー項目とそのプロパティの詳細については、 [メニュー](menu) を参照してください。

![シンプルなメニューバー](attachments/menu-widgets/simple-menu-bar.png)

## 2つのプロパティ

以下の画像に、単純なメニュー バーのプロパティの例を示します。

{{% image_container width="250" %}}![シンプルなメニューバーのプロパティ](attachments/menu-widgets/simple-menu-bar-properties.png)
{{% /image_container %}}

メニューバーのプロパティは以下のセクションで構成されています:

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

| 値                        | 説明                                                           |
| ------------------------ | ------------------------------------------------------------ |
| プロジェクトナビゲーション  *(デフォルト)* | メニュー アイテムは、 [ナビゲーション](navigation) で定義されたプロファイルのいずれかから取得されます。 |
| メニュードキュメント               | メニュー項目は [メニュー](menu) ドキュメントから取得されます。                         |

#### 2.3.2 プロファイル

[メニュー ソース](#menu-source) が **プロジェクト ナビゲーション** に設定されている場合にのみ使用できます。 **Profile** プロパティは、ウィジェットに [ナビゲーション プロファイル](navigation#profiles) が使用されるものを指定します。

デフォルト: *レスポンシブ*

#### 2.3.3 メニュー

[メニュー ソース](#menu-source) が **メニュー ドキュメント** に設定されている場合にのみ使用できます。 **メニュー** プロパティは、ウィジェットに使用される [メニュー](menu) ドキュメントを指定します。

#### 2.3.4 向き

このプロパティは、単純なメニュー バーのレイアウト方法を決定します。

| 方向         | 説明                                |
| ---------- | --------------------------------- |
| 水平  *(既定)* | メニュー項目は隣接しており、画像はキャプションの上にあります。   |
| 垂直方向       | メニュー項目はお互いの下にあり、画像はキャプションの横にあります。 |

## 3 続きを読む

* [ページ](page)
* [メニューウィジェット](menu-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
