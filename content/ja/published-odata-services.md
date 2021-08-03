---
title: "公開されたOData Services"
parent: "統合"
menu_order: 10
tags:
  - "studio pro"
---

## 1つの紹介

Studio Pro では、新しい公開された OData サービスを追加することで、エンティティを [OData リソース](published-odata-resource) として公開することができます。 公開された OData サービスには、任意の数の関連リソースを公開できます。 デフォルトでは、エンティティの非修飾名の複数形は一意に識別するために URI 内で使用されます。 でもリソースの名前も上書きできます

Mendix の OData に使用される標準は次のとおりです。

* [Atom XML 形式のデータを返すOData バージョン 3](http://www.odata.org/documentation/odata-version-3-0)。
* [JSON形式のデータを返すOData バージョン 4](http://www.odata.org/documentation)。

{{% alert type="info" %}}
Studio Pro [9.4.0](/releasenotes/studio-pro/9.4) で OData バージョン 4 の機能を導入しました。
{{% /alert %}}

標準のすべての部分が実装されているわけではありません。 何かがここで文書化されていない場合は、まだ追加されていません。

このドキュメントでは、パブリッシュされた OData サービスを作成する際に利用できるオプションについて説明し、実行時の考慮事項で終了します。

## 2つの全般

### 2.1 サービス名

サービス名は、OData サービスの固有の URI を作成するために使用されます。 従って、サービス名は [RFC 3986](https://tools.ietf.org/html/rfc3986) および [RFC 3987](https://tools.ietf.org/html/rfc3987) に従って整形されるべきです。

### 2.2 バージョン

**バージョン** フィールドを使用して、サービスにバージョン番号を割り当てます。 この番号はAPIドキュメントに表示されます。

{{% alert type="info" %}}

公開するサービスに意味的な番号を採用することをお勧めします。

{{% /alert %}}

### 2.3 名前空間

OData では、名前空間はデータ型を参照するために使用されます。 **設定** タブで、この名前空間をカスタマイズできます。 文字、数字、またはドットで始まる任意の値に変更できます。最大長は 512 文字です。

### 2.4 リソース

[リソース](published-odata-resource) は、エンティティによって表現され、URI によって識別されるネットワークアクセス可能なデータオブジェクトです。

## 3つの設定

### 3.1 OData version

OData 4(推奨)とOData 3のどちらかを選択できます。 主な違いは、OData 4 サービスは JSON で結果を返し、OData 3 サービスは XML で結果を返すことです。

{{% alert type="info" %}}
この設定は Studio Pro [9.4.0](/releasenotes/studio-pro/9.4) で導入されました。 以前のバージョンでは、公開されていたODataサービスはすべてOData 3でした。
{{% /alert %}}

### 3.2 関連

関連付けを表す方法を選択できます。 詳細については、 [OData 表現](odata-representation#associations) の *Associations* セクションを参照してください。

### 3.3 セキュリティ {#security}

[App Security](project-security) が有効な場合、OData サービスのセキュリティを設定できます。

#### 3.3.1 認証が必要 {#authentication}

クライアントを認証する必要があるかどうかを選択します。 制限なくリソースへのアクセスを許可するには、 _No_ を選択します。 サポートする認証方法を選択するには、 _はい_ を選択します。

_はい_を選択した場合でも、OData リソースを匿名ユーザに公開できます。 匿名ユーザを許可する方法についての詳細は、 [匿名ユーザロール](anonymous-users) を参照してください。

#### 3.3.2 認証メソッド

認証が必要な場合は、サポートしたい認証方法を選択できます。

* **ユーザー名とパスワード** を選択すると、クライアントが **Authorization** ヘッダー内のユーザー名とパスワードを使用して自分自身を認証できるようになります (これは「基本認証」と呼ばれます)
* 現在のアプリケーション内でJavaScriptからのアクセスを許可するには、 **アクティブセッション** を選択してください
* **カスタム** を選択して、マイクロフローを使用して認証します。(このマイクロフローは、ユーザーがリソースにアクセスしたいたびに呼び出されます)

サービスがそれらのそれぞれを試してもらうために複数の認証方法を確認してください。 最初に **カスタム** 認証、次に **ユーザー名とパスワード**、次に **アクティブセッション**を試してみます。

##### 3.3.2.1 ユーザー名 & パスワード {#username-password}

認証は、呼び出しの HTTP ヘッダーに基本的な認証を含めることによって行うことができます。 これを行うには、 **Authorization** というヘッダを構築する必要があり、その内容は以下のように構成される必要があります。

1.  ユーザー名とパスワードは、文字列 "username:password" に結合されます。
2.  結果の文字列は Base64 の [RFC2045-MIME](https://tools.ietf.org/html/rfc2045) variant を使って符号化されます (ただし、76 char/lineに限定されません)。
3.  認可方法と単一のスペース (つまり、「Basic 」はエンコードされた文字列の前に置かれます)。

この結果は、 `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==` のようなヘッダです。

##### 3.3.2.2 アクティブセッション {#authentication-active-session}

この認証方法を確認すると、アプリケーションのJavaScriptは現在のユーザーのセッションを使用してRESTサービスにアクセスできます。

クロスサイト・リクエストの偽造を防ぐには、 `X-Csrf-Token` ヘッダーを各リクエストに設定する必要があります。例えば:

```
var xmlHttp = new XMLHttpRequest();
xmlHttp.open("GET", "http://mysite/odata/myresource", false);
xmlHttp.setRequestHeader("X-Csrf-Token", mx.session.getConfig("csrftoken"));
xmlHttp.send(null);
```

##### 3.3.2.3 カスタム {#authentication-microflow}

カスタム認証に使用するマイクロフローを指定します。

microflow は [HttpRequest](http-request-and-response-entities#http-request) をパラメータとして受け取ることができるため、受信するリクエストを検査することができます。

マイクロフローは、パラメータとして [HttpResponse](http-request-and-response-entities#http-response) を取ることもできます。 マイクロフローがこのレスポンスのステータスコードを他のものに設定した場合、 **200**この値は返され操作は実行されません。 レスポンスに設定されたすべてのヘッダーは返されます (microflow が空のユーザーを返す場合を除く)。

認証マイクロフローは、ユーザを返す必要があります。

認証のマイクロフローには3つの可能性のある結果があります。

  * HttpResponse パラメータのステータスコードが他のものに設定されている場合 **200**. この値が返され操作は実行されません
  * 結果のユーザーが空でない場合、そのユーザーのコンテキストで操作が実行されます。
  * 結果のUserが空の場合、次の認証方法が試行されます(他の認証方法がない場合)。 結果は **404 Not Found** ) です。

#### 3.3.3 許可されたロール

許可されたロールは、どの [モジュール ロール](module-security#module-role) ユーザがサービスにアクセスできる必要があるかを定義します。 このオプションは、 **** が **はい** に設定されている場合にのみ使用できます。

{{% alert type="warning" %}}
Webサービス利用者はODataサービスにアクセスできません。
{{% /alert %}}

## 4つのプロパティ

OData サービスドキュメントが表示されている場合のプロパティ ペインで。 **一般** タブで設定できる値の一部を編集できます。 例えば、** サービス名 ** 、 **バージョン**、 **バージョン**、および **名前空間** など。

このセクションでは、設定できる追加の値について説明します。

### 4.1 ドキュメント

ここでは、サービスの説明を追加できます。 これは、このアプリで作業している他のユーザーが利用でき、OData サービスがデプロイされている場合は公開されません。

### 4.2 Illegal XML 文字を置換

XML では特殊文字が使用できない場合があります。 データにこれらの 文字が含まれている場合、クライアントはエラーを受け取ります。 If you set this setting to *Yes*, those illegal characters are replaced by the DEL character, and the client will not get an error. しかし、クライアントが受け取るデータは、データベースに格納されているもの ではありません。これは、これらの文字が置き換えられているためです。

この *無効な XML 文字を置換する* オプションは、OData バージョンが OData 4 の場合は使用できません。 OData 4 はデータを JSON 形式で返すためです。

デフォルト値: *いいえ*

### 4.3 公開ドキュメント

*概要* と *説明* を書くことができます。

## 5ランタイムについての考慮事項

### 5.1 全般

アプリが公開されたら、 公開された OData サービスは、アプリのルート URL に続いて `/odata-doc/` で利用可能になります。 例えば、 `http://localhost:8080/odata-doc/` OData リソースと Excel の間のリンクを作成するには、リンクをコピー&ペーストします。

{{% alert type="warning" %}}
OData リソースの API ドキュメントはデフォルトで有効になっていますが、本番環境で実行されているアプリのアクセスは管理者によって制限される場合があります。
{{% /alert %}}

OData レスポンスをフィルタリングする方法については、 [OData Query Options](odata-query-options) を参照してください。

Mendix 属性が OData でどのように表現されるかについては、 [OData 表現](odata-representation) を参照してください。

OData を介してエンティティを公開するとき、エンティティはストリーミング方法で Mendix データベースから取得され、Mendix ランタイムでメモリ不足のエラーを回避します。

### 5.2 オンプレミスのデプロイ

一部のオンプレミスサーバ、特にMicrosoft IISを使用しているサーバは、ホストヘッダをリクエストから除去します。 これは、OData サービスとドキュメントが予期しないURLに公開されることを意味します。

この問題を解決するには、サーバーがホストヘッダーを保持していることを確認する必要があります。 [Microsoft Windows](/developerportal/deploy/deploy-mendix-on-microsoft-windows#preserve-header) デプロイメントのドキュメントの *ホストヘッダーの保持* セクションを参照してください。
