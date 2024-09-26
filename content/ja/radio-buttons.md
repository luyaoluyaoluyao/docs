---
title: "Radio Buttons"
parent: "input-widgets"
menu_order: 50
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/radio-buttons.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

{{% alert type="warning" %}}ラジオボタンウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

**Radio Buttons** are used to display and, optionally, allow the end-user to edit the value of an attribute of [data type](data-types) *Boolean* or *Enumeration*.

ページがエンドユーザーに表示されると、利用可能なすべての値が表示されます。 は、選択された値の隣に塗りつぶされた円と、選択されていない値の隣にある空の円で囲まれます。 別の値を選択すると、現在の値の選択が解除されます。 例:

![](attachments/radio-buttons/radio-buttons-displayed.png)

ラジオボタンは [データ ウィジェット](data-widgets) に配置し、ウィジェットによって取得されたオブジェクトの属性を表示する必要があります。 表示される属性の名前は、角括弧と青色の間のラジオボタンウィジェット内に表示されます。

例えば、次の画像には2つのラジオボタンが含まれています。  最初のものはエンドユーザーが見、設定することを可能にします。 この人 (**PreferredContact** ) に連絡するのに好ましい時間を識別する列挙の値。 2 番目は、エンドユーザーが、これが **個人的** コンタクトであるかどうかを示す Boolean を参照および設定することを可能にします。

![](attachments/radio-buttons/radio-buttons.png)

## 2つのプロパティ

以下の画像にラジオボタンのプロパティの例を示します。

{{% image_container width="250" %}}![](attachments/radio-buttons/radio-buttons-properties.png)
{{% /image_container %}}

ラジオボタンのプロパティは以下のセクションで構成されています:

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

#### 2.6.1 向き

このプロパティは、ラジオボタンを **水平** または **垂直** リストとしてレンダリングするかどうかを定義します。

デフォルト: *水平*

### 2.7 ラベルセクション{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.8 検証セクション{#validation}

{{% snippet file="refguide8/widget-validation-link.md" %}}

### 2.9 可視性セクション{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
