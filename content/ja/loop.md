---
title: "ループ"
parent: "マイクロフローとナノフロー"
menu_order: 80
tags:
  - "studio pro"
  - "ループ"
  - "繰り返します。"
  - "各"
  - "中に"
---

## 1つの紹介

ループは繰り返されたアクションを実行するために使用され、フレームとして視覚化されます。 繰り返しごとに、ループ内のフローが実行されます。 ループは、リスト上で反復するか、ブール式に基づいて設定できます。 詳細については、 [Loop Type プロパティ](#loop-type) を参照してください。

ループには、 [開始イベント](start-event) と [終了イベント](end-event) を除き、マイクロフローで使用されるすべての種類の要素を含めることができます。 ループのみが [ブレークイベント](break-event) と [継続イベント](continue-event)を含めることができます。

## 2 Loop Type プロパティ {#loop-type}

以下に、2 つのループタイプについて説明します。

### 2.1 各 (リスト内の項目) {#for-each}

これは、新しいループ・アクティビティを作成するときのデフォルトのタイプであり、オブジェクトのリストを繰り返すために使用できます。 リストは、 **** プロパティをフロースコープ内のリストに設定することで構成できます。 リスト内の各オブジェクトに対して、ループ内のフローが実行されます。 イテレータ(パラメータと同じように見えます)は、各イテレーションのリスト内の現在のオブジェクトを表します。 そして、 **Loop object name** を設定することで名前を変更できます。 このオブジェクトは黒で、オブジェクトのエンティティタイプは青で表示されます。

![](attachments/loop/foreach-loop-edit-form.png)

例えば、 If you have a list of objects of the **OrderLine** entity and you want to set the purchase date for every object 購入日を設定する変更アクティビティを含むループを使用できます。

![](attachments/loop/foreach-loop.png)

### 2.1 While (Condition Is True) {#while}

このループ型は、ある条件が `false` と評価されるまで、ループ内のフローを何度も繰り返します。 この条件は、ループ本体の実行の前に評価されます。 通常、 **While** ループは、事前に繰り返しの正確な数を決定することができない場合に使用されます。

**図表番号** フィールドを設定することで、ループまたは条件の説明を指定できます。 ループ条件は [式](expressions) エディタで **式** として入力することができ、ブール値を返す必要があります。 **キーワード** は青で表示され、 **図表番号** は黒で下に表示されます。

![](attachments/loop/while-loop-edit-form.png)

For example, if you want to [log](log-message) numbers between 1 and 5, you can use a loop with a condition that checks whether a **Counter** [variable](variable-activities) is less than or equal to 5. ループの中に **Counter** の値を記録し、 **Counter** 変数に 1 を追加して、ループが **Counter** が5より大きいときに実行を停止するようにします。

![](attachments/loop/while-loop.png)
