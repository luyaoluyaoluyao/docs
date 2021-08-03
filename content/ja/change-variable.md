---
title: "変数の変更"
parent: "変数アクティビティ"
tags:
  - "studio pro"
  - "変数の変更"
  - "変数"
  - "可変アクティビティ"
---

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** と **Nanoflows** の両方で使用できます。
{{% /alert %}}

## 1つの紹介

変数を変更すると、既存の変数の値を変更できます。 例えば、特定の商品の50%割引を顧客に提供する *$Discount* 変数がある場合。 この変数を変更して、新しい値を割り当てることができます。 この値を使用して、新しい顧客に大きな割引を与えることができます:

![変数の変更](attachments/variable-activities/change-variable.png)



## 2つのプロパティ

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

![変数のプロパティを変更](attachments/variable-activities/change-variable-properties.png)

**変数の変更** プロパティ ペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3 アクションセクション {#action}

### 3.1 変数

値を変更する変数。

### 3.2 値

変数の新しい値。 [式](expressions) を使用して値を入力します。 式の型は、選択した変数の型と同じでなければなりません。

## 4つの共通セクション {#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}

## 5 続きを読む

* [アクティビティ](アクティビティ)