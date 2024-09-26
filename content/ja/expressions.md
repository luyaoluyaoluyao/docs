---
title: "式"
menu_order: 55
description: "Mendix Studio で利用可能なマイクロフロー式について説明します。"
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "表現"
  - "表現"
  - "値を設定"
  - "変数"
aliases:
  - /ja/studio/microflows-expressions.html
---

## 1つの紹介

式は関数または関数の組み合わせに基づいて値を変更します。

ワークフロー、ページ、マイクロフローに式を使用できます。 式は通常、特定のアクティビティまたはプロパティの条件を設定するために使用されます。 例えばマイクロフローやワークフローの決定条件です

ワークフローでは、次の要素に式を使用できます。

* [決定](workflows-general-activities)
* **** [ワークフロー](workflow-properties) と [ユーザー タスク](workflows-user-task) の期限 </a> プロパティ

式は、ページ上の以下のプロパティで使用できます。

* ウィジェットの条件付き編集
* ウィジェットの条件付き表示
* **コンテンツ** プロパティ [テキスト ウィジェット](page-editor-widgets-text)

表現は、マイクロフロー内で以下のアクティビティに使用できます。

*  オブジェクトの変更
*  変数の変更
*  オブジェクトを作成
*  変数を作成
*  [決定](microflows-decision)
*  イベントを終了

マイクロフローアクティビティの設定と値の変更の詳細については、 see [Set & Change a Value for different Activities in the Microflow](microflows-setting-and-changing-value).

## 2 式を書く

マイクロフローとワークフロー内の名前付き項目 (オブジェクト、リストなど) または変数)は、アイテムの名前を挿入し、ドル記号を追加することによって式で呼び出すことができます(例えば、  `$Customer` は、 `Customer` という名前のオブジェクトを参照することができます。

オブジェクトの属性と関連付けはスラッシュを使用してアクセスされます (例えば、 顧客オブジェクトの **Name** 属性は `$Customer/Name` と呼ばれます。

かっこを使用して、計算の優先度と関連性を決定できます。 例えば、 **SellingPrice** は、デフォルトの **Price** と **Discount** 属性に基づいて計算されます。

```
$CurrentPrice/Price - (($CurrentPrice/Price **div** 100) * $OrderLine/Discount)
```

ここでは算術関数(減算、除算、乗算)を組み合わせています。

式ではプレーンテキストを入力することはできません。テキストはその周りにシングルクォテーションマーク (`'`) で記述する必要があります。 例えば、文字列 `Mendix`を返したい場合は、 `'Mendix'` として記述する必要があります。

式を書くのに役立つ候補のリストを使うことができます。 このリストを表示するには、 <kbd>Ctrl</kbd> + <kbd>スペース</kbd> のショートカットを使用します。 提案は次のカテゴリに分けることができます:

* **変数とその属性** - 現在のマイクロフロー、ページ、またはワークフローで利用可能な変数または属性
* **列挙値** - 式で使用できる [列挙タイプ](domain-models-enumeration) の値
* **関数** - 式で使用できる操作 (詳細については、 [式タイプ](#expression-types) セクションを参照してください)
* **Keywords** – key phrases or words that you can use in an expression (for example, `empty` – a value that can be used to check if a variable is empty)
* **Booleans** – trueまたはfalse キーワード
* **Operators** – code elements that perform logical or mathematical operations; you can use Boolean or relational expressions (for more information, see the [Expression Types](#expression-types) section below)

式にエラーがある場合は、エラーのある場所 が赤色に強調表示され、マウスポインタを置くとエラーメッセージが表示されます。  場合によっては、問題を迅速に解決するための迅速な修正があります。

![](attachments/expressions/expression-error.png)


### 2.3 式の例

式の使用方法を示す例を以下に示します。

#### 2.3.1 例 1

マイクロフローに [Decision](microflows-decision) があり、顧客の成績が金であり、注文の価格が100を超えているかどうかをチェックする式を書く必要があります (この式がtrueの場合に許可される **Decision** の後に割引を設定できます):

![](attachments/expressions/example-decision.png)

式は次のようになります:

![](attachments/expressions/expression-decision.png)

#### 2.3.2 例 2

マイクロフローに [の決定](microflows-decision) を追加して、オブジェクトが存在するかどうかをチェックします(以下の例では、オブジェクト *顧客*です)。 また、お客様の名前が特定の名前と一致するかどうかも確認します(下の例では、お客様の名前は *Mendix* です)。 式は次のようになります:

![](attachments/expressions/customer-empty-and-name-example.png)

#### 2.3.3 例 3

ワークフローに [ユーザー タスク](workflows-user-task) があり、明後日までにユーザー タスクを行う必要があることをリマインダーとして **締切日** を追加します。 次の式を記述できます。

![ユーザータスク式](attachments/expressions/user-task-due-date.png)

## 3 式のタイプ {#expression-types}

Studio で最も多く使用されている式のリストは以下のとおりです。 使用可能な式の完全なリストについては、 [Studio Pro Guide](/refguide/expressions) の *式* を参照してください。

### 3.1 単項式

* [単位マイナス（-）](/refguide/unary-expressions)

### 3.2 算術式

* [かけ算 ( * )](/refguide/arithmetic-expressions)
* [Division ( div or : )](/refguide/arithmetic-expressions)
* [Modulo ( mod )](/refguide/arithmetic-expressions)
* [追加 ( + )](/refguide/arithmetic-expressions)
* [減算 ( - )](/refguide/arithmetic-expressions)

### 3.3 リレーショナル式

* [より小さい ( <)](/refguide/relational-expressions)
* [( > ) より大きい](/refguide/relational-expressions)
* [以上 ( <= )](/refguide/relational-expressions)
* [以上 ( >= )](/refguide/relational-expressions)
* [( = ) と等しいです](/refguide/relational-expressions)
* [等しくない ( != )](/refguide/relational-expressions)

### 3.5 ブール式

* [と](/refguide/boolean-expressions)
* [または](/refguide/boolean-expressions)
* [いいえ](/refguide/boolean-expressions)

### 3.6 数学関数コール

* [`max`](/refguide/mathematical-function-calls) - 数値のリストの最大値
* [`min`](/refguide/mathematical-function-calls) – 数値のリストの最小値
* [`ラウンド`](/refguide/mathematical-function-calls) - 特定の精度に数値を四捨五入します
* [`random`](/refguide/mathematical-function-calls) - 乱数生成
* [`floor`](/refguide/mathematical-function-calls) - 浮動小数点数の丸め
* [`ceil`](/refguide/mathematical-function-calls) - 浮動小数点数の丸め
* [`pow`](/refguide/mathematical-function-calls) - 指数化
* [`abs`](/refguide/mathematical-function-calls) – 絶対値

### 3.7 文字列関数コール

* [`toUpperCase`](/refguide/string-function-calls) - 文字列を大文字に変換します
* [`toLowerCase`](/refguide/string-function-calls) – 文字列を小文字に変換します
* [`length`](/refguide/string-function-calls) - 文字列の長さ
* [`substring`](/refguide/string-function-calls) - 文字列の一部を取得する
* [`find`](/refguide/string-function-calls) - 部分文字列の位置を取得する
* [`findLast`](/refguide/string-function-calls) – gets the last sub-string position
* [`には`](/refguide/string-function-calls) が含まれています - サブストリングを含む
* [`startsWith`](/refguide/string-function-calls)  - 文字列が指定された部分文字列で始まるかどうかを決定する
* [`endsWith`](/refguide/string-function-calls) - 文字列が指定されたサブストリングで終わるかどうかを決定します
* [`trim`](/refguide/string-function-calls) - 先頭と末尾の空白を削除する
* [`replaceAll`](/refguide/string-function-calls) – サブストリングの出現を置き換え
* [`replaceFirst`](/refguide/string-function-calls) - サブストリングの最初の発生を置き換えます
* [`String concatenation ( + )`](/refguide/string-function-calls) – 文字列の結合

### 3.8 日付作成

* [`dateTime`](/refguide/date-creation) - サーバーのカレンダーを使用して日付値を作成する

### 3.9 日付関数の呼び出し間

* [`ミリ秒間隔`](/refguide/between-date-function-calls) - 2つの日付間のミリ秒
* [`秒`](/refguide/between-date-function-calls) - 2つの日付の間の秒
* [`分前`](/refguide/between-date-function-calls) - 2日間の分
* [`時間`](/refguide/between-date-function-calls) - 2つの日付の間の時間
* [`日前`](/refguide/between-date-function-calls) - 2日前
* [`週間`](/refguide/between-date-function-calls) - 2つの日付の間の週
* [`calendarMontsBetween`](/refguide/between-date-function-calls) - 2つの日付の間のヶ月
* [`calendar YearsBetween`](/refguide/between-date-function-calls) - the years between two date

### 3.10 日付関数呼び出しを追加

* [`addMilliseconds`](/refguide/add-date-function-calls) - 日付にミリ秒を追加します
* [`addSeconds`](/refguide/add-date-function-calls) - 日付に秒を追加
* [`addMinutes`](/refguide/add-date-function-calls) - 日付に分を追加
* [`addHours`](/refguide/add-date-function-calls) - 日付に時間を追加
* [`addDays`](/refguide/add-date-function-calls) - 日付に日付を追加
* [`addWeek`](/refguide/add-date-function-calls) - 日付に週を追加
* [`addMonths`](/refguide/add-date-function-calls) - 月を日付に追加
* [`addYears`](/refguide/add-date-function-calls) - 日付に年を追加

### 3.11 parse & Format Decimal Function Calls

* [formatDecimal`formatDecimal`](/refguide/parse-and-format-decimal-function-calls) - 小数を文字列に変換します。

## 4 続きを読む

* [マイクロフロー](マイクロフロー)
* [ワークフロー](workflows)
* [Set & Change a value for different activities in the Microflow](microflows-setting-and-changing-value)
* [式](/refguide/expressions)
