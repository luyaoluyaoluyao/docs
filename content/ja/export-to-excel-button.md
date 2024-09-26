---
title: "Excelボタンにエクスポート"
parent: "コントロール バー"
---


このボタンを使用すると、エンドユーザーはグリッドまたは参照セットセレクタの内容をExcelファイルにエクスポートできます。 検索フィールドやソートによる制約もエクスポートされますのでご注意ください。

excel エクスポート関数は、特定のデータ検索メソッドに依存します。 このため、XPath データソースを使用するリストウィジェットでのみ使用することができます。

## 共通のプロパティ

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 一般プロパティ

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+button+Property.md" %}}

### 行の最大数

エクスポート時にデータグリッドに存在できる行の最大数を示します。 ユーザーが大量のデータをエクスポートするのを防ぐのに役立ちます。サーバーに負荷がかかる可能性があります。

### 日付のエクスポート形式

日付をエクスポートする方法を定義します。 _日付値_ を選択すると、日付値が実際の日付としてエクスポートされます。 Excel日付関数を並べ替えなど使用できるようにします。 _テキスト_ を選択すると、日付値はデータ グリッドに表示される通りにエクスポートされます。

_デフォルト値:_ 日付値

{{% alert type="warning" %}}

_日付値_を選択すると、日付はWindowsアカウントのタイムゾーンにのみ表示されます。 Excelは特定のタイムゾーンの定義をサポートしていないためです。

{{% /alert %}}

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}
