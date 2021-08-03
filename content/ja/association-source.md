---
title: "関連ソース"
parent: "データソース"
---


The association source is a data source available to nested [data grids](data-grid), [template grids](template-grid), and [list views](list-view). これにより、関連付け方法で既にコンテキスト内のオブジェクトにリンクされているオブジェクトがウィジェットに表示されます。 これを機能させるには、そのコンテキストを提供するために、データ ウィジェットを別のデータ ウィジェット内にネストする必要があります。

Data widgets that can function as a container for other data widgets are the [template grid](template-grid), [list view](list-view), and [data view](data-view).

{{% alert type="warning" %}}

関連データソースを持つデータ ウィジェットでは列の並べ替えや検索はできません。 これらの機能は、関連データソースが必ずしも起動しない、関数へのデータベース呼び出しを必要とするためです。

{{% /alert %}}

## プロパティー

### エンティティ (パス)

エンティティ (path) プロパティは、ウィジェットが生成される関連付けを指定します。 ウィジェットに表示される唯一のオブジェクトは、選択された関連付けの方法で含まれているウィジェット内のオブジェクトにリンクされているオブジェクトです。
