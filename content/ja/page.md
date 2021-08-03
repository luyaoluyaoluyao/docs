---
title: "ページ"
parent: "ページ"
---

## 1つの紹介

{{% alert type="info" %}}

このドキュメントでは、ページのプロパティについて説明します。 どのページにどのようなウィジェットを配置できるかの詳細については、 [ページ](pages) を参照してください。

{{% /alert %}}

PagesはMendixアプリケーションのエンドユーザーインターフェイスを定義します。 すべてのページは [レイアウト](layout) に基づいています。 [データ ビュー](data-view) や [データ グリッド](data-grid) などのウィジェットでレイアウトによって定義された "ギャップ" をページに埋めます。

{{% alert type="success" %}}
Mendixバージョンから 7. 6. ページエディタの **ビューモード** ボタンをクリックすると、デザインしているページのプレビューを見ることができます。 **編集モード** をクリックすると、ページの編集に戻ることができます。

![編集モードと表示モードボタン](attachments/pages/view-mode.png)

{{% /alert %}}

## 2つの一般的なプロパティ

{{% snippet file="refguide7/Document+Name+Property.md" %}}

{{% snippet file="refguide7/Documentation+Property.md" %}}

{{% snippet file="refguide7/Document+Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## デザイナープロパティ

{{% snippet file="refguide7/Canvas+Width+Property.md" %}}

{{% snippet file="refguide7/Canvas+Height+Property.md" %}}

## 4つの一般プロパティ

### 4.1 タイトル

[ページ タイトル ウィジェット](page-title) を使用して表示されるページのタイトル。 ページがポップアップウィンドウに表示されると、ポップアップのタイトルバーにタイトルが表示されます。 タイトルは、異なる目的でページを再利用できるようにするために、フォームが開かれた場所から上書きすることができます。 For example, a [grid create button](grid-new-button) and an [edit button](edit-button) can refer to the same page, but they override the titles to **New** and **Edit**, respectively.

### 4.2 レイアウト

これは、このページが基になっている [レイアウト](layout) です。

### 4.3 URL

ページの URL を使用して、直接ページに移動することができます (例えば、外部リンクやブックマークから)。 ページにアクセスすると、ブラウザのアドレスバーに表示されます。 URLが設定されていないページに移動すると、最後に訪問したURLが表示されます。 Note that the full URL of the page will be the base URL of your application followed by `/p` and then by the configured URL of the page (for example, `http://example.mendixcloud.com/p/home_page`).

トップレベルのデータビュー(パラメータ化されたページ)を持つページにはURLもあります。 そのようなページの URL プロパティには、最後に `{Id}` のパスセグメントが含まれている必要があります。 ブラウザーでは、 `{Id}` セグメントはエンティティの実際の識別子に置き換えられます。

簡単な電子商取引アプリケーションでは、次のようにURLを構成できます。

* */orders/* – the URL for a page with a data grid for `Orders` (in a browser, the URL will look like `http://example.mendixcloud.com/p/orders/`)

* */order/{Id}* – the URL for a page with data from a particular `Order` (actual URLs in a browser will look like `http://example.mendixcloud.com/p/order/3212449487634321`, wherein `3212449487634321` is the unique identifier of the `Order`)

## 5つのナビゲーションプロパティ

### 5.1 表示:

これらはページが表示されるモジュールロールです。 This has an effect on [menu widgets](menu-widgets) and on buttons that are visible only if allowed (for example, the [edit button](edit-button)).

詳細については、 [モジュールセキュリティ](module-security) を参照してください。

## 6種類のポップアッププロパティ

ポップアッププロパティはポップアップページにのみ関連します (コンテンツページではなく)。

### 6.1 幅 (ピクセル)

ポップアップの幅をピクセルで指定します。 0に設定すると、幅が自動的に決まります。

*デフォルト値:* 0

### 高さ6.2 (ピクセル)

ポップアップの高さをピクセルで指定します。 0に設定すると、高さが自動的に決まります。

*デフォルト値:* 0

### 6.3 Resizable

ポップアップをリサイズ可能(はい)または固定サイズ(いいえ)にするかを指定します。

*デフォルト値:* はい

### 6.4 アクションを閉じる

ポップアップ閉じボタンの動作を設定します(右上の小さな十字)。 ポップアップ閉じボタンのデフォルトの動作は、変更をロールバックしてポップアップを閉じることです。 ポップアップを閉じるボタンの動作をカスタマイズする場合は、ページ上のボタンを指すことができます。 ポップアップ閉じボタンがクリックされると、選択したボタンがクリックされたように動作します。 選択したボタンが使用できない場合、ポップアップ閉じるボタンはデフォルトの動作に戻ります。

 _Default value:_ Default (cancel)

## 7つの用法プロパティ

### 7.1 使用済みマーク

<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> を押すと、モデラー内の未使用の項目を検索できます。 Javaコードからのみ使用されるページは、モデラーがJavaソースコード内を見ることができないため、使用されないページとして表示されます。

プロパティ **を** に **はい**に設定します は、ドキュメントが暗黙的に使用されていることを指定し、モデラーは未使用のアイテムを検索するときにそれをリストしなくなります。

*デフォルト値:* いいえ
