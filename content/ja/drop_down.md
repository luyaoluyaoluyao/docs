---
title: "ドロップダウン"
parent: "input-widgets"
tags:
  - "ドロップダウン"
  - "input"
  - "ページ"
  - "ウィジェット"
  - "列挙型"
aliases:
  - /refguide7/drop-down-widget.html
---

ドロップダウンは、列挙属性の表示と編集に使用できる [入力ウィジェット](input-widgets) です。 参照セレクタと混同してはいけません。これは、 [アソシエーション](associations) を埋めるオブジェクトを選択するために使用されます。

{{% alert type="info" %}}

 ![](attachments/pages/drop-down.png)

このドロップダウン ウィジェットでは、ユーザーがお気に入りの色を選択できます。

{{% /alert %}}

## 一般プロパティ

### オプションの図表番号を空にする

このプロパティは、ユーザーに表示されるドロップダウンの空のオプションのキャプションを表します。 これは翻訳可能なテキストです。 詳細については、 [翻訳可能なテキスト](translatable-texts) を参照してください。

{{% alert type="info" %}}

空のオプションにキャプションを記入すると、アプリケーションのユーザーエクスペリエンスが向上します。 また、スクリーンリーダーのユーザーがアプリケーションを簡単に操作するのに役立ちます。 たとえば、車の色の選択を表すドロップダウンには、"Select a color" というキャプションが表示されます。

{{% /alert %}}

{{% alert type="info" %}}

空のオプションキャプションは Mendix 7.2.0 から利用できます。

{{% /alert %}}

## バリデーションプロパティ

{{% snippet file="refguide7/Widget+Validation.md" %}}

## データソースのプロパティ

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Label+Property.md" %}}

## 編集可能なプロパティ

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## イベントのプロパティ

{{% snippet file="refguide7/On+Change+Event.md" %}}

{{% snippet file="refguide7/On+Enter+event.md" %}}

{{% snippet file="refguide7/On+Leave+Event.md" %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
