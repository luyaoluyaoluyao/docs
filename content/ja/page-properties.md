---
title: "ページのプロパティ"
parent: "ページ"
menu_order: 10
tags:
  - "studio pro"
  - "ページ"
  - "プロパティ"
---

## 1つの紹介

このドキュメントでは、ページ プロパティについて説明します。 どのページにどのようなウィジェットを配置できるかの詳細については、 [ページ](pages) を参照してください。

## 2つのプロパティ

以下の画像では、ページ プロパティの例を示します。

{{% image_container width="250" %}}![ページのプロパティ](attachments/page/page-properties.png)
{{% /image_container %}}

ページプロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [デザイナー](#designer)
* [全般](#general)
* [Navigation](#navigation)
* [ポップアップ](#pop-up)
* [使用法](#usage)

### 2.1 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 デザイナーセクション {#designer}

{{% snippet file="refguide/designer-properties.md" %}}

### 2.3 一般セクション {#general}

#### 2.3.1 プラットフォーム

**Platform** プロパティの値は以下のとおりです。

* Web *(デフォルト)* – ブラウザまたはハイブリッドモバイルアプリに表示されるページ
* ネイティブ - ネイティブモバイルアプリに表示されるページ

#### 2.3.2 レイアウトタイプ {#layout-type}

**レイアウト タイプ**は、ページの目的と開き方を決定します。

| レイアウトタイプ       | 説明                                                                       |
| -------------- | ------------------------------------------------------------------------ |
| **レスポンシブ**     | あらゆる種類のデバイスで正常に動作するページ。                                                  |
| **タブレット固有の**   | レスポンシブオプションはタブレット上で良いユーザーインターフェイスを提供しないため、タブレットに表示されるページ。                |
| **電話番号指定**     | レスポンシブオプションが電話で良いユーザーインターフェイスを提供しないので、電話に表示されるページ。                       |
| **モーダルポップアップ** | モーダルポップアップウィンドウ [として表示されるページ](https://www.wikiwand.com/en/Modal_window)。 |
| **ポップアップ**     | *モデル* ポップアップウィンドウとして表示されるページ                                             |

#### 2.3.3 レイアウト

このページが基づく [レイアウト](layout)

#### 2.3.4 タイトル {#title}

[ページ タイトル ウィジェット](page-title) を使用して表示されるページのタイトル。 ページがポップアップウィンドウに表示されると、ポップアップのタイトルバーにタイトルが表示されます。

タイトルは上書きすることができます。 For example, the [Create button](control-bar) and the [Edit button](control-bar) of a data grid can refer to the same page, but they override the titles to **New** and **Edit**, respectively.

#### 2.3.6 URL

ページの URL を使用して、直接ページに移動することができます (例えば、外部リンクやブックマークから)。 ページにアクセスすると、ブラウザのアドレスバーに表示されます。 URLが設定されていないページに移動すると、最後に訪問したURLが表示されます。 Note that the full URL of the page will be the base URL of your application followed by `/p` and then by the configured URL of the page (for example, `http://example.mendixcloud.com/p/home_page`).

トップレベルのデータビュー(パラメータ化されたページ)を持つページにはURLもあります。 そのようなページの URL プロパティには、最後に `{Id}` のパスセグメントが含まれている必要があります。 ブラウザーでは、 `{Id}` セグメントはエンティティの実際の識別子に置き換えられます。

簡単な電子商取引アプリケーションでは、次のようにURLを構成できます。

* */orders/* – the URL for a page with a data grid for `Orders` (in a browser, the URL will look like `http://example.mendixcloud.com/p/orders/`)

* */order/{Id}* – the URL for a page with data from a particular `Order` (in a browser, the URL will look like `http://example.mendixcloud.com/p/order/3212449487634321`, wherein `3212449487634321` is the unique identifier of the `Order`)

### 2.4 ナビゲーションセクション {#navigation}

#### 2.4.1 表示

このプロパティは、ページが表示されるモジュールのロールを定義します。 This has an effect on [menu widgets](menu-widgets) and on buttons that are visible only if allowed (for example, an [action button](button-widgets) for editing).

詳細については、 [モジュールセキュリティ](module-security) を参照してください。

### 2.5 ポップアップセクション {#pop-up}

**ポップアップ** セクションはポップアップページにのみ表示されます。 ポップアップページの詳細については、 [Layout Type](#layout-type) セクションを参照してください。

#### 2.5.1 幅 (ピクセル単位)

ポップアップページの幅をピクセル単位で指定します。 0に設定すると、幅が自動的に決まります。

デフォルト: *0 0*

#### 2.5.2 高さ (ピクセル単位)

このプロパティは、ポップアップページの高さをピクセルで指定します。 0に設定すると、高さが自動的に決まります。

デフォルト: *0 0*

#### 2.5.3 Resizable

このプロパティは、エンドユーザーがポップアップのサイズを変更できるかどうかを指定します。

デフォルト: *はい*

#### 2.5.4 アクションを閉じる

ポップアップページを閉じるボタンの動作を設定します。 ポップアップ閉じボタンのデフォルトの動作は、変更をロールバックしてポップアップウィンドウを閉じることです。

ポップアップを閉じるボタンの動作をカスタマイズしたい場合は、ページ上のボタンを指すことができます。 ポップアップ閉じボタンがクリックされると、選択したボタンがクリックされたように動作します。 選択したボタンが使用できない場合、ポップアップ閉じるボタンはデフォルトの動作に戻ります。

デフォルト: *デフォルト (キャンセル)*

### 2.6 使用セクション {#usage}

#### 2.6.1 使用済みマーク

Studio Pro で未使用の項目を検索するには、 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> を押します。 Studio Pro は、Java ソースコード内を参照することができないため、Java コードからのみ使用されるページは、使用されていないと表示されます。

プロパティ **使用済みとして** を *はい*に設定する ドキュメントが暗黙的に使用されていることを指定し、使用されていない項目を検索するときに Studio Pro がリストに追加されなくなります。

*デフォルト値*: いいえ