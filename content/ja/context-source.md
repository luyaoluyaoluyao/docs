---
title: "コンテクストソース"
parent: "データソース"
tags:
  - "studio pro"
  - "context"
  - "データソース"
menu_order: 30
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/context-source.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**コンテキスト** ソースはデータビューのデータソースです。 このデータソースを使用したデータビューは、コンテキストからオブジェクトを取得します。これは2つのうちの1つです。

* この場合、データビューまたはリストビューなどの周囲のデータコンテナ **エンティティ (パス)** プロパティは関連付けに従う必要があります
* ページパラメータ – ページパラメータは、ページを開くときにページに渡されるオブジェクトを含みます (パラメータを渡す別のページまたはオブジェクトを渡すマイクロフローのいずれか)

## 2つのプロパティ

### 2.1 エンティティ (パス)

**エンティティ (パス)** プロパティは、データビューに表示されるエンティティを指定します。 トップレベルのデータビューがある場合 **エンティティ (path)** はエンティティであり、ページが開かれたときにこのエンティティのオブジェクトまたはオブジェクトが渡されることを期待する。

ネストされたデータビューがある場合は、周囲のデータコンテナのエンティティに関連付けられているエンティティを選択できます。 そして、周囲のデータコンテナの実体は、この協会の親であるべきです。 関連付けの詳細については、 [Associations](associations) を参照してください。

{{% image_container width="400" %}}![コンテクストソース](attachments/data-widgets/context-source-example.png)
{{% /image_container %}}

## 3 続きを読む

* [データウィジェット](data-widgets)
* [関連](関連)