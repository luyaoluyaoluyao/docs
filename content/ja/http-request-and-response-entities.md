---
title: "HttpRequest & HttpResponse System Entities"
parent: "統合"
menu_order: 45
tags:
  - "studio pro"
---

## 1つの紹介

`HttpRequest` は、サーバーへのリクエストを表すシステムエンティティです。 `HttpResponse` はサーバからのレスポンスを表している。 [publishing](published-rest-services) または [](consumed-rest-services) REST サービスを利用する場合は、これらのエンティティを使用します。

![](attachments/http-request-and-response-entities/http-request-and-response-domain-model.png)

## 2HttpRequest {#http-request}

`HttpRequest` エンティティには、次の属性があります。

| 属性                                  | タイプ | デフォルト値   | 説明                             |
| ----------------------------------- | --- | -------- | ------------------------------ |
| `HttpVersion` ( `HttpMessage` から継承) | 文字列 | HTTP/1.1 | プロトコルバージョン ほとんどの場合、この値を無視できます。 |
| `Uri`                               | 文字列 | 空        | クエリパラメータを含む、受信リクエストの完全なURI。    |
| `コンテンツ` ( `HttpMessage` から継承)       | 文字列 | 空        | リクエストの本文                       |

リクエストヘッダーは、 `HttpHeaders` アソシエーションから取得できます。

## 3 HttpResponse {#http-response}

`HttpResponse` エンティティには次の属性があります。

| 属性                                  | タイプ | デフォルト値   | 説明                             |
| ----------------------------------- | --- | -------- | ------------------------------ |
| `HttpVersion` ( `HttpMessage` から継承) | 文字列 | HTTP/1.1 | プロトコルバージョン ほとんどの場合、この値を無視できます。 |
| `StatusCode`                        | 整数  | 200      | サーバーから返された HTTP ステータスコード。      |
| `理由フレーズ`                            | 文字列 | OK       | `StatusCode` のテキスト表現。          |
| `コンテンツ`                             | 文字列 | 空        | レスポンスの本文。                      |

HTTP ステータスコードの詳細については、 [W3C ステータスコード定義の仕様](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) を参照してください。

`HttpHeaders` アソシエーションを介してレスポンスヘッダーを取得または作成できます。

重要な `HttpResponse` ヘッダーは `Content-Type`で、コンテンツがどのように解釈されるべきかを示します。 このヘッダの詳細については、Content-Type [の](https://www.w3.org/Protocols/rfc1341/4_Content-Type.html) W3C 仕様を参照してください。
