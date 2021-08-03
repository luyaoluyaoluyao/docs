---
title: "テキストボックス"
parent: "input-widgets"
menu_order: 10
tags:
  - "studio pro"
  - "データ"
---

## 1つの紹介

テキストボックスを使用して表示し、必要に応じて表示します。 エンドユーザーがテキスト形式のオブジェクトから属性の値を編集できるようにします。 以下の [データ型の属性を表示するために使用できます](data-types):

* Autonumber
* 小数点以下桁数
* ハッシュ文字列
* 整数
* 長い順
* 文字列

テキスト ボックスは、 [データ ウィジェット](data-widgets) に配置し、ウィジェットによって取得されたオブジェクトの属性を表示する必要があります。 表示される属性の名前は、テキストボックス内に角括弧と青色の間で表示されます。

例えば、次のテキストボックスでは、エンドユーザーが顧客の **名前** を表示して設定することができます。

![](attachments/text-box/text-box.png)

## 2つのプロパティ

テキストボックスのプロパティの例を以下の画像に示します。

{{% image_container width="250" %}}![](attachments/text-box/text-box-properties.png)
{{% /image_container %}}

テキスト ボックスのプロパティは、次のセクションで構成されています。

* [アクセシビリティ](#accessibility)
* [一般的な](#common)
* [データソース](#data-source)
* [デザインプロパティ](#design-properties)
* [編集可能](#editability)
* [イベント](#events)
* [書式設定](#formatting)
* [全般](#general)
* [ラベル](#label)
* [検証](#validation)
* [公開範囲](#visibility)

### 2.1 アクセシビリティセクション{#accessibility}

#### 2.1.1 自動完了

autocomplete プロパティは、テキストボックスにオートコンプリートを有効にするかどうかを指定します。 autocomplete 属性は、ユーザーが好む値を持つフィールドに事前に入力するブラウザの機能も向上します。 これがどのようにアクセシビリティガイドラインを遵守するのに役立つかについては、 [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG21/#input-purposes) を参照してください。

### 2.2 共通セクション{#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.3 データソースセクション{#data-source}

{{% snippet file="refguide/data-source-section-link.md" %}}

### 2.4 プロパティセクション{#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.5 編集可能セクション{#editability}

{{% snippet file="refguide/editability-section-link.md" %}}

### 2.6 イベントセクション{#events}

#### 2.6.1 変更時のイベント{#on-change}

on change イベントプロパティは、値が変更されて送信されたときに実行されるアクションを指定します。 A value will be submitted when pressing the <kbd>Enter</kbd> key or leaving the widget, either by using the <kbd>Tab</kbd> key or by clicking another widget.

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.2 動作の変更時

The On Change Behaviour property lets users select how **on change** is handled via the following options Studio Pro:

* ユーザーが入力フィールドを離れたとき (デフォルト)
* ユーザーがデータを入力している間

##### 2.6.2.1 ユーザが入力フィールドを離れた場合 (Default)

このオプションは、Studio Pro の以前のバージョンと同様に動作します。 テキストボックスは、データベースに保存されている値と同じではなく、次のいずれかの条件が満たされた場合に変更を適用します。

* 入力キーが押された時: これは変更時と入力キーが押された時にトリガーされます
* ぼかし：これは変更時と休暇時にトリガーされます

これは、入力中にユーザが変更イベントをトリガーする方法がないことを意味します。 このユースケースでは、2つ目のオプションが必要です: **ユーザーがデータを入力している間**。

##### 2.6.2.2 ユーザーがデータを入力している間

このオプションを使用すると、入力中にユーザーが変更イベントを起動するようになります。 テキストボックスは、データベースに保存されている以前の値と同じではなく、設定された **(ms)** の時間の後に適用された最後の変更が行われた場合に変更を保存します。

**では、ユーザーがデータ**を入力している間、ユーザーは **(ms) 後に適用** と呼ばれるもう1つのプロパティを調整できるようになりました(上記)。 これにより、変更イベントの呼び出し量が減り、アプリのパフォーマンスが向上します。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.3 イベントに参加する

on enter イベントプロパティは、ウィジェットの入力時に実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、マウスでクリックします。

{{% snippet file="refguide/events-section-link.md" %}}

#### 休暇中の2.6.4

on leave イベントプロパティは、ウィジェットを離れたときに実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、別のウィジェットをクリックします。

これは、値が変更されていない場合でも、イベントが常にトリガーされるという点で [On change](#on-change) プロパティとは異なります。

{{% snippet file="refguide/events-section-link.md" %}}

#### 2.6.5 キー入力時 イベント

on enter key press event プロパティは、フォーカスがウィジェット内にあり、 <kbd>Enter</kbd> キーが押されたときに実行されるアクションを指定します。 Webアプリケーションでは、アクションが実行された後、ウィジェットはフォーカスを保持します。

{{% snippet file="refguide/events-section-link.md" %}}

### 2.7 書式設定セクション{#formatting}

書式設定セクションは、数値属性の表示方法にのみ適用されます。 以下は以下のデータ型の属性です:

* 小数点以下桁数
* 整数
* 長い順

{{% snippet file="refguide/numeric-formatting-link.md" %}}

### 2.8 一般セクション{#general}

#### 2.8.1 パスワードとして表示

データ型の属性 `String` または `ハッシュ文字列` は、その値を非表示にすることができます。 これは、たとえば、傍観者がそれらを見ないようにするために、パスワードに使用することができます。

| 値                 | 説明                                                |
| ----------------- | ------------------------------------------------- |
| False *(default)* | 標準テキスト ボックス                                       |
| True              | 型付けされた文字はエンド・ユーザーには表示されず、型付けされた文字ごとにアスタリスクが表示されます |

#### 2.8.2 Input Mask

{{% alert type="info" %}}入力マスクはネイティブのモバイルページではサポートされていません。

入力マスクは、文字列データ型用に設計されています。 数値またはハッシュ化された文字列データ型で使用する場合は注意が必要です。
{{% /alert %}}

入力マスクは、以下のルールに従って、エンドユーザーがテキストボックスに入力できるものを制限します:

| 文字  | Allows Input of |
| --- | --------------- |
| `9` | 任意の数字           |
| `Z` | どんな文字           |
| `U` | 大文字の文字          |
| `L` | 小文字です           |
| `*` | 文字 *または* 桁の数字   |

他の文字は文字通り取られます。

例えば、入力マスク `99-LLL-9999` は `24-apr-2008` にマッチします。

#### 2.8.3 最大長さ

このプロパティは、このテキストボックスに入力できる最大文字数を指定します。

| 値               | 説明                         |
| --------------- | -------------------------- |
| 属性の長さ *(デフォルト)* | 最大文字数は、接続された属性の最大長さと同じです   |
| 無制限です           | 最大文字数に制限はありません             |
| カスタム            | ウィジェットのプロパティで文字数の最大値を指定します |

#### 2.8.4 プレースホルダーテキスト

プレースホルダー テキストは、まだ入力されていない場合、または、表示された属性が空の場合に表示されます。

たとえば、エンドユーザーにどのようなテキストを入力すべきかのヒントを与えるために使用できます。

<a name="label-properties"></a>

### 2.9 ラベルセクション{#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.10 検証セクション{#validation}

{{% snippet file="refguide/widget-validation-link.md" %}}

### 2.11 可視性セクション{#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}

## 3 続きを読む

* [データ型：](data-types)
* [データビュー](data-view)
* [属性](attributes)
