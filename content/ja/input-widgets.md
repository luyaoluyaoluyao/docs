---
title: "入力ウィジェット"
parent: "ページ"
menu_order: 30
description: "オブジェクトの属性を表示および編集するためにページに追加できるウィジェット。"
tags:
  - "studio pro"
  - "ウィジェットを入力"
  - "ウィジェット"
  - "参照選択"
  - "参照セット"
  - "関連"
  - "編集"
  - "data input"
---

## 1つの紹介

入力ウィジェットはエンドユーザーにデータを表示し、必要に応じてデータを編集することができます。

入力ウィジェットは機能するためにエンティティの属性にリンクする必要があります。 そのため、エンティティタイプのオブジェクトを含むデータ ウィジェット内に配置する必要があります。

例えば、入力ウィジェットは [データ ビュー](data-view) 内に配置できます。

![ウィジェットを含むデータビュー](attachments/input-widgets/data-view.png)

いくつかの異なる入力ウィジェットがあります。これらは、異なる [データ型](data-types) と [関連付け](associations) の異なるタイプに使用されます。 入力ウィジェットカテゴリには以下のウィジェットが含まれています:

*   [Text Box](text-box) – displays and, optionally, allows the end-user to add or edit text data from a *numeric* or *string-like* attribute:

    ![名前属性を含むテキストボックス](attachments/input-widgets/text-box.png)

*   [テキストエリア](text-area) - エンドユーザーが *文字列* 属性から長いテキストデータを追加または編集できるようにします。

    ![メモ属性を含むテキストエリア](attachments/input-widgets/text-area.png)

*   [Drop-Down](drop-down) – shows the current value of and, optionally, allows end-users to pick an option from a list of options in an *enumeration* attribute:

    ![地域属性を含むドロップ ダウン](attachments/input-widgets/drop-down.png)

*   [Check Box](check-box) – shows the current value of and, optionally, allows end-users to set a *Boolean* attribute to `true` or `false`:

    ![個人属性を表示するチェックボックス](attachments/input-widgets/check-box.png)

*   [ラジオボタン](radio-buttons) – 現在の値と、オプションで表示されます。 エンドユーザーが[enumeration ](radio-buttons)属性または *ブール* 属性のオプションのリストからオプションを選択できるようにします。 *ブール* 属性の値:

    ![優先する連絡先時間と個人の属性を表示するラジオボタン](attachments/input-widgets/radio-buttons.png)

*   [日付選択](date-picker) - エンドユーザーが *日付と時刻* 属性をカレンダーから選択できるようにします。

    ![最後に連絡した属性を表示する日付ピッカー](attachments/input-widgets/date-picker.png)

*   [Reference Selector](reference-selector) – shows and, optionally, allows end-users to select a *one-to-one* or *one-to-many* association using the value of a *string*, *numeric*, *enumeration*, or *Date and time* attribute on the associated object:

    ![関連会社の会社名属性を示す参照セレクター](attachments/input-widgets/reference-selector.png)

*   [Reference Set Selector](reference-set-selector) –  lists with one or more attributes and, optionally, allows the end-user to add and remove associated objects linked via a *many-to-many* association:

    ![関連製品の詳細を示す参照セットセレクター](attachments/input-widgets/reference-set-selector.png)

*   [Input Reference Set Selector](input-reference-set-selector) – shows an attribute from and, optionally, allows the user to add and remove associated objects linked via a *many-to-many* association:

    ![関連製品の名前属性を示す入力参照セットセレクター](attachments/input-widgets/input-reference-set-selector.png)

{{% alert type="info" %}}
データ型の詳細については、 [Data Types](data-types) を参照してください。

関連付けとそのプロパティの詳細については、 [Associations](associations) を参照してください。
{{% /alert %}}

## 2 基本機能の実行

{{% snippet file="refguide/performing-basic-functions-widgets.md" %}}

## 3 続きを読む

* [ページ](page)
* [ページ](ページ)
* [データ型：](data-types)
* [関連](関連)
  