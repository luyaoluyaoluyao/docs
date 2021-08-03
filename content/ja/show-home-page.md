---
title: "ホームページを表示"
parent: "client-activities"
menu_order: 30
tags:
  - "studio pro"
  - "ホームページを表示"
  - "ホームページ"
  - "クライアントアクティビティ"
aliases:
  - /ja/refguide/Show+Home+Page.html
---

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** でのみ使用できます。
{{% /alert %}}

{{% alert type="warning" %}}
このアクションは無視され、オフライン、ネイティブ、またはハイブリッド・アプリケーションからマイクロフローが呼び出されたときには機能しません。 詳細については、 [オフライン-First Reference Guide](offline-first#microflows) の *Microflow* セクションを参照してください。
{{% /alert %}}

## 1つの紹介

**Show home page** アクティビティは、エンドユーザーのホームページを開きます。 たとえば、ログインしていないユーザーをホームページに移動させることができます。

{{% image_container width="200" %}}
![ホームページを表示](attachments/client-activities/show-home-page.png)
{{% /image_container %}}

このアクティビティは、ログイン後にエンドユーザーに表示される同じページを表示します。 つまり、現在のユーザーロールに対して定義されているホームページが表示されます。 ロールベースのホームページの詳細については、 [ナビゲーション](navigation) を参照してください。

## 2つのプロパティ

**Show home page** アクティビティ プロパティは以下のセクションで構成されています:

* [アクション](#action)

* [一般的な](#common)

    {{% image_container width="300" %}}
![ホームページのプロパティを表示](attachments/client-activities/show-home-page-properties.png)
{{% /image_container %}}

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

## 4つの共通セクション {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 続きを読む

* [ページを表示](show-page)
* [アクティビティ](アクティビティ)

