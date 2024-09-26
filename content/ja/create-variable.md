---
title: "変数を作成"
parent: "変数アクティビティ"
tags:
  - "studio pro"
  - "変数を作成"
  - "変数"
  - "可変アクティビティ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/create-variable.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** と **Nanoflows** の両方で使用できます。
{{% /alert %}}

## 1つの紹介

このアクションを使用すると、新しい変数を作成して値を割り当てることができます。 たとえば、 *$Discount* 変数を作成して、値 0 を割り当てることができます。 をクリックして顧客に50%割引を与え、この値を使用して顧客の価格を計算します。

![変数を作成](attachments/variable-activities/create-variable.png)

## 2つのプロパティ

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

![変数のプロパティを作成](attachments/variable-activities/create-variable-properties.png)

**変数の作成** プロパティ ペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3 アクションセクション {#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

### 3.1 データ タイプ

**データ型** は、変数に格納されるデータ型を定義します。 変数は以下の [データ型のいずれかを持つことができます](data-types): ブーリアン、列挙、小数、整数/Long、または文字列。

### 3.2 初期値

変数の初期値を定義します。 値は [式](expressions) を使用して入力されます (マイクロフロー式の結果は変数のデータ型と一致する必要があります)。

### 3.3 変数名

変数は、生成される変数の名前を定義します。 この変数は、フロー内でこのアクティビティに続くすべてのアクティビティで使用できます。

## 4つの共通セクション {#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}

## 5 続きを読む

* [アクティビティ](アクティビティ)