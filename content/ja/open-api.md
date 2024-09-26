---
title: "OpenAPI 2.0 ドキュメント"
parent: "published-rest-technical-details"
menu_order: 30
description: "公開された REST サービスによって生成された swagger.json ファイルの説明"
tags:
  - "swagger"
  - "swagger.json"
  - "OpenAPI 2.0"
  - "ドキュメント"
  - "パス"
  - "操作"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/open-api.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

[公開された REST サービス](published-rest-service) はすべて自動的に文書化されます。 このシステムは *swagger.json* ファイルを生成し、 [OpenAPI 2.0 仕様](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md) (以前は "swagger 仕様"として知られていました) に準拠します。 このファイルは [Studio Pro](published-rest-service#export-swagger-json) から保存することも、 */rest-doc/servicename/swagger.json* からダウンロードすることもできます。

If you need to communicate with the service from another app, you can use the *swagger.json* file to generate an API in many different systems, including Microsoft Visual Studio, React, Angular, and Java. これにより、異なるアプリ間で簡単に通信できます。

Many of the popular API tools support OpenAPI 2.0, including [SoapUI](https://www.soapui.org/), [Postman](https://www.getpostman.com/), and [Swagger UI](https://swagger.io/swagger-ui/) (for a longer list of supported tools, see [swagger.io/commercial-tools](https://swagger.io/commercial-tools/)). つまり、これらのツールから公開されたサービスを簡単にテストできます。

A technical description is presented below of which parts of the *swagger.json* file are generated.

## 2つのスキーマ

メインスキーマオブジェクトはサービスをドキュメントします。

| 属性                   | 生成された値                                                                                                                      |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `swagger`            | 2.0                                                                                                                         |
| `info.title`         | サービス [の](published-rest-service#service-name) の名前。                                                                          |
| `info.description`   | [サービスの公開ドキュメント](published-rest-service#public-documentation).                                                               |
| `info.version`       | 1.0.0                                                                                                                       |
| `ホスト`                | アプリが実行されているホスト。                                                                                                             |
| `basePath`           | */rest/servename*                                                                                                           |
| `スキーム`               | アプリが実行されているサーバーのスキーム（*http* または *https* ） 。                                                                                 |
| `回答`                 | セキュリティが有効な場合の不正な応答が含まれています。                                                                                                 |
| `securityDefinition` | セキュリティが有効な場合の基本認証が含まれています。                                                                                                  |
| `セキュリティ`             | セキュリティが有効な場合の基本認証が含まれています。                                                                                                  |
| `タグ`                 | 各リソースは、リソースの [名前](published-rest-resource#name) と説明 ([公開ドキュメント](published-rest-resource#public-documentation)) を持つタグを生成します。 |
| `パス`                 | 演算の各グループはパスオブジェクトを生成します。 詳細は以下をご覧ください。                                                                                      |

## 3つのパス

サービスの操作は、 [operation path](published-rest-operation#operation-path) でグループ化されています。 これらの各グループは、操作パスを名前として `PathItem` を生成します。 `PathItem` には、グループ内の各操作に `Operation` プロパティがあります。

## 4つの操作

各操作は、 `操作` オブジェクトを生成します。

| 属性        | 生成された値                                                      |
| --------- | ----------------------------------------------------------- |
| `タグ`      | リソースの [名](published-rest-resource#name)。                    |
| `summary` | 操作の [公開ドキュメントの要約](published-rest-operation#summary)。        |
| `説明`      | 操作の [公開ドキュメントの説明](published-rest-operation#description)。    |
| `パラメータ`   | パスとクエリパラメータ。 POST、PUT、PATCH、OPTIONS メソッドには、body パラメータもあります。 |
| `回答`      | OK レスポンス。 セキュリティが有効になっている場合、これも許可されていない応答です。                |
| `非推奨です`   | 非推奨として操作がマークされている場合は true に設定します。                           |
