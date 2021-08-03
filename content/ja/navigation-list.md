---
title: "ナビゲーションリスト"
parent: "container-widgets"
menu_order: 70
tags:
  - "studio pro"
  - "ナビゲーションリスト"
  - "コンテナウィジェット"
  - "ウィジェット"
---

{{% alert type="warning" %}}
ナビゲーション リスト ウィジェットは、ネイティブ モバイル ページではサポートされていません。
{{% /alert %}}

## 1つの紹介

ユーザーがこの行をクリックしたときに、ナビゲーションリストを使用してアクションを行全体にアタッチできます。 そのような行はナビゲーションリスト項目と呼ばれます。

たとえば、ある行をクリックするとページを開くことができます。別の行をクリックすると、マイクロフローが実行されます。

![ナビゲーションリスト](attachments/container-widgets/navigation-list.png)

## 2つのプロパティ

ナビゲーションリストのプロパティの例を以下の画像に示します。

{{% image_container width="250" %}}![ナビゲーションリストのプロパティ](attachments/container-widgets/navigation-list-properties.png)
{{% /image_container %}}

ナビゲーション リストのプロパティは、次のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.3 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3つのナビゲーションリストアイテム

ナビゲーションリストの行は、ナビゲーションリストの項目です。 ナビゲーション・リストの各行ごとに **をクリックすると** イベントを個別に設定できます。

### 3.1 ナビゲーションリスト項目プロパティ

#### 3.1.1 共通セクション

{{% snippet file="refguide/common-section-link.md" %}}

#### 3.1.2 一般セクション

**一般** セクションでは、ナビゲーションリストの項目ごとにクリックイベントを特定することができます。 on click イベントは、ユーザーが行をクリックしたときに実行されるアクションを定義します。 クリックイベントの詳細については、 [[イベント & イベント]セクション](on-click-event)を参照してください。

{{% alert type="info" %}}

Microflows set as an on click event for a navigation list item have no **Execution**, **Confirmation**, or **Advanced** microflow settings. マイクロフローを呼び出す方法の詳細については、 [[イベント & イベント]セクション](on-click-event#call-microflow)をクリックしてください。

{{% /alert %}}

#### 3.1.3 表示セクション

{{% snippet file="refguide/visibility-section-link.md" %}}

## 4 続きを読む

* [ページ](page)
* [コンテナウィジェット](container-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)