---
title: "スタティックラベル（ドキュメントテンプレート）"
parent: "ドキュメントテンプレート"
tags:
  - "studio pro"
aliases:
  - /ja/refguide/Static+label+(document+template).html
  - /ja/refguide/static-label-(document-template).html
---

## 1つの紹介

静的ラベルには、静的テキストの行が表示されます。 これを使用して、データビュー、テンプレートグリッド、またはテーブル内にカスタムテキストを配置できます。

例えば、テキスト「顧客名」のラベルは以下のようになります。

![](attachments/document-templates/918130.png)

ドキュメントに現在のページ番号または合計ページ数を挿入する場合。 静的ラベル内(および静的ラベル内のみ)でトークンを使用できます。

例えば、静的なラベルコンテンツ `ページ [%pageNumber%] の [%totalPageCount%]` は、 **ページ 2 の 4** を出力します。

## 2つの一般的なプロパティ

{{% snippet file="refguide/name-property.md" %}}

## 3つの外観プロパティ

### 3.1 図表番号

これはドキュメントに表示される値です。

### 3.2 スタイル

詳細は [スタイル](style) を参照してください。
