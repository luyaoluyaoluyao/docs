---
title: "Set & Change a value for different activities in the Microflow"
category: "マイクロフロー"
menu_order: 50
description: "Mendix Studio でオブジェクトまたは変数の初期値を設定するプロセスを説明します。"
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "値を設定"
  - "変数"
---

## 1つの紹介

このドキュメントでは、Mendix Studio のマイクロフローでのさまざまなアクティビティの値の設定と変更方法について説明します。

次のアクティビティのプロパティを設定する場合は、オブジェクト/変数に値を割り当てる必要があります。

* **オブジェクトの作成** - このアクティビティでオブジェクトを作成し、オブジェクトのプロパティの初期値を提供することができます
* **変数の作成** - 変数を作成し、このアクティビティで値を割り当てることができます。

次のアクティビティを設定するときに値を変更することもできます。

* **Change Object** - このオブジェクトの既存のオブジェクトやプロパティを変更するために使用できます
* **Change Variable** - 現在のマイクロフローにおける既存の変数の値を変更する。

また、 **End Event** の戻り値を設定することもできます。これは、マイクロフローが停止する場所です。

これらのアクティビティの機能の詳細については、 [Microflow](microflows) を参照してください。

## 2 オブジェクト作成時の初期値の設定とオブジェクト変更時の値の変更

 初期値を設定したり、オブジェクトの値を変更したりするには、以下を行います:

1. **Create Object**/**Change Object** アクティビティをマイクロフローに追加します。 詳細については、 [Microflow](microflows#adding-activity-to-microflow) の ** のformat@@4 新しいイベントまたはアクティビティの追加</em> セクションを参照してください。
2. アクティビティをクリックして、そのプロパティを表示します。
3.  アクティビティのデータソースを選択し、 **新しい値を追加** をクリックします

    ![](attachments/microflows-setting-and-changing-value/add-new-value.png)

4. **初期値の設定**/**値の変更 ダイアログ**で、属性または関連付けを選択します。
5.  Set the initial value (for **Create Object**) or assign a new value (for **Change Object**) in **Variables/Attributes**, **Constant** or **Expression** tabs.  これらのタブの詳細については、セクション [5 Common Elements](#set-value-common-elements) を参照してください。

    ![](attachments/microflows-setting-and-changing-value/set-initial-value-object-dialog.png)

## 3 変数の初期値の設定と変更値の変更

初期値を設定するか、変数の値を変更するには、以下を行います:

1. **Create Variable**/**Change Variable** アクティビティをマイクロフローに追加します。 詳細については、 [Microflow](microflows#adding-activity-to-microflow) の ** のformat@@4 新しいイベントまたはアクティビティの追加</em> セクションを参照してください。
2. アクティビティをクリックして、そのプロパティを表示します。
3.  アクティビティのデータ型を選択し、 **初期値を設定** / **値を変更** をクリックします

    ![](attachments/microflows-setting-and-changing-value/set-initial-value-var.png)

4.  Set the initial value (for **Create Variable**) or assign a new value (for **Change Variable**) in **Variables / Attributes**, **Constant** or **Expression** tabs.  これらのタブの詳細については、セクション [5 Common Elements](#set-value-common-elements) を参照してください。

    ![](attachments/microflows-setting-and-changing-value/change-value-var-dialog.png)

## 4 終了イベントの戻り値の設定

戻り値は、フローまたは現在のフローを呼び出したウィジェットに返される値です。 戻り値を設定するには、次の手順を実行します。

1. **End Event** をマイクロフローに追加するか、既存の終了イベントを選択します。 詳細については、 [Microflow](microflows#adding-activity-to-microflow) の ** のformat@@4 新しいイベントまたはアクティビティの追加</em> セクションを参照してください。
2. イベントをクリックして、そのプロパティを表示します。
3.  **戻り値** オプションを **値** に設定します。

    ![](attachments/microflows-setting-and-changing-value/end-event-returns-value-setting.png)

4.  データ型を選択し、 **値** をクリックして設定します。

    ![](attachments/microflows-setting-and-changing-value/configure-return-value.png)

5.  戻り値を **変数/属性**、 **定数** または **式** タブに設定します。 詳しい情報については、 [5 つの共通要素](#set-value-common-elements) セクションを参照してください。

    ![](attachments/microflows-setting-and-changing-value/configure-retuen-value-dialog.png)

## 5つの一般的な要素 {#set-value-common-elements}

値を設定する際に、以下の一般的な要素が表示されます。

* **変数/属性** タブ
* **定数** タブ
* **式** タブ

これらのタブの機能は以下の表で説明されています。

| Tab   | 説明                                                                                                                                                                                                                                                                                                                                                                                              |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 変数/属性 | 作成または変更したい属性、関連付け、または変数のタイプに一致する変数と属性を表示します。 <br />例えば、10 進数型の属性を選択すると、10 進数型と整数型の変数がタブに表示されます。 これは、decimal が整数(整数)を含めることができるためです。 ただし、Integer型の属性を選択すると、10進数型の変数は表示されません。 整数は小数を含むことができないためです。  For more information on attribute types, see [Attribute Types](domain-models-attributes).<br />**Note** The attribute of the type Long will be shown as Integer in the microflows. |
| 定数    | このタブでは、列挙型の属性の値から選択する新しい値を割り当てることができます。                                                                                                                                                                                                                                                                                                                                                         |
| 式     | このタブでは、式で記述する内容に応じて、属性、関連付け、または変数の異なる値を割り当てることができます。 詳細については、 [Microflow Expressions](microflows-expressions) を参照してください。                                                                                                                                                                                                                                                                        |

## 6もっと読む

* [マイクロフロー](マイクロフロー)
* [マイクロフロー式](microflows-expressions)
