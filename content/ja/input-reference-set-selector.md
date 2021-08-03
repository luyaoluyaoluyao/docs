---
title: "入力リファレンスセットセレクター"
parent: "input-widgets"
menu_order: 90
tags:
  - "studio pro"
---

{{% alert type="warning" %}}The **input reference set selector** ウィジェットはネイティブのモバイルページではサポートされていません。{{% /alert %}}

## 1つの紹介

**入力参照集合セレクタ** は、関連するオブジェクトを選択することによって、エンドユーザーが多対多の(参照集合) [関連](associations) の値を表示または選択できるようにするために使用されます。

入力リファレンスセットセレクタは、 [データ ウィジェット](data-widgets) に配置する必要があります。

たとえば、顧客をグループにグループ化でき、各顧客は複数のグループに属することができます。 各グループには多くの顧客がいます。 エンティティ **顧客** と **グループ** は多対多の関係を持っている (参照セット) 。 入力リファレンスセットセレクタを使用して、顧客が属するグループを選択できます。

入力リファレンスセットセレクタでできることは、アソシエーションの **オーナー** に依存します。 以下のドメインモデルの例 **所有者** は **デフォルト** に設定されています (関連プロパティ **'顧客' オブジェクトは 'グループ' オブジェクト** を参照します)。

![顧客（親）とグループの間の入力参照セットセレクタのドメインモデル (オーナーが「デフォルト」の場合と同様) 顧客はグループを参照しています)](attachments/input-reference-set-selector/domain-model-owner-default.png)

顧客データビューに入力参照セットセレクタを入れることで、ユーザーが顧客が属するグループを選択できるようになります。 ただし、お客様が協会の所有者であるため、 グループ内の顧客を選択するには、format@@0ビューに入力参照セットセレクタを入れることはできません。

顧客にグループを追加し、顧客をグループに追加できるようにする。 あなたは、関連付けの所有権を **** に設定する必要があります。

![オーナーが「両方」である顧客（親）とグループ間の入力参照セットセレクタのドメインモデル 顧客とグループが互いを参照します)](attachments/input-reference-set-selector/domain-model-owner-both.png)

入力参照セットセレクタでは、表示される属性へのパス (関連付け、関連エンティティ) 属性)は、入力参照セットセレクタ内に表示され、角括弧と青色の間で表示されます。

たとえば、上記のドメインモデルを使用します。 以下の入力参照セットセレクタは、関連付け **Customer_Group**を設定することによって、エンドユーザーが1つ以上のグループと顧客を関連付けることを可能にします。 これは、現在の **顧客**に関連付けられている **グループ**の **名**を選択することによって行われます。

![](attachments/input-reference-set-selector/input-reference-set-selector.png)

## 2つのプロパティ

以下の画像では、入力参照セットセレクタプロパティの例を示します。

{{% image_container width="250" %}}![](attachments/input-reference-set-selector/input-reference-set-selector-properties.png)
{{% /image_container %}}

参照集合セレクタープロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [データソース](#data-source)
* [デザインプロパティ](#design-properties)
* [編集可能](#editability)
* [イベント](#events)
* [全般](#general)
* [ラベル](#label)
* [選択可能なオブジェクト](#selectable-objects)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 データソースセクション {#data-source}

{{% snippet file="refguide/data-source-section-link.md" %}}

属性パスは、関連するエンティティのどの属性を参照セットセレクタに表示するかを指定します。 パスは、データビューのエンティティから始まるタイプ参照セットの関連付けに従う必要があります。

### 2.3 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide/design-section-link.md" %}}

### 2.4 編集可能セクション {#editability}

{{% snippet file="refguide/editability-section-link.md" %}}

### 2.5 イベントセクション {#events}

on-change プロパティは、ウィジェットを離れたときに実行されるアクションを指定します。 <kbd>Tab</kbd> キーを使用するか、値が変更された後に別のウィジェットをクリックします。

{{% snippet file="refguide/events-section-link.md" %}}

### 2.6 一般プロパティ {#general}

#### 2.6.1 ページを選択

format@@0 プロパティにより、入力リファレンスセレクターがクリックされたときに表示されるページが決定されます。 このページは、選択可能なオブジェクトのリストから関連するオブジェクトを選択するために使用できます。 このページには、入力参照セットセレクタと同じエンティティに接続されたデータグリッド、テンプレートグリッド、またはリストビューが含まれている必要があります。

入力参照セットセレクタが編集できない場合、選択ページは必要ありません。

[Show a Page](on-click-event#show-page) section of *On Click Event & Events Section* を参照してください。 選択ページには [ポップアップ レイアウト](layout#layout-type) が必要です。

{{% alert type="info" %}}
ウィジェットを右クリックして **選択ページを生成…** を選択することで、新しいページを表示することができます。
{{% /alert %}}

### 2.7 ラベルセクション {#label}

{{% snippet file="refguide/label-section-link.md" %}}

### 2.8 選択可能なオブジェクトセクション {#selectable-objects}

format@@0 セクションのプロパティによって、エンドユーザーが選択できるオブジェクトが決定されます。 ソースとして、 **データベース** または **XPath** を使用することができます。 **XPath**を使用する場合、 **XPath 制約**を追加するか、 **** パスを使用することができます。

詳細に関しては、 [参照セレクター](reference-selector#xpath-constraints) の *XPath* セクションを参照してください。

{{% alert type="info" %}}
入力リファレンスセットセレクタ内で選択可能なオブジェクトを定義するためにマイクロフローを使用することはできません。
{{% /alert %}}

### 2.9 表示セクション {#visibility}

{{% snippet file="refguide/visibility-section-link.md" %}}
