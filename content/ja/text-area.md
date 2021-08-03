---
title: "テキストエリア"
parent: "input-widgets"
menu_order: 20
tags:
  - "studio pro"
---

## 1つの紹介

A **text area** is used to display and, optionally, allow the end-user to edit the value of an attribute of [data type](data-types) *String*. [テキスト ボックス](text-box) とは異なります。値は複数行にわたって表示できます。

テキスト エリアは、 [データ ウィジェット](data-widgets) に配置し、ウィジェットによって取得されたオブジェクトの属性を表示する必要があります。 表示される属性の名前は、テキスト領域、角括弧、および青色の範囲内に表示されます。

例えば、以下のテキストエリアでは、エンドユーザーがコンタクトについて **ノート** を見、設定することができます。

![](attachments/text-area/text-area.png)

## 2つのプロパティ

以下の画像にテキスト領域のプロパティの例を示します。

{{% image_container width="250" %}}![](attachments/text-area/text-area-properties.png)
{{% /image_container %}}

テキスト エリアのプロパティは、次のセクションで構成されています。

* [一般的な](#common)
* [データソース](#data-source)
* [デザインプロパティ](#design-properties)
* [編集可能](#editability)
* [イベント](#events)
* [全般](#general)
* [ラベル](#label)
* [検証](#validation)
* [公開範囲](#visibility)

### 2.1 共通セクション{#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 データソースセクション{#data-source}

{{% snippet file="refguide/data-source-section-link.md" %}}

### 2.3 デザインプロパティセクション{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 編集可能セクション{#editability}

{{% snippet file="refguide/editability-section-link.md" %}}

### 2.5 イベントセクション{#events}

#### 2.5.1 変更時{#on-change}

on-change プロパティは、ウィジェットを離れたときに実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、値が変更された後に別のウィジェットをクリックします。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.5.2 入口で

on-enter プロパティは、ウィジェットの入力時に実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、マウスでクリックします。

{{% snippet file="refguide/events-section-link.md" %}}

#### 休暇中 2.5.3

on-leave プロパティは、ウィジェットを離れたときに実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、別のウィジェットをクリックします。

これは、値が変更されていない場合でも、イベントが常にトリガーされるという点で [On change](#on-change) プロパティとは異なります。

{{% snippet file="refguide/events-section-link.md" %}}

### 2.6 一般セクション{#general}

#### 2.6.1 自動的に成長する

{{% alert type="info" %}}自動的に grow プロパティは、ネイティブ モバイル ページの動作には影響しません。 iOSでは、テキストエリアは常に自動的に拡大されます
{{% /alert %}}

このプロパティは、テキストの量に応じてテキスト領域が自動的に拡大するかどうかを定義します。

デフォルト: *いいえ*

#### 2.6.2 行数

**行数** は行の高さに基づいてテキスト領域のサイズを決定します。 テキスト領域内のテキストがより多くの行を含んでいる場合、スクロールバーはエンドユーザーがすべてを見ることを可能にします。 このプロパティは、 **** が *いいえ* に設定されている場合にのみ使用されます。

デフォルト: *5*

#### 2.6.3 カウンターメッセージ

{{% alert type="info" %}}Counter message is not supported on native mobile pages.{{% /alert %}}

これは、テキストエリアに入力するときに表示されるテキストです。 このテキストには [パラメータ](text#parameters)が2つあります。 最初のパラメータはすでに入力されている文字数を含み、2番目のパラメータは文字数の最大値を含みます。

For example, if you use the counter message `You've used {1} characters of the {2} characters that are allowed.` for your text area, the end-user will see this message displayed below the text area widget:

![](attachments/text-area/counter-message.png)

#### 2.6.4 メッセージが長すぎます

{{% alert type="info" %}}Text too long message is not supported on native mobile pages.{{% /alert %}}

これは、入力された文字の数が最大文字数よりも大きい場合に表示されるテキストです。

#### 2.6.5 最大長さ

このプロパティは、このテキスト領域で入力できる最大文字数を指定します。

| 値               | 説明                         |
| --------------- | -------------------------- |
| 属性の長さ *(デフォルト)* | 最大文字数は、接続された属性の最大長さと同じです   |
| 無制限です           | 最大文字数に制限はありません             |
| カスタム            | ウィジェットのプロパティで文字数の最大値を指定します |

#### 2.6.6 プレースホルダーテキスト

プレースホルダー テキストは、まだ入力されていない場合、または、表示された属性が空の場合に表示されます。

たとえば、エンドユーザーにどのようなテキストを入力すべきかのヒントを与えるために使用できます。

#### 2.6.7 オートコンプリート

autocomplete プロパティは、テキスト領域を自動補完可能にするかどうかを指定します。 autocomplete 属性により、モバイルデバイスの項目への事前入力機能も向上します。

{{% alert type="info" %}}このオプションはネイティブページでのみ利用できます。{{% /alert %}}
{{% alert type="info" %}}Android でオートコンプリートがオフになっている場合、新しい行のサポートが削除されます。{{% /alert %}}

### 2.7 ラベルセクション{#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.8 検証セクション{#validation}

{{% snippet file="refguide/widget-validation-link.md" %}}

### 2.9 可視性セクション{#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
