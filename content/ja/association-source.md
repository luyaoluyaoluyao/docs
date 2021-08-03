---
title: "関連ソース"
parent: "データソース"
tags:
  - "studio pro"
  - "関連"
  - "データソース"
menu_order: 60
---

## 1つの紹介

The **Association** source is a data source available to nested [data grids](data-grid), [template grids](template-grid), and [list views](list-view).

{{% alert type="warning" %}}

**アソシエーション** ソースは、データベースからではなくメモリからオブジェクトを取得します。

{{% /alert %}}

**関連付け** データ ソースは、関連付けによって別のオブジェクトにリンクされたオブジェクトでウィジェットを埋めます。 コンテキストを提供するには、データ ウィジェットを別のデータ ウィジェット内にネストする必要があります。

Data widgets that can function as a container for other data widgets are the [template grid](template-grid), [list view](list-view), and [data view](data-view).

{{% alert type="warning" %}}

関連データソースを持つデータ ウィジェットでは列の並べ替えや検索はできません。 これらの機能は、関連データソースが必ずしも起動しない、関数へのデータベース呼び出しを必要とするためです。

{{% /alert %}}

## 2つのプロパティ

### 2.1 エンティティ (パス)

**エンティティ (パス)** プロパティは、ウィジェットが生成される関連を指定します。 ウィジェットには、関連付けによって周囲のデータコンテナのオブジェクトに接続されているオブジェクトのみが表示されます。

## 3 続きを読む

* [関連](関連)
* [データウィジェット](data-widgets)