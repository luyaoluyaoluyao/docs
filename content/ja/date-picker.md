---
title: "日付の選択"
parent: "input-widgets"
menu_order: 60
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/date-picker.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

A **date picker** is used to display and, optionally, allow the end-user to edit the value of an attribute of [data type](data-types) *Date and Time*. It uses the values set in the **Languages** tab of **Project Settings** to display a correctly localized value to the end-user, using the **Language** object associated with the end-user.

日付ピッカーを [データ ウィジェット](data-widgets) に配置し、ウィジェットによって取得されたオブジェクトの属性を表示する必要があります。 表示される属性の名前は、日付選択、角括弧、および青色の間で表示されます。

例えば、次の日付ピッカーでは、エンドユーザーが顧客の **LastContacted** 日付を表示および設定することができます。

![](attachments/date-picker/date-picker.png)

## 2つのプロパティ

日付ピッカーのプロパティの例を以下の画像に示します。

{{% image_container width="250" %}}![](attachments/date-picker/date-picker-properties.png)
{{% /image_container %}}

日付ピッカーのプロパティは以下のセクションで構成されています:

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

#### 2.6.1 日付フォーマット

日付の形式は、日付の値を日付、時刻、日付と時刻、またはカスタム形式で表示するかを決定します。

ここで選択したフォーマットは、データの保存方法には影響しません。すべての場合、日付と時刻の両方が記録されます。 データの表示方法に影響を与えるだけです。 日付および/または時刻フォーマットは、データを表示するエンドユーザーのローカライズ(言語)によっても異なります。

日付フォーマットの可能な値を以下に示します。

* **Date** *(default)*
* **時刻**
* **日付と時刻**
* **カスタム** (詳細は以下を参照)

#### 2.6.2 カスタム日付フォーマット

日付書式として **Custom** を選択した場合(上記参照)、このプロパティは属性値のフォーマット方法を決定します。 カスタム日付フォーマットは、以下の表で見つかった任意のシンボルを組み合わせることができる文字列です。 句読点は文字通りレンダリングされます。

{{% snippet file="refguide8/custom-date-format-tokens.md" %}}

{{% alert type="info" %}}
Even though a date picker with a custom date format is editable, the calendar drop-down button will only be shown if the custom format represents a full date (that is, the year [`y`-`yyyy`], month [`M`-`MMMM`], and day of month [`d`-`dd`] tokens are all present in the custom format).
{{% /alert %}}

#### 2.6.3 プレースホルダーテキスト

date 属性が空の場合、プレースホルダー テキストが表示されます。 エンドユーザーに期待されるフォーマットについてのヒントを与えるために使用できます。

{{% alert type="warning" %}}
ネイティブの日付ピッカー(つまり、iOSおよびAndroidバージョン4.0以降)が使用可能な場合、プレースホルダテキストは表示されません。
{{% /alert %}}

### 2.7 ラベルセクション{#label}

{{% snippet file="refguide8/label-section-link.md" %}}

### 2.8 検証セクション{#validation}

{{% snippet file="refguide8/widget-validation-link.md" %}}

### 2.9 可視性セクション{#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
