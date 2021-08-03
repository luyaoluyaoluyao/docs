---
title: "マイクロフロー式"
category: "マイクロフロー"
menu_order: 40
description: "Mendix Studio で利用可能なマイクロフロー式について説明します。"
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "値を設定"
  - "変数"
---

## 1つの紹介

このドキュメントでは、Mendix Studio でのマイクロフロー式について説明します。 式は、ロジックに基づいてオブジェクトや変数を作成または変更するために使用できます。

**式** タブは、以下のような活動に対応しています。

*  [イベントを終了](/refguide/end-event)
*  [決定](microflows-decision)
*  [オブジェクトを作成](/refguide/create-object)
*  [オブジェクトの変更](/refguide/change-object)
*  [変数を作成](/refguide/create-variable)
*  [変数の変更](/refguide/change-variable)

![](attachments/microflows-expressions/expression-tab.png)

マイクロフローアクティビティの設定と値の変更の詳細については、 see [How to Set & Change a Value for different Activities in the Microflows](microflows-setting-and-changing-value).

## 2 式を書く

式を書くには2つの方法があります。

* 候補の使用
* 式を手動で書く

式にエラーが表示されると、説明のヒントが表示されます。

{{% image_container width="350" %}}![](attachments/microflows-expressions/expression-error.png)
{{% /image_container %}}

### 2.1 提案を使って式を書く

式を入力し始めると、次のカテゴリに分けられた候補の一覧が表示されます:

* **マイクロフローからの提案** – マイクロフローで作成または取得した変数または属性
* **列挙値** - 式で使用できる [列挙タイプ](domain-models-enumeration) の値
* **キーワード** - 表現で使用できるキーフレーズまたは単語
* **Boolean** – true または false の表現
* **演算子** – 論理演算または数学演算を実行するコード要素。 ブール式またはリレーショナル式を使用できます (詳細については、 [式タイプ](#expression-types) セクションを参照してください)

![](attachments/microflows-expressions/expressions-list.png)

提案を使用して式を書くには、次の操作を行います:

1. 候補のリストを参照し、マウスまたはキーボードを使用して式の要素を選択します。
2. リストから要素を選択します。
4. 式が完了したら、 **Add** をクリックします。

{{% alert type="info" %}}

候補の一覧を呼び出すには、 <kbd>Ctrl</kbd> + <kbd>スペース</kbd> を押します

{{% /alert %}}

### 2.2 手動で式を書く

手動で表現を記述したい場合は、次の点に注意してください。

* マイクロフロー内の変数は、ドル記号と変数の名前を挿入することで、式内で呼び出すことができます。 例えば、 *$Customer* は変数 *を参照します顧客*
* オブジェクト変数の属性と関連付けはスラッシュを使用してアクセスします。 例えば、 *$Customer/Name*, *$Customer/Grade* エンティティの名前とグレードを参照します
* Studio では、Unary、Boolean、およびリレーショナル型の式が使用できます (詳細については、 [式タイプ](#expression-types) セクションを参照してください)

## 3 式の例

以下に、式の使用方法を示す2つの例を示します。

### 3.1 例 1

**[Decision](microflows-decision)** があり、顧客の成績が金であり、注文の価格が100を超えているかどうかをチェックする式を書く必要があります (この式がtrueの場合に許可される **Decision** の後に割引を設定できます):

![](attachments/microflows-expressions/example-decision.png)

式は次のようになります:

![](attachments/microflows-expressions/expression-decision.png)

### 3.2 例 2

**[Decision](microflows-decision)** を追加して、オブジェクトが存在するかどうかを確認します(以下の例では、オブジェクト *Customer*です)。 また、お客様の名前が特定の名前と一致するかどうかも確認します(下の例では、お客様の名前は *Mendix* です)。 式は次のようになります:

![](attachments/microflows-expressions/customer-empty-and-name-example.png)

## 4 式のタイプ {#expression-types}

Studio で式で使用できる演算子のリストは以下のとおりです。

### 4.1 リレーショナル表現

* [より小さい ( <)](/refguide/relational-expressions)
* [( > ) より大きい](/refguide/relational-expressions)
* [以上 ( <= )](/refguide/relational-expressions)
* [以上 ( >= )](/refguide/relational-expressions)
* [( = ) と等しいです](/refguide/relational-expressions)
* [等しくない ( != )](/refguide/relational-expressions)

### 4.2 ブール式

* [と](/refguide/boolean-expressions)
* [または](/refguide/boolean-expressions)

## 5 続きを読む

* [マイクロフロー](マイクロフロー)
* [Set & Change a value for different activities in the Microflow](microflows-setting-and-changing-value)
