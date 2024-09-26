---
title: "Nanoflowに発信"
parent: "client-activities"
menu_order: 2
tags:
  - "studio pro"
  - "ナノフロー・コール"
  - "nanoflowを呼べ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/nanoflow-call.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

{{% alert type="warning" %}}
このアクティビティは **Nanoflows** でのみ使用できます。
{{% /alert %}}

**nanoflow** 活性は、別の [nanoflow](nanoflows) を呼び出すために使用することができる。

{{% image_container width="200" %}}
![Nanoflow Call](attachments/action-call-activities/nanoflow-call.png)
{{% /image_container %}}

引数はnanoflowに渡すことができ、その結果を変数に格納することができます。

## 2つのプロパティ

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

![Nanoflow 呼び出しプロパティ](attachments/action-call-activities/nanoflow-call-properties.png)

**Nanoflow calls** プロパティ ペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 Nanoflow

この活動によって呼び出されるナノフロー。

### 3.2 パラメータ

選択したマイクロフローに応じて、テーブルにパラメーターのリストが表示されます。 パラメータはアクティビティにデータを渡します。

#### 3.2.1 名前

読み取り専用のパラメータ名です。

#### 3.2.2 タイプ

読み取り専用のパラメータのタイプ。 パラメータの型についての詳細は、 [Data Types](data-types) を参照してください。

#### 3.2.3 引数 {#argument}

**パラメータ値** を編集ボタンで、引数の値を編集できます。 nanoflowの各パラメータについては、同じ型の引数を指定する必要があります。 引数の値は [式](expressions) を使用して表されます。

### 3.3 戻り値の種類

この読み取り専用プロパティは、変数、オブジェクト、またはリストを取得するかどうかを示します。

### 3.4 戻り値を使用

このプロパティは、現在の nanoflow の残りの部分で nanoflow と呼ばれる値を使用できるかどうかを決定します。 If **Use return value** is set to *Yes*, you will need to fill in the [name](#name) of the variable, object, or list returned by the activity.

### 3.5 変数名、オブジェクト名、またはリスト名 {#name}

アクティビティによって返される変数、リスト、またはオブジェクトの名前。

## 4つの共通セクション {#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}