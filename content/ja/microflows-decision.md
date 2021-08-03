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

意思決定は、条件に基づく要素であり、発信フローの1つだけに従います。 たとえば、異なる成績を持つ顧客に対して異なる注文フォームを表示するには、決定を使用する必要があります。 ブロックされた顧客が注文するのを防ぐためです

## 2つの条件

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

式を書くことで条件を設定することもできます。 詳細については、 [Microflow Expressions](microflows-expressions) を参照してください。

## 3件のケース

利用可能なケースの数は、選択した **条件** によって異なります。

パラメータまたは属性の Boolean 型では、true と false の 2 つの値が使用できます。

![](attachments/microflows-decision/decision-boolean.png)

列挙型で使用可能なケースの数は、対応する列挙定数/値によって異なります。 列挙のために利用可能な空のケースもあります。 オブジェクトの列挙パラメータまたは属性が割り当てられていない場合、キャプション付きのシーケンスフローが続きます (空)。

![](attachments/microflows-decision/decision-enumeration.png)

## 4つの図表番号

キャプションは、この要素で何が起こるかを説明します。

## 5 続きを読む

* [マイクロフロー](マイクロフロー)
* [マイクロフロー式](microflows-expressions)
* [決定を設定する](microflows-how-to-configure-decision) 

