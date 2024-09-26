---
title: "Java アクションコール"
parent: "action-call-activity"
menu_order: 10
tags:
  - "studio pro"
  - "Java"
  - "javaアクションコール"
  - "アクション通話"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/java-action-call.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

**Java アクションコール** アクティビティは、 [Java アクション](java-actions) を呼び出すために使用できます。

{{% image_container width="200" %}}

![Java アクション](attachments/action-call-activities/java-action-call.png)

{{% /image_container %}}

引数はアクションに渡すことができ、結果を保存することができます。

## 2つのプロパティ

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

![Javaアクションコールプロパティ](attachments/action-call-activities/java-action-call-properties.png)

**Java アクションコール** プロパティペインは以下のセクションで構成されています。

* [アクション](#action)
* [一般的な](#common)

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 Java アクション

このアクティビティによって呼び出されるJavaアクション。

### 3.2 引数

引数を入力するには、パラメータの横にある **** をクリックします。

引数は、Java アクションに渡す入力データです。 Javaアクションパラメータごとに、同じ型の引数を指定する必要があります。

引数の値は [式](expressions) を使用して定義されます:

![引数](attachments/action-call-activities/argument-edit.png)

### 3.3 戻り値の種類

この読み取り専用プロパティは、変数、オブジェクト、またはリストを取得するかどうかを示します。 戻り値の型は Java アクションによって定義されます。

### 3.4 戻り値を使用

**User return value** が *Yes* に設定されている場合、返り値に名前を付けるように求められます。

### 3.5 変数名、オブジェクト名、またはリスト名

Javaアクションの結果には、この名前が与えられます。 ラベルは、結果が変数、オブジェクト、またはリストであるかどうかを示します。 オブジェクトまたはリストの場合、 **Return type** は、返されるエンティティを示します。

## 4つの共通セクション {#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}