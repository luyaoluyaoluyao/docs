---
title: "ドロップダウン"
parent: "input-widgets"
menu_order: 30
tags:
  - "ドロップダウン"
  - "input"
  - "ページ"
  - "ウィジェット"
  - "列挙型"
  - "studio pro"
aliases:
  - /refguide8/drop-down-widget.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/drop-down.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**ドロップダウン** を使用して表示し、オプションで表示します。 **データ型** [列挙](data-types) の属性の値を編集することができます *列挙*。

ドロップダウンは [データ ウィジェット](data-widgets) に配置し、ウィジェットによって取得されたオブジェクトの属性を表示する必要があります。 表示される属性の名前は、ドロップダウン、角括弧、青色の中に表示されます。

{{% alert type="info" %}}
ドロップダウンは、 [リファレンスセレクター](reference-selector)と混同しないでください。これは、別のオブジェクトへの [アソシエーション](associations) を選択するために使用されます。
{{% /alert %}}

たとえば、次のドロップダウンでは、エンドユーザーが顧客が割り当てられている **リージョン** を確認し、設定することができます。 **リージョン** の可能な値は列挙で保持されます。

![](attachments/drop-down/drop-down.png)

## 2つのプロパティ

ドロップダウン プロパティの例を以下の画像に示します。

{{% image_container width="300" %}}![](attachments/drop-down/drop-down-properties.png)
{{% /image_container %}}

ドロップダウンのプロパティは以下のセクションで構成されています:

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

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 データソースセクション{#data-source}

{{% snippet file="refguide8/data-source-section-link.md" %}}

### 2.3 デザインプロパティセクション{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.4 編集可能セクション{#editability}

{{% snippet file="refguide8/editability-section-link.md" %}}

### 2.5 イベントセクション{#events}

#### 2.5.1 変更時{#on-change}

on-change プロパティは、ウィジェットを離れたときに実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、値が変更された後に別のウィジェットをクリックします。

{{% snippet file="refguide8/events-section-link.md" %}}

#### 2.5.2 入口で

on-enter プロパティは、ウィジェットの入力時に実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、マウスでクリックします。

{{% snippet file="refguide8/events-section-link.md" %}}

#### 休暇中 2.5.3

on-leave プロパティは、ウィジェットを離れたときに実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、別のウィジェットをクリックします。

これは、値が変更されていない場合でも、イベントが常にトリガーされるという点で [On change](#on-change) プロパティとは異なります。

{{% snippet file="refguide8/events-section-link.md" %}}

### 2.6 一般セクション{#general}

#### 2.6.1 空のオプションの図表番号

空のオプションキャプションは、エンドユーザーに表示されるドロップダウンで空のオプションに対して表示されるテキストです。 これは翻訳可能なテキストです。 詳細は [言語メニュー](translatable-texts) を参照してください。

空のオプションにキャプションを追加すると、アプリケーションのユーザーエクスペリエンスが向上します。 また、スクリーンリーダーを使用するエンドユーザーがアプリケーションを簡単に操作できるようにします。

For example, the drop-down that allows the end-user to select the region allocated to a customer, where the possible values for **Region** are held in an enumeration, could have the caption `Select a region`.

![](attachments/drop-down/select-a-region.png)

### 2.7 ラベルセクション{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.8 検証セクション{#validation}

{{% snippet file="refguide8/widget-validation-link.md" %}}

### 2.9 可視性セクション{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
