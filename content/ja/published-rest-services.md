---
title: "公開された REST サービス"
parent: "統合"
menu_order: 20
description: "Mendix アプリから公開された REST サービスの概要"
tags:
  - "公開"
  - "REST サービス"
  - "概要"
  - "構成"
---

## 1つの紹介

[公開された REST サービス](published-rest-service) を追加して、エンティティやマイクロフローを REST 標準を使用して他のアプリに公開します。

## 2件の公開されたRESTサービス

公開されたサービスを追加する際の利用可能なオプションの概要については、 [Publiced REST Service](published-rest-service) を参照してください。

[ドメインモデル](domain-model) 内のエンティティを右クリックし、 [RESTリソースとして公開](generate-rest-resource)を選択すると、RESTを介してエンティティを簡単に公開できます。

REST 操作としてマイクロフローを発行するには、エディタ内の任意の場所を右クリックし、 [REST サービス操作として公開](publish-microflow-as-rest-operation) を選択します。

## <a name="authorization"></a>3 認証

公開された REST サービスは、基本認証、アクティブセッション認証、カスタム認証で保護できます。 基本およびアクティブなセッション認証はデフォルトです。 そして、アプリの [セキュリティレベル](project-security) を **プロトタイプ/デモ**  または **プロダクション**に設定すると、自動的に適用されます。

基本認証をしたくない場合は、次の3つのオプションがあります。

* 特定の公開された REST サービスに対して、 [認証なし](published-rest-service#authentication) を選択するか、または
* [匿名ユーザー](project-security#anonymous-users) をアプリに許可すると、公開された REST サービスはすべて認証なしで利用可能になり、または
* microflow [を使用して](published-rest-service#authentication-microflow) カスタム認証を実装できます。

{{% alert type="warning" %}}
なお、Web サービスユーザは REST サービスにアクセスできません。
{{% /alert %}}

詳細については、 [公開された REST ルーティング](published-rest-routing) および [](published-rest-service#authentication) *公開された REST サービス* の認証が必要です 。

## <a name="interactive-documentation"></a>4 ドキュメント

[公開された REST サービス](published-rest-service) はすべて自動的に文書化されます。 このドキュメントは `http://yourapp.com/rest-doc/` のアプリから入手できます。 各サービスには、 [Swagger UI](https://swagger.io/swagger-ui/) を使用したインタラクティブなドキュメントページがあります。 サービスとやり取りして、サービスがどのように動作するかを確認できます。

サービスのドキュメントは [OpenAPI 2.0](open-api) 形式で入手可能で、多くのシステムやツールで読めます。 メッセージ定義のための [JSON スキーマ](published-rest-service-json-schema) を含んでいます。

## 5件のログ

公開された REST サービスとのやり取りに関する詳細情報を記録するには [](logging) REST 公開 **のログノードのログレベル** を **トレース** に設定します。

