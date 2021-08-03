---
title: "日付の選択"
parent: "input-widgets"
---

## 1つの紹介

日付選択は、日付/時刻の属性を表示および編集するために使用できる [入力ウィジェット](input-widgets) です。 ローカライズされたカレンダーを表示する言語設定を考慮します。

{{% alert type="info" %}}

![](attachments/pages/date-picker.png) この日付ピッカーは、エンドユーザーが顧客の生年月日を設定できるようにします。

{{% /alert %}}

## 2 つの一般プロパティ

### 2.1 日付フォーマット

日付フォーマットは、日付ピッカーが日付、時刻、日付と時刻を表示するか、リンクされた属性のカスタムバリエーションを表示するかどうかを決定します。 これはデータの保存方法には影響しません。いずれの場合も、日付と時刻の両方が記録されます。 データの表示方法に影響を与えるだけです。 日付および/または時刻がどのようにフォーマットされるかは、データを表示するユーザーのローカライズによって異なります。

可能な値は次のとおりです。

* **Date** (これはデフォルトです)
* **時刻**
* **日付と時刻**
* **カスタム** (詳細は以下を参照)

### 2.2 カスタム日付フォーマット

日付書式として 'Custom' を選択した場合(上記参照)、このプロパティは属性値のフォーマット方法を決定します。 カスタム日付フォーマットは、以下の表で見つかった任意のシンボルを組み合わせることができる文字列です。 句読点は文字通りレンダリングされます。

{{% snippet file="refguide7/Custom+Date+Format+Tokens.md" %}}

{{% alert type="info" %}}
Even though a date picker with a custom date format is editable (as of Mendix 7.21.0), the calendar drop-down button will not be shown if the custom format does not represent the full date (meaning, the year [`y`-`yyyy`], month [`M`-`MMMM`], or day of month [`d`-`dd`] tokens are missing in the custom format).
{{% /alert %}}

### 2.3 プレースホルダーテキスト

date 属性が空の場合、プレースホルダー テキストが表示されます。 これは、エンドユーザーに期待されるフォーマットに関するヒントを与えるために使用することができます。 注意: ネイティブの日付ピッカー(iOSおよびAndroidバージョン4.0以降など)がある場合、プレースホルダテキストは機能しません。

## 3 バリデーションプロパティ

{{% snippet file="refguide7/Widget+Validation.md" %}}

## 4 データソースのプロパティ

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Label+Property.md" %}}

## 5 編集可能なプロパティ

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 6つの可視性プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 7 つのイベントのプロパティ

{{% snippet file="refguide7/On+Change+Event.md" %}}

{{% snippet file="refguide7/On+Enter+event.md" %}}

{{% snippet file="refguide7/On+Leave+Event.md" %}}

## 8 一般的なプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 9 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
