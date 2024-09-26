---
title: "すべてのボタンを選択"
parent: "コントロール バー"
---

format@@0 ボタンをクリックすると、エンドユーザーはグリッド内のすべてのオブジェクト、または参照セットセレクターを選択できます。 format@@0 プロパティを使用すると、このボタンが現在のページのオブジェクトを選択するか、すべてのページのオブジェクトを選択するかを指定できます。

## 共通のプロパティ

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 一般プロパティ

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+button+Property.md" %}}

### 選択タイプ

| 値      | 説明                                       |
| ------ | ---------------------------------------- |
| ページを選択 | このボタンをクリックすると、現在のページ上のすべてのオブジェクトが選択されます。 |
| すべて選択  | このボタンをクリックするとすべてのオブジェクトが選択されます。          |

{{% alert type="warning" %}}

技術的な制限により、選択タイプの「すべて選択」ボタンを削除、削除、または選択ボタンと組み合わせることはできません。 format@@0 ボタンは、選択タイプが "Select page" のように常に動作します。 オブジェクトを選択するために使用されていた「すべて選択」ボタンの実際の設定に関係なく。

{{% /alert %}}

_デフォルト値:_ ページを選択

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}
