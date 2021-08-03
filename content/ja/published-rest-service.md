---
title: "公開されたRESTサービス"
parent: "published-rest-services"
menu_order: 10
description: "公開された REST サービスの設定オプション"
tags:
  - "公開された REST"
  - "サービス"
  - "予約済みURLの接頭辞："
  - "swagger"
  - "セキュリティ"
  - "CORS"
  - "リソース"
  - "操作"
  - "how-to"
---

{{% alert type="info" %}}

**公開されたRESTサービス** 機能は、バージョン7.10.0で導入されました。

{{% /alert %}}

## 1つの紹介

公開された REST サービスを使用して、エンティティとマイクロフローを REST 標準を使用して他のアプリに公開します。

このドキュメントでは、Desktop ModelerでパブリッシュされたRESTサービスが開かれたときに表示されるパブリッシュされたRESTサービス構成オプションについて説明します。

## 2つの全般

<a name="service-name"></a>

### 2.1 サービス名

サービス名はアプリ内のサービスを一意に識別します。 [OpenAPI (Swagger) ドキュメント ページ](open-api) にも表示されます。

サービスが最初に作成されると、サービスのデフォルトの場所の作成にサービス名が使用されます。 サービス名にスペースや特殊文字が含まれている場合は、サービスロケーションで `_` 文字に置き換えられます。

### 2.2 バージョン

{{% alert type="info" %}}

**バージョン** 機能は、バージョン 7.12.0 で導入されました。

{{% /alert %}}

バージョンは [OpenAPI (Swagger) ドキュメント ページ](open-api) にバージョン情報を表示するために使用されます。 バージョン フィールドで任意の文字列を設定できますが、 [セマンティック バージョン管理](https://semver.org/) スキームに従うことをお勧めします。

デフォルトでは、バージョンは "1.0.0" に設定されています。

<a name="location"></a>

### 2.3 場所

{{% alert type="info" %}}

**場所** は Mendix バージョン 7.12.0 以降で編集可能です。

{{% /alert %}}

format@@0には、サービスに到達できるURLが表示されます。

デフォルトでは、場所はサービス名と"v1"を"rest/"プレフィックスに追加することで構築されます。 サービス名は無効なURL文字から除外されます。スペースや特殊文字などです。

例
```
http//localhost:8080/rest/my_service_name/v1
```

デフォルトの場所をほぼすべての有効な URL に変更できます。

#### 2.3.1 予約されたプレフィックス

次の URL プレフィックスは予約されており、ロケーションでの使用は許可されていません。

* `ws/`
* `ws-doc/`
* `rest-doc/`
* `odata/`
* `odata-doc/`
* `api-doc/`
* `xas/`
* `p/`
* `reload/`

アプリケーションが実行されると、場所をクリックして [インタラクティブなドキュメント ページ](published-rest-services#interactive-documentation) を開くことができます。

<a name="public-documentation"></a>

### 2.3 公開ドキュメント

公開ドキュメントは、サービスの [OpenAPI 2.0 (Swagger) ドキュメント](open-api) で使用されます。 リッチテキストには、 [GitHub風味のマークダウン](gfm-syntax) を使用できます。

<a name="export-swagger-json"></a>

### 2.5 swagger.json をエクスポート

To save a service's [OpenAPI (Swagger) documentation](open-api) somewhere on your machine, simply right-click the service in the **Project Explorer** and select **Export swagger.json** (or just click the **Export swagger.json** button, depending on your Modeler version). これは [OpenAPI 2.0 ファイル形式](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md) の機械可読形式のファイルです。 ほとんどのAPIツールはこのフォーマットをサポートしています。

アプリが実行されているとき、このファイルは `/rest-doc/servicename/swagger.json` の下で利用できます。

## 3つのセキュリティ

<a name="authentication"></a>

### 3.1 認証が必要

{{% alert type="info" %}}

**認証なし** 機能は、バージョン 7.11.0 で導入されました。 以前のバージョンでは、常に **ユーザー名とパスワード**でした。

**Active Session** の認証はバージョン7.13.0で導入されました

**カスタム** 認証はバージョン 7.17.0 で導入されました

{{% /alert %}}

クライアントを認証する必要があるかどうかを選択します。

### 3.2 認証メソッド

認証が必要な場合は、サポートしたい認証方法を選択できます。

* **ユーザー名とパスワード** を選択すると、クライアントが **Authorization** ヘッダー内のユーザー名とパスワードを使用して自分自身を認証できるようになります (これは「基本認証」と呼ばれます)
* 現在のアプリケーション内でJavaScriptからのアクセスを許可するには、 **アクティブセッション** を選択してください
  * ユーザーがブラウザにログインすると、アプリ内の JavaScript は現在のユーザーのセッションを使用して REST サービスにアクセスできます
  * クロスサイト・リクエストの偽造を防ぐには、 `X-Csrf-Token` ヘッダーを各リクエストに設定する必要があります。例えば:

    ```var xmlHttp = new XMLHttpRequest();
    xmlHttp.open("GET", "http://mysite/rest/myservice/myresource", false);
    xmlHttp.setRequestHeader("X-Csrf-Token", mx.session.getConfig("csrftoken"));
    xmlHttp.send(null);
    ```
* マイクロフローを使用して認証するには、 **Custom** を選択します。 このマイクロフローは、ユーザーがリソースにアクセスするたびに呼び出されます。

サービスがそれらのそれぞれを試してもらうために複数の認証方法を確認してください。 最初に **カスタム** 認証、次に **ユーザー名とパスワード**、次に **アクティブセッション**を試してみます。 詳細については、 [公開された REST ルーティング](published-rest-routing) を参照してください。

<a name="authentication-microflow"></a>

### 3.3 マイクロフロー

カスタム認証に使用するマイクロフローを指定します。

**パラメータ** を選択すると、 [認証マイクロフロー](published-rest-authentication-parameter) に渡されるパラメータのリストが表示されます。 このウィンドウでは、認証マイクロフローのパラメータがリクエストヘッダから来るか、クエリ文字列から来るかを指定できます。

microflow は [HttpRequest](http-request-and-response-entities#http-request) をパラメータとして受け取ることができるため、受信するリクエストを検査することができます。

マイクロフローは、パラメータとして [HttpResponse](http-request-and-response-entities#http-response) を取ることもできます。 マイクロフローがこのレスポンスのステータスコードを他のものに設定した場合、 **200**この値は返され操作は実行されません。 レスポンスに設定されたすべてのヘッダーは返されます (microflow が空のユーザーを返す場合を除く)。

認証マイクロフローは、ユーザを返す必要があります。

認証マイクロフローには3つの可能性のある結果があります
  * HttpResponse パラメータのステータスコードが他のものに設定されている場合 **200**. この値は返され操作は実行されません
  * そうでなければ、結果のユーザーが空でない場合、そのユーザーのコンテキストで操作が実行されます。
  * そうでなければ、結果のUserが空の場合、次の認証方式が試みられます。 他の認証方法がない場合、結果は **404 Not Found** です。

### 3.4 許可されたロール

許可されたロールは、どの [モジュール ロール](module-role) ユーザがサービスにアクセスできる必要があるかを定義します。 このオプションは、 **** が **はい** に設定されている場合にのみ使用できます。

{{% alert type="warning" %}}
WebサービスユーザーはRESTサービスにアクセスできません。
{{% /alert %}}

## 4 CORS を有効にする

自分以外のウェブサイトでサービスを利用する必要がある場合は、このボックスにチェックを入れてください。

[設定](cors-settings) ボタンをクリックして、このアクセスを詳細に指定します(たとえば、どのウェブサイトにサービスへのアクセスが許可されているか)。

## 5つのリソース

REST サービスは、多数の [リソース](published-rest-resource) を公開します。 リソース上では、GET、PUT、POST、PATCH、DELETE、HEAD、OPTIONS 演算を定義できます。

エンティティまたはメッセージ定義をこのリストにドラッグして [完全なリソース](generate-rest-resource) を生成できます。

## 6つの操作

リソースを選択すると、そのリソースに対して定義されている [操作](published-rest-operation) が表示されます。

リソースと操作は [Location](#location) に追加され、アクセスできる URL を形成します。

![](attachments/published-rest-service/example-location-url.png)

## 7例

**MendixでネイティブにRESTを公開する方法**

{{% youtube HzrFkv0U4n8 %}}

## 8 続きを読む

特定のリクエスト URL に対してどの操作が実行されるかについての詳細は、 [公開された REST Routing](published-rest-routing) を参照してください。
