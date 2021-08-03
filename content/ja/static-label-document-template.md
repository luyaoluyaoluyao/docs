---
title: "スタティックラベル（ドキュメントテンプレート）"
parent: "ドキュメントテンプレート"
aliases:
  - /refguide7/Static+label+(document+template).html
  - /refguide7/static-label-(document-template).html
---


静的ラベルには、静的テキストの行が表示されます。 これを使用して、データビュー、テンプレートグリッド、またはテーブル内にカスタムテキストを配置できます。

{{% alert type="info" %}}

![](attachments/819203/918130.png)] テキスト「顧客名」のラベル。

{{% /alert %}}

ドキュメントに現在のページ番号または合計ページ数を挿入する場合。 静的ラベル内(および静的ラベル内のみ)でトークンを使用できます。 バージョン 2.5.4 以前は、スペースは自動的にトークンの両側に挿入されていました。 これはもはやケースではありません。

{{% alert type="info" %}}

Static label content: Page [%pageNumber%] of [%totalPageCount%] Will print: Page 2 of 4

{{% /alert %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

## 外観のプロパティ

### 図表番号

これはドキュメントに表示される値です。

### スタイル

[スタイル](style) を参照
