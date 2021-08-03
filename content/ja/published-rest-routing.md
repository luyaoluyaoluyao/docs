---
title: "公開されたRESTリクエストルーティング"
parent: "published-rest-technical-details"
menu_order: 10
description: "例のリクエストがどのように処理されるか、どのようなセキュリティが適用されるか、サービスによって何が返されるかを示すフローチャート。"
tags:
  - "フローチャート"
  - "処理中"
  - "セキュリティ"
  - "サービス"
  - "リソース"
  - "操作"
  - "method"
  - "認証"
  - "返品コード"
  - "公開された REST"
---

{{% alert type="info" %}}

**公開されたRESTサービス** 機能はMendix 7.10.0に導入されました。

{{% /alert %}}

REST HTTP リクエストがサーバーに到着すると、サーバーは実行する [操作](published-rest-operation) と適用するセキュリティを決定する必要があります。

このフローチャートは、リクエストの例、これがどのように処理されるか、そして異なる状況下でサービスによって返されるものを示しています。

次のような質問に答えるには、このフローチャートを参照してください。

* URLに対してどのRESTオペレーションマイクロフローが実行されますか？
* RESTオペレーションマイクロフローで例外が発生した場合はどうなりますか?
* REST サービスの基本認証はどのように機能しますか?
* REST サービスの匿名認証はどのように機能しますか?
* REST 操作の microflow が空の HTTPResponse を返す場合はどうなりますか?
* 私のRESTサービスは _400Bad Request_を返すのはなぜですか?
* なぜ私のRESTサービスは _401 未承認_を返すのですか?
* なぜ REST サービスは _404 Not Found_ を返すのですか?
* なぜ私のRESTサービスは _405メソッドが許可されていない_を返すのですか？

リクエストの例は `GET/rest/petstore/pet/12` です。

![](attachments/published-rest-service/determine-operation.png)
