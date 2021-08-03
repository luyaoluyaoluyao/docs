---
title: "編集ボタン"
parent: "コントロール バー"
---

{{% alert type="info" %}}

このボタンは Mendix 7.17 で削除されました。 [ページの](action-button) を代わりに表示する **アクションボタン** を使用します。

{{% /alert %}}

編集ボタンを使用すると、グリッドまたは参照セットセレクタで選択したオブジェクトを編集または表示できます。

## 共通のプロパティ

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 一般プロパティ

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+button+Property.md" %}}

### ページ

このプロパティは、エンドエンドエンドユーザーがこのボタンをクリックしたときに表示されるページを示します。 エンドユーザーは、このページを使用して選択したオブジェクトを編集できます。 このページには、グリッドと同じ図形に接続されたデータビュー、または参照セットセレクタが含まれている必要があります。

[ページを開く](opening-pages) を参照してください。

### 専門分野のページ

グリッドまたは参照セットセレクターに接続されているエンティティに特殊化がある場合は、オプションで各特殊化のページを指定できます。 データ グリッドで行を編集すると、最も特定のページが開きます。 専門分野ごとに、開くページと開くページのタイトルを指定します。

{{% alert type="info" %}}

私たちは、エンティティを持っていると言いましょう 車とその2つの専門分野:自転車と車。 そしてSportsCarと呼ばれる車の専門化があります。 車両に接続されたデータグリッドを作成します。 データ グリッドの page プロパティで、任意の車両に対して開くページを指定します。 自転車と車の専門用には、それらを編集するための別々のページを作成します。 自転車タイプの行を編集すると、自転車専用のページが開きます。 車を編集すると、車のページが表示されます。 スポーツカーを編集すると、車のページが開きます! スポーツカーに特有のページはありません(この例では)し、車はページがある「最も近い」一般化です。

{{% /alert %}}

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Extended.md" %}}
