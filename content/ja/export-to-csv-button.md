---
title: "CSVボタンにエクスポート"
parent: "コントロール バー"
---


このボタンを使用すると、グリッドまたは参照セットセレクタの内容を CSV ファイルにエクスポートできます。 検索フィールドやソートによる制約もエクスポートされますのでご注意ください。

csv export 関数は、特定のデータ検索メソッドに依存します。 このため、XPath データソースを使用するリストウィジェットでのみ使用することができます。

## 共通のプロパティ

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 書式設定

### 小数点記号

文字列は、Float、Currency、Decimal 値の一部全体から分数部分を分離するために使用されます。

_デフォルト値:_.

### グループセパレーター

数字のグループを大きな数字で区切るために使用される文字列。

_デフォルト値:_,

### 区切り文字

結果のCSVファイルの値を区切るために使用される文字列。

_デフォルト値:_;

## 一般プロパティ

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

{{% snippet file="refguide7/Is+default+button+Property.md" %}}

### 行の最大数

エクスポート時にデータグリッドに存在できる行の最大数を示します。 ユーザーが大量のデータをエクスポートするのを防ぐのに役立ちます。サーバーに負荷がかかる可能性があります。

### Excel区切りヒントを生成

true の場合、CSV ファイルのヘッダーに行を追加し、区切り文字が何であるかを Excel に通知します。 これにより、Excelやローカライゼーションとの互換性の問題が解決されます。

### グリッドの日付フォーマットを使用

true の場合、列の日付書式が使用されます。そうでなければ、Excel が日付として認識する書式が使用されます (yyyy-MM-dd)。

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}
