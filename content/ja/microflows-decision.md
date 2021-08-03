---
title: "決定"
category: "マイクロフロー"
menu_order: 20
description: "Mendix Studioで決定を説明します。"
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "排他的分割"
  - "決定"
---

## 1つの紹介

このドキュメントでは、Mendix Studio の **決定** について説明します。

意思決定は、条件に基づく要素であり、それは、発信の流れの1つに過ぎません。 たとえば、異なる成績を持つ顧客に対して異なる注文フォームを表示するには、決定を使用する必要があります。 ブロックされた顧客が注文するのを防ぐためです

## 2つの条件 {#condition}

判断に条件を設定するには2つの方法があります:

* [ **変数/属性**](#variables-attributes-tab) (例えば、列挙型の属性に異なるフローを作成するために使用できます)
*  [ **式**](#expression-tab) を使用する (たとえば、それと比較を作成することができます)

   ![](attachments/microflows-decision/configure-condition-dialog.png)

### 2.1 変数または属性を使用した条件の設定 {#variables-attributes-tab}

**変数/属性** タブでは、以下の要素を決定条件として使用できます。

* ブール型のデータ型変数
* 列挙型データ型の変数
* ブール型の属性
* 列挙型の属性

{{% alert type="info" %}}

決定の条件を設定する際に使用したいパラメータとエンティティは、microflowに存在する必要があります。 入力パラメータとしてか、アクティビティの結果としてか。

{{% /alert %}}

### 2.2 式による条件の設定 {#expression-tab}

式を書くことで条件を設定することもできます。 式の記述方法の詳細については、 [Microflow Expressions](microflows-expressions) を参照してください。

## 3件のケース

**ケース** は発信フローの数を定義し、選択された [条件](#condition) に依存します。

パラメータまたは属性の Boolean 型では、2 つのフローが可能です: **true** と **false**。

![](attachments/microflows-decision/decision-boolean.png)

列挙型で使用可能なケースの数は、対応する列挙値によって異なります。 There is also the *empty* case available for enumeration: if the enumeration parameter or an attribute of an object is unassigned, the sequence flow with the caption **(empty)** is followed.

たとえば、エンドユーザーが顧客の成績を選択する必要がありますが、そうしない場合。 **(空)** とラベル付けされたフローがフォローされ、エンドユーザーにエラーメッセージが表示されます。

![](attachments/microflows-decision/decision-enumeration.png)

## 4つの図表番号

キャプションは、この要素で何が起こるかを説明します。

## 5 続きを読む

* [マイクロフロー](マイクロフロー)
* [マイクロフロー式](microflows-expressions)
* [決定を設定する](/studio-how-to/microflows-how-to-configure-decision) 

