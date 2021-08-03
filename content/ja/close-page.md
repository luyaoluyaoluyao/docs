---
title: "ページを閉じる"
parent: "client-activities"
menu_order: 10
tags:
  - "studio pro"
  - "ページを閉じる"
  - "クライアントのアクティビティ"
aliases:
  - /ja/refguide/Close+Form.html
  - /ja/refguide/close-form.html
---

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** と **Nanoflows** の両方で使用できます。
{{% /alert %}}

{{% alert type="warning" %}}
このアクションは無視され、オフライン、ネイティブ、またはハイブリッド・アプリケーションからマイクロフローが呼び出されたときには機能しません。 詳細については、 [オフライン-First Reference Guide](offline-first#microflows) の *Microflow* セクションを参照してください。
{{% /alert %}}

## 1つの紹介

**ページを閉じる** アクティビティは、現在開いているページを閉じます。 たとえば、ポップアップページを閉じるために使用できます。

{{% image_container width="200" %}}
![](attachments/client-activities/close-page.png)
{{% /image_container %}}

## 2つのプロパティ

**ページ** のアクティビティ プロパティは以下のセクションで構成されています:

* [アクション](#action)

* [一般的な](#common)

![ページプロパティを閉じる](attachments/client-activities/close-page-properties.png)

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

### 3.1 ページ数

{{% alert type="info" %}}
このオプションはネイティブモバイルでのみ利用可能で、Mendix Studio Pro v8.14 で導入されました。
{{% /alert %}}

このプロパティでは、閉じるページ数を制御できます。

| 値        | 説明                                                               |
| -------- | ---------------------------------------------------------------- |
| Single   | 1 ページを閉じる (デフォルトの動作)                                             |
| Multiple | 現在のスタック内の複数のページを一度に閉じると、1つのアニメーションのみが表示されます。 この番号は、式を使用して設定できます。 |
| すべて      | スタック内の最初のページを除いて、現在のスタック内のすべてのページを一度に閉じます。1つのアニメーションのみを表示します。    |

## 4つの共通セクション {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 続きを読む

* [ページを表示](show-page)
* [ネイティブナビゲーション](native-navigation)
