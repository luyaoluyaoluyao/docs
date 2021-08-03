---
title: "式"
parent: "共通要素"
aliases:
  - /ja/refguide7/microflow-expressions.html
description: "Mendixで様々な目的で使用できる式について説明します(例えば、 をクリックして、論理に基づいてオブジェクトのメンバーを変更します。"
---

表現は、例えばロジックに基づいてオブジェクトのメンバーを変更するために使用することができます。 マイクロフロー内の変数は、変数の名前を挿入し、ドル記号を追加することによって、式内で呼び出すことができます。 例えば、 _$customer_ は変数 _の顧客_ を指します。 式は再帰的に使うことができます。例えば、 _1 + 2 + 3_. オブジェクト変数の属性と関連付けは、例えば、 _$customer/Name_, _$customer/CRM.Customer_Order_ を使用してアクセスされます。

これを示すために、変数名 _パッケージ_ が 2 つの属性を持つオブジェクトを想像してみてください: _weight_ (Float) と _shippingCosts _(Decimal )。 ルール:パッケージの重量が1キロ未満の場合は、送料はありません。 それ以外の場合、送料は€5.00です。 属性 _shippingCosts を変更するための式_ は: _if $package/weight < 1.00 then 0.00 else 5.00_.

式の可能性の概要は以下のとおりです。

### [単項式](unary-expressions):

* [単位マイナス（-）](unary-expressions)

### [Arithmetic Expressions](arithmetic-expressions):

* [かけ算 ( * )](arithmetic-expressions)
* [Division ( div or : )](arithmetic-expressions)
* [Modulo ( mod )](arithmetic-expressions)
* [追加 ( + )](arithmetic-expressions)
* [減算 ( - )](arithmetic-expressions)

### [リレーショナル表現](relational-expressions):

* [より小さい ( <)](relational-expressions)
* [( > ) より大きい](relational-expressions)
* [以上 ( <= )](relational-expressions)
* [以上 ( >= )](relational-expressions)
* [( = ) と等しいです](relational-expressions)
* [等しくない ( != )](relational-expressions)

### [特別チェック](special-checks)

* [空のオブジェクトをチェックしています](special-checks)
* [空のオブジェクトメンバーをチェックしています](special-checks)
* [isNew``](special-checks) - オブジェクトが新しいかどうかをチェックする

### [ブーリアン式](boolean-expressions)

* [と](boolean-expressions)
* [または](boolean-expressions)
* [いいえ](boolean-expressions)

### [If expressions](if-expressions)

### [数学関数の呼び出し](mathematical-function-calls)

* [`max`](mathematical-function-calls) - 数値のリストの最大値
* [`min`](mathematical-function-calls) - 数値のリストの最小値
* [`round`](mathematical-function-calls) - 浮動小数点数を四捨五入し、必要に応じて指定した精度に丸めます
* [ランダム``](mathematical-function-calls) - 乱数生成
* [`floor`](mathematical-function-calls) - 浮動小数点数を下に丸めます
* [`ceil`](mathematical-function-calls) - 浮動小数点数を四捨五入する
* [`pow`](mathematical-function-calls) - 基準
* [`abs`](mathematical-function-calls) - 絶対値
* [`floatsEqual` `/ currenciesEqual`](mathematical-function-calls) - 特定の精度のための float/currencies の平等（非推奨）

### [文字列関数の呼び出し](string-function-calls)

* [`toUpperCase`](string-function-calls) - 文字列を大文字に変換する
* [`toLowerCase`](string-function-calls) - 文字列を小文字に変換
* [長さ``](string-function-calls) - 文字列の長さ
* [`substring`](string-function-calls) - 文字列の一部を取得する
* [`find`](string-function-calls) - 部分文字列の位置を取得する
* [`findLast`](string-function-calls) - Get last substring position
* [`には`](string-function-calls) が含まれています - 部分文字列を含む
* [`startsWith`](string-function-calls)  - 文字列が指定された部分文字列で始まるかどうかを決める
* [`endsWith`](string-function-calls)  - 文字列が指定された部分文字列で終わるかどうかを決定する
* [`trim`](string-function-calls) - 先頭と末尾の空白を削除
* [`isMatch`](string-function-calls) - 正規表現
* [`replaceAll`](string-function-calls) - 部分文字列の発生を置換
* [replaceFirst``](string-function-calls) - 部分文字列の最初の発生を置換
* [文字列の連結(+)](string-function-calls) - 文字列の連結(concatenate)
* [`urlEncode`](string-function-calls) - URLで使用する文字列を変換する
* [`urlDecode`](string-function-calls) - URLから文字列を戻す。

### [作成日](date-creation)

* [`dateTime`](date-creation) - サーバーのカレンダーを使用して日付値を作成する
* [`dateTimeUTC`](date-creation) - UTCカレンダーを使用して日付の値を作成する

### [日付関数の呼び出し間](between-date-function-calls)

* [`ミリ秒間`](between-date-function-calls) - 2つの日付の間の時間
* [`秒間`](between-date-function-calls) - 2つの日付の間の秒
* [`分間`](between-date-function-calls) - 2日間の分
* [`時間`](between-date-function-calls) - 2日間の時間
* [``](between-date-function-calls) - 2つの日付の間
* [`週間`](between-date-function-calls) - 2つの日付の間の週

### [日付関数の呼び出しを追加](add-date-function-calls)

* [`addMilliseconds`](add-date-function-calls) - 日付にミリ秒を追加
* [`addSeconds`](add-date-function-calls) - 日付に秒を追加
* [`addMinutes`](add-date-function-calls) - 日付に分を追加
* [`addHours`](add-date-function-calls) - 日付に時間を追加
* [`addDays`](add-date-function-calls) - 日付に日付を追加
* [`addDaysUTC`](add-date-function-calls) - UTCカレンダーを使用して日付を追加
* [`addWeek`](add-date-function-calls) - 日付に週を追加
* [`addWeksUTC`](add-date-function-calls) - UTCカレンダーを使用して週を日付に追加
* [`addMonths`](add-date-function-calls) - 日付に月を追加
* [`addMontsUTC`](add-date-function-calls) - UTCカレンダーを使用して月を日付に追加
* [`addYears`](add-date-function-calls) - 日付に年を追加
* [`addYearsUTC`](add-date-function-calls) - UTCカレンダーを使用して日付に年を追加

### [これまでにトリムする](trim-to-date)

* [`trimToSeconds`](trim-to-date) - 秒単位でトリムする
* [`trimToMinutes`](trim-to-date) - 分単位でトリムする
* [`trimToHours`](trim-to-date) - 時間をトリムする
* [`trimToHoursUTC`](trim-to-date) - UTCカレンダーを使用して時間をトリムする
* [`trimToDays`](trim-to-date) - 日にトリムする
* [`trimToDaysUTC`](trim-to-date) - UTCカレンダーを使用して日数をトリムする
* [`trimToMonths`](trim-to-date) - 月にトリムする
* [`trimToMonthsUTC`](trim-to-date) - UTCカレンダーを使用して月にトリムする
* [`trimToYears`](trim-to-date) - 年をトリムする
* [`trimToYearsUTC`](trim-to-date) - UTCカレンダーを使用して年をトリムする

### [文字列へ](to-string)

### [フロートするには](to-float) (非推奨)

### [整数を解析](parse-integer)

### [フロート関数呼び出しの解析/フォーマット](parse-and-format-float-function-calls) (非推奨)

* [`parseFloat`](parse-and-format-float-function-calls) - 文字列をfloatに変換する
* [formatFloat``](parse-and-format-float-function-calls) - フロートを文字列に変換する

### [小数点以下の関数呼び出しを解析/書式設定する](parse-and-format-decimal-function-calls)

* [`parseDecimal`](parse-and-format-decimal-function-calls)  - 文字列を小数に変換する
* [`formatDecimal`](parse-and-format-decimal-function-calls)  - 小数を文字列に変換する

### [日付関数の呼び出しを解析/書式設定する](parse-and-format-date-function-calls)

* [`parseDateTime[UTC]`](parse-and-format-date-function-calls) - 文字列を日付の値に変換する
* [`formatDateTime[UTC]`](parse-and-format-date-function-calls) - 日付値を文字列に変換する
* [`formatTime[UTC]`](parse-and-format-date-function-calls) - 日付値の時刻部分を文字列に変換する
* [`[UTC]`](parse-and-format-date-function-calls) - 日付値の日付部分を文字列に変換する

### [式内の列挙数](enumerations-in-expressions)

* [`getCaption`](enumerations-in-expressions) - 現在の言語での列挙値のキャプションの取得
* [`getKey`](enumerations-in-expressions) - 列挙値の技術的な名前を取得する
