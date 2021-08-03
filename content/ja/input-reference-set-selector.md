---
title: "入力リファレンスセットセレクター"
parent: "input-widgets"
---


入力参照セットセレクタは [入力ウィジェット](input-widgets) であり、複数の親オブジェクトが複数の子要素に関連付けられるように多重度設定が構成されている [関連付け](associations) を表示および編集するために使用できます。 このタイプの関連付けは、参照セットとも呼ばれます。

{{% alert type="info" %}}

![](attachments/16713883/16844008.jpg) 関連の多重度設定は、 [ドメイン モデル](domain-model) 内の関連付けをダブルクリックすることで確認できます。

{{% /alert %}}{{% alert type="info" %}}

![](attachments/pages/input-reference-set-selector.png) この入力リファレンスセットセレクターでは、従業員を組織にリンクすることができます。

{{% /alert %}}

クリック時 入力参照セットセレクタは、関連付けを埋めるために使用できるすべての可能なオブジェクトを含むウィジェットを含むセレクトページを開きます。

## 一般プロパティ

### ページを選択

select ページは、入力リファレンスセレクターがクリックされたときに表示されるページを決定します。 このページは、可能なすべてのオブジェクトのリストから関連するオブジェクトを選択するために使用できます。 このページには、入力参照セットセレクタと同じエンティティに接続されたデータグリッド、テンプレートグリッド、またはリストビューが含まれている必要があります。

どのような状況でも入力参照セットセレクタが編集可能でない場合、select ページは必要ありません。

[ページを開く](opening-pages) を参照してください。 コンテンツ内の選択ページを開くことは禁止されています。

{{% alert type="success" %}}

ウィジェットを右クリックして「選択ページを生成...」を選択すると、新しいページを生成することができます。

{{% /alert %}}

## 選択可能なオブジェクトのプロパティ

### XPath 制約

XPath 制約を使用すると、選択することのできるオブジェクトのリストを制限する手動制約を追加することができます。

{{% alert type="info" %}}

商品の参照セレクタ上の XPath 制約 `[InStock = true()]` は、在庫にある商品のみが選択可能であることを保証します。

{{% /alert %}}

### 制約を受けた人

入力リファレンスセットセレクタは、1つ以上のパスで制約することができます。 これは通常、ある参照セレクタを別のセレクタに依存させるために使用されます。 たとえば、ユーザを編集できるページでは、組織セレクタを国セレクタに制約することができます。 国を選択した後、組織セレクターはこの国によって制約され、その国にリンクされた組織のみが表示されます。

{{% alert type="info" %}}

![](attachments/16713883/16844007.jpg)

ドメインモデルでは、ユーザーは国への参照関連、組織への参照セット関連があります。 第三の協会は、国から組織まで、両者の関係を説明しています。 このような「三角形」の領域モデルの一部が制約を可能にするものである。

![](attachments/16713883/16844006.jpg)

ページには国への参照用の参照セレクタとOrganizationへの参照セット用の入力参照セットセレクタが表示されています。 後者は、三角形を形成するドメインモデルを通るパスによって制約されます。

![](attachments/16713883/16844005.jpg)

{{% /alert %}}

## データソースのプロパティ

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Label+Property.md" %}}

## 編集可能なプロパティ

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## イベントのプロパティ

{{% snippet file="refguide7/On+Change+Event.md" %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 続きを読む

*   [データビュー](data-view)
