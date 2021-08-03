---
title: "式"
parent: "application-logic"
menu_order: 100
description: "Mendixで様々な目的で使用できる式について説明します(例えば、 をクリックして、論理に基づいてオブジェクトのメンバーを変更します。"
tags:
  - "studio pro"
  - "表現"
  - "マイクロフロー式"
aliases:
  - /refguide8/microflow-expressions.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/expressions.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

式は関数または関数の組み合わせに基づいて値を変更します。

マイクロフロー内の名前付きアイテム (例えば、オブジェクト、リスト) または変数)は、アイテムの名前を挿入し、ドル記号を追加することによって式で呼び出すことができます(例えば、  `$customer` は、 `顧客` という名前のオブジェクトを参照することができます。

Attributes and associations of objects are accessed using a slash (for example, the **Name** attribute of the customer object is referred to as `$customer/Name`, and the **CRM.Customer_Order** association of the customer object is referred to as `$customer/CRM.Customer_Order`).

Starting from Studio Pro [8.10.0](/releasenotes/studio-pro/8.10#8100), attributes of associated objects can be accessed using multiple slashes (for example, the **Number** attribute of a single associated **CRM.Order** is referred to as `$customer/CRM.Customer_Order/CRM.Order/Number`).

式内の関数を結合できます。 この場合、かっこを使用して、計算の優先度と関連性を決定できます。 例えば、 **SellingPrice** は、デフォルトの **Price** と **Discount** 属性に基づいて計算されます。

```
$CurrentPrice/Price - (($CurrentPrice/Price **div** 100) * $OrderLine/Discount)
```

ここでは算術関数(減算、除算、乗算)を組み合わせています。

### 1.1 例

たとえば、 **パッケージ** と呼ばれる2つの属性を持つオブジェクトがあります。 `weight` (decimal) と `shippingCosts` (decimal) です。 パッケージの重量が1キロ未満の場合、送料はかかりません。 それ以外の場合、送料は€5.00です。 `shippingCosts` 属性を変更するための式は次のとおりです。

```
if $package/weight < 1.00 then 0.00 else 5.00`
```

### 1.2 正規表現

[正規表現](regular-expressions) リソースドキュメントを式で使用することはできません。 ただし、正規表現、サブ表現の形式 そして、正規表現文字列で使用されるクオンタイファイアは、 [正規表現](regular-expressions#expression) の *正規表現* のセクションで説明されているものと同じです。

## 2つの単語式

* [単位マイナス（-）](unary-expressions)

## 3 つの算術式

* [かけ算 ( * )](arithmetic-expressions)
* [Division ( div or : )](arithmetic-expressions)
* [Modulo ( mod )](arithmetic-expressions)
* [追加 ( + )](arithmetic-expressions)
* [減算 ( - )](arithmetic-expressions)

## 4つのリレーショナル式

* [より小さい ( <)](relational-expressions)
* [( > ) より大きい](relational-expressions)
* [以上 ( <= )](relational-expressions)
* [以上 ( >= )](relational-expressions)
* [( = ) と等しいです](relational-expressions)
* [等しくない ( != )](relational-expressions)

## 5つの特別チェック

* [空のオブジェクトをチェックしています](special-checks)
* [空のオブジェクトメンバーをチェックしています](special-checks)
* [isNew``](special-checks) - オブジェクトが新しいものかどうかをチェックする

## 6 ブール式

* [と](boolean-expressions)
* [または](boolean-expressions)
* [いいえ](boolean-expressions)

## 7 式の場合

* [if](if-expressions) – 条件付きアクションを実行する

## 8 数学関数コール

* [`max`](mathematical-function-calls) - 数値のリストの最大値
* [`min`](mathematical-function-calls) – 数値のリストの最小値
* [`ラウンド`](mathematical-function-calls) - 浮動小数点数の丸め、必要に応じて指定された精度に
* [`random`](mathematical-function-calls) - 乱数生成
* [`floor`](mathematical-function-calls) - 浮動小数点数の丸め
* [`ceil`](mathematical-function-calls) - 浮動小数点数の丸め
* [`pow`](mathematical-function-calls) - 指数化
* [`abs`](mathematical-function-calls) – 絶対値

## 9 文字列関数コール

* [`toUpperCase`](string-function-calls) - 文字列を大文字に変換します
* [`toLowerCase`](string-function-calls) – 文字列を小文字に変換します
* [`length`](string-function-calls) - 文字列の長さ
* [`substring`](string-function-calls) - 文字列の一部を取得する
* [`find`](string-function-calls) - 部分文字列の位置を取得する
* [`findLast`](string-function-calls) – gets the last sub-string position
* [`には`](string-function-calls) が含まれています - サブストリングを含む
* [`startsWith`](string-function-calls)  - 文字列が指定された部分文字列で始まるかどうかを決定する
* [`endsWith`](string-function-calls) - 文字列が指定されたサブストリングで終わるかどうかを決定します
* [`trim`](string-function-calls) - 先頭と末尾の空白を削除する
* [`isMatch`](string-function-calls) – 正規表現に一致
* [`replaceAll`](string-function-calls) – サブストリングの出現を置き換え
* [`replaceFirst`](string-function-calls) - サブストリングの最初の発生を置き換えます
* [`String concatenation ( + )`](string-function-calls) – 文字列の結合
* [`urlEncode`](string-function-calls) – URLで使用する文字列を変換します。
* [`urlDecode`](string-function-calls) – URLから文字列を戻します。

## 10 日付の作成

* [`dateTime`](date-creation) - サーバーのカレンダーを使用して日付値を作成する
* [`dateTimeUTC`](date-creation) - UTCカレンダーを使用して日付値を作成する

## 日付関数呼び出しの間に11

* [`ミリ秒間隔`](between-date-function-calls) - 2つの日付間のミリ秒
* [`秒`](between-date-function-calls) - 2つの日付の間の秒
* [`分前`](between-date-function-calls) - 2日間の分
* [`時間`](between-date-function-calls) - 2つの日付の間の時間
* [`日前`](between-date-function-calls) - 2日前
* [`週間`](between-date-function-calls) - 2つの日付の間の週
* [`calendarMontsBetween`](between-date-function-calls) - 2つの日付の間のヶ月
* [`calendar YearsBetween`](between-date-function-calls) - the years between two date

## 12 日付関数呼び出しを追加

* [`addMilliseconds`](add-date-function-calls) - 日付にミリ秒を追加します
* [`addSeconds`](add-date-function-calls) - 日付に秒を追加
* [`addMinutes`](add-date-function-calls) - 日付に分を追加
* [`addHours`](add-date-function-calls) - 日付に時間を追加
* [`addDays`](add-date-function-calls) - 日付に日付を追加
* [`addDaysUTC`](add-date-function-calls) - UTCカレンダーを使用して日付を追加します
* [`addWeek`](add-date-function-calls) - 日付に週を追加
* [`addWeksUTC`](add-date-function-calls) - UTCカレンダーを使用して週を日付に追加
* [`addMonths`](add-date-function-calls) - 月を日付に追加
* [`addMonthsUTC`](add-date-function-calls) - UTCカレンダーを使用して月を日付に追加
* [`addYears`](add-date-function-calls) - 日付に年を追加
* [`addYearsUTC`](add-date-function-calls) - UTCカレンダーを使用して日付に年を追加

## 13 日付までトリム

* [`trimToSeconds`](trim-to-date) - 秒単位でトリムする
* [`trimToMinutes`](trim-to-date) - 分単位でトリムする
* [`trimToHours`](trim-to-date) - 時間をトリムする
* [`trimToHoursUTC`](trim-to-date) - UTCカレンダーを使用して時間をトリムする
* [`trimToDays`](trim-to-date) - 日数をトリムする
* [`trimToDaysUTC`](trim-to-date) - UTCカレンダーを使用して日数をトリムする
* [`trimToMonths`](trim-to-date) - 月にトリムする
* [`trimToMonthsUTC`](trim-to-date) - UTCカレンダーを使用して月にトリムします
* [`trimToYears`](trim-to-date) - 年をトリムする
* [`trimToYearsUTC`](trim-to-date) - UTCカレンダーを使用して年をトリムする

## 14 To String

詳細は [To String](to-string) を参照してください。

## 15 parse Integer

詳細は [整数の解析](parse-integer) を参照してください。

## 16 parse & Format Decimal Function Calls

* [`parseDecimal`](parse-and-format-decimal-function-calls) - 文字列を小数に変換します
* [formatDecimal`formatDecimal`](parse-and-format-decimal-function-calls) - 小数を文字列に変換します。

## 17 Parse & Format Date Function Calls

* [`parseDateTime[UTC]`](parse-and-format-date-function-calls) - 文字列を日付値に変換します
* [`formatDateTime[UTC]`](parse-and-format-date-function-calls) - 日付の値を文字列に変換します
* [`formatTime[UTC]`](parse-and-format-date-function-calls) - 日付値の時刻部分を文字列に変換します。
* [`[UTC]`](parse-and-format-date-function-calls) – 日付値の日付部分を文字列に変換します。
* [`dateTimeToEpoch`](parse-and-format-date-function-calls) - 日付を長いに変換します
* [`epochToDateTime`](parse-and-format-date-function-calls) - 長さを日付に変換する

## 式で18列挙型

* [`getCaption`](enumerations-in-expressions) – 現在の言語の列挙値のキャプションを取得
* [`getKey`](enumerations-in-expressions) – 列挙値の技術的な名前を取得
