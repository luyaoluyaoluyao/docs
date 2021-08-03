---
title: "チェックボックス"
parent: "input-widgets"
menu_order: 40
tags:
  - "studio pro"
---

## 1つの紹介

A **check box** is used to display and, optionally, allow the end-user to edit the value of an attribute of [data type](data-types) *Boolean*. 値が true の場合はチェックマークを表示し、false の場合は空のままにします。

{{% alert type="info" %}}ネイティブ モバイル アプリケーションでは、チェック ボックス ウィジェットは toggle.{{% /alert %}} としてレンダリングされます。

チェック ボックスは [データ ウィジェット](data-widgets) に配置し、ウィジェットによって取得されたオブジェクトの属性を表示する必要があります。 表示される属性の名前は、チェック ボックス ウィジェット内に、角括弧と青色の間で表示されます。

たとえば、このチェックボックスをオンにすると、誰かがニュースレターを購読しているかどうかを確認し、設定することができます。

![](attachments/check-box/check-box.png)

## 2つのプロパティ

以下の画像には、チェック ボックス プロパティの例が示されています。

{{% image_container width="250" %}}![](attachments/check-box/check-box-properties.png)
{{% /image_container %}}

チェック ボックスのプロパティは、次のセクションで構成されています。

* [一般的な](#common)
* [データソース](#data-source)
* [デザインプロパティ](#design-properties)
* [編集可能](#editability)
* [イベント](#events)
* [ラベル](#label)
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

### 2.6 ラベルセクション{#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.7 可視性セクション{#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
