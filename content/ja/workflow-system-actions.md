---
title: "システムアクション"
category: "ワークフロー"
menu_order: 40
tags:
  - "ワークフロー"
  - "ワークフロー"
  - "マイクロフローを呼び出します。"
---

## 1つの紹介

ワークフロー内のシステムアクションは、選択した **microflow** を呼び出すために使用される [microflow](microflows) アクションで構成されています。

![](attachments/workflows-system-actions/call-microflow-example.jpg)

## 2 マイクロフローのプロパティを呼び出します。

以下の図に、 **Call microflow** プロパティの例を示します。

![マイクロフローのプロパティを呼び出す](attachments/workflows-system-actions/call-microflow-properties.jpg)

コールマイクロフローのプロパティは以下のセクションで構成されています:

* [全般](#general)
* [パラメータ](#parameters)
* [成果](#outcomes)

### 2.1 一般セクション {#general}

**一般** セクションでは、アクションのキャプションを定義したり、マイクロフローを選択したりできます。

セクションプロパティは以下の表に記載されています。

| 属性      | 説明                                                                      |
| ------- | ----------------------------------------------------------------------- |
| 図表番号    | **図表番号** では、この要素で何が起こるかを説明します。 ワークフローエディタに表示され、ワークフローの読みやすさと理解が容易になります。 |
| マイクロフロー | この要素によって呼び出されるマイクロフロー。                                                  |

### 2.3 パラメーターセクション {#parameters}

パラメータは要素にデータを渡します。 現在、パラメータはStudio Proでのみ選択および設定できます。 詳細については、 [Microflow](/refguide/call-microflow) を参照してください。

### 2.2 アウトカムセクション {#outcomes}

**結果** は、マイクロフローの戻り値に依存する。 例えば、Booleanの場合、 **true** と **false** の結果があります。 while the enumeration – 各enumeration valueごとの結果と、値が未割り当ての場合の空の値です。

## 3 続きを読む

* [一般的な活動](workflows-general-activities)