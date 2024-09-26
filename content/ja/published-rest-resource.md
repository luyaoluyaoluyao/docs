---
title: "公開されたRESTリソース"
parent: "published-rest-service"
menu_order: 50
description: "公開された REST リソースの設定可能なオプション"
tags:
  - "公開された REST"
  - "リソース"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-resource.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

公開された REST リソースは、 [公開 REST サービス](published-rest-service) の一部であり、1 つまたは複数の [操作](published-rest-operation) を定義できるアイテムのコレクションを表します。

ドメインモデル内のエンティティから公開された REST リソースを生成できます。 [公開された REST リソースの生成](generate-rest-resource) を参照してください。

## 2つの全般

### <a name="name"></a>2.1 リソース名

リソース名は、 [サービス](published-rest-service) 内のリソースを一意に識別します。 操作の場所の一部であるため、スペースや特殊文字を含めることはできません。

## <a name="public-documentation"></a>2.2 公開ドキュメント

公開ドキュメントは、サービスの [OpenAPI (Swagger) ドキュメント ページ](published-rest-services#interactive-documentation) で使用されます。 リッチテキストには、 [GitHub風味のマークダウン](gfm-syntax) を使用できます。
