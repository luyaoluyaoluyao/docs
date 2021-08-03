---
title: "JavaScript アクションコール"
parent: "action-call-activity"
menu_order: 20
description: "この参照では、JavaScript アクション呼び出しアクティビティのプロパティを説明します。"
tags:
  - "javascript"
  - "return"
  - "変数"
  - "studio pro"
  - "アクション通話"
---

{{% alert type="warning" %}}
このアクティビティは **Nanoflows** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

JavaScriptアクションコールアクティビティは、 [JavaScriptアクション](javascript-actions)を呼び出すために使用できます。 引数はアクションに渡すことができ、結果を保存することができます。

{{% image_container width="200" %}}
![javascriptアクションコールプロパティ](attachments/action-call-activities/javascript-call.png)
{{% /image_container %}}

## 2つのプロパティ

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

![JavaScriptアクションプロパティ](attachments/action-call-activities/javascript-action-call.png)

**JavaScript アクション コール** プロパティ ペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 JavaScript アクション

このプロパティは、アクティビティによって呼び出された JavaScript アクションを設定します。

### 3.2 パラメータ

選択したJavaScriptアクションに応じて、パラメータのリストが表示されます。 パラメータはアクティビティにデータを渡します。

#### 3.2.1 引数

引数を入力するには、パラメータの横にある **** をクリックします。

引数は、JavaScript アクションに渡す入力データです。 JavaScript アクションパラメータごとに、同じ型の引数を指定する必要があります。

引数の値は [式](expressions) を使用して定義されます:

![引数](attachments/action-call-activities/argument-edit.png)

### 3.3 戻り値の種類 {#return-type}

この読み取り専用プロパティは、変数、オブジェクト、またはリストを取得するかどうかを示します。 戻り値の型は JavaScript アクションによって定義されます。

### 3.4 戻り値を使用

このプロパティは、JavaScriptアクションから返される値を、マイクロフローの残りの部分またはnanoflowで利用できるかどうかを決定します。 If **Use return value** is set to *Yes*, you will need to fill in the [name](#name) of the variable, object, or list returned by the activity.

### 3.5 変数名、オブジェクト名、またはリスト名 {#name}

アクティビティによって返される変数、リスト、またはオブジェクトの名前。 オブジェクトまたはリストの場合、 [Return type](#return-type) は、返されるエンティティを示します。

## 4つの共通セクション {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 続きを読む

* [JavaScript アクション](javascript-actions)
* [JavaScriptアクションをビルド](/howto/extensibility/build-javascript-actions)
* [Nanoflows](ナノフロー)
* [Java アクションコール](java-action-call)
