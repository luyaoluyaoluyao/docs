---
title: "ドロップダウン検索フィールド"
parent: "検索バー"
---

## 共通のプロパティ

{{% snippet file="refguide7/Search+Field+Caption+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Type+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Default+Value+Property.md" %}}

## 一般プロパティ

{{% snippet file="refguide7/Search+Field+Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Search+Field+Comparison+Property.md" %}}

ドロップダウンの選択オプションの数は 1,000 に上限されます。 したがって、選択された属性の一意な値は 1000 を超えることはできません。 この制限は、これらのオプションがサーバーから取得される必要がある場合、古いブラウザでのページの読み込みパフォーマンスを保護するように設定されています。 Mendix 8 では、この制限は削除されました。

### 複数選択を許可

このプロパティが「はい」に設定されている場合、結果のドロップダウンでは1つではなく複数の値を選択できます。 すべてのレコードを検索すると、対応する属性が選択された値のいずれかに一致します。 たとえば、「送信済み」または「処理中」のすべての注文を検索できます。

### XPath 制約

'drop-down' 検索フィールドが(グリッドエンティティ自体ではなく)関連するエンティティの属性に接続されている場合、ドロップダウンに表示されるオブジェクトを制限するために XPath 制約を使用することができます。

{{% alert type="info" %}}

自転車を示すグリッドがあるとしましょう。 ドメインモデルでは、自転車が買えるお店との関連があります。 検索フィールドをグリッドに追加して、エンドユーザーがショップ名で選択できるようにできます。 XPath を使用すると、特定の国にあるショップを限定することができます。 `[MyWebshop.Bicycle_Shop/MyWebshop.Shop/Country='Netherlands']`

{{% /alert %}}

### 並び順

並べ替え順序は、ドロップダウン検索フィールドの項目を表示する順序を指定します。 複数の属性を並べ替えることができます (昇順と降順)。 ソート順が指定されていない場合、ドロップダウンの検索項目が表示される属性をソートします。

_デフォルト値:_ ソート順なし
