---
title: "REST サービスに発信"
parent: "インテグレーションアクティビティ"
tags:
  - "studio pro"
  - "統合アクティビティ"
  - "休憩所に電話する"
menu_order: 10
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/call-rest-action.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}
このアクティビティは、 **Microflow** でのみ使用できます。
{{% /alert %}}

## 1つの紹介

**REST サービスを呼び出す** アクティビティは、REST エンドポイントを呼び出すために使用できます。 REST コールの応答をどのように処理するか、場所を指定できます。

## 2つのプロパティ

以下の画像では、コールレストアクションプロパティの例を示しています。

![restactionプロパティを呼び出す](attachments/integration-activities/call-rest-action-properties.png)

このアクティビティには2つのプロパティがあります。 左側のダイアログボックスと右側のプロパティ ペインに表示されています

コールレストアクションプロパティペインは以下のセクションで構成されています:

* [アクション](#action)
* [一般的な](#common)

## 3つのアクションセクション{#action}

プロパティ ペインの **アクション** セクションには、このアクティビティに関連付けられたアクションが表示されます。

アクションの横にある省略記号 (**…**) をクリックすることで、このアクションを構成するためのダイアログボックスを開くことができます。

また、マイクロフロー内のアクティビティをダブルクリックするか、アクティビティを右クリックして **プロパティ** を選択することで、ダイアログボックスを開くこともできます。

プロパティ ダイアログ ボックスは 4 つのタブで構成されています:

* [全般](#general)
* [HTTP ヘッダー](#http-headers)
* [リクエスト](#request)
* [回答](#response)

## 4つの一般タブ {#general}

![](attachments/integration-activities/general-tab.png)

### 4.1 場所

**Location** プロパティで、呼び出される REST エンドポイントを定義します。

場所は文字列テンプレートを使用して入力する必要があります。これは有効なURL文字列になります。

#### 4.1.1 文字列テンプレート{#string-template}

ロケーションのテンプレートには、括弧の間の数値として記述されたパラメータを含めることができます (例: `{1}`)。 最初のパラメータは `1`、2 番目の `2`などの数字を持ちます。 opening brace (`{`), double opening brace (`{{` ) を使ってエスケープすることができます。

#### 4.1.2 パラメータ

テンプレート内の各パラメータに対して、文字列値を生成する [マイクロフロー式](expressions) を使用してその値を指定できます。 この値はパラメーターの位置に挿入されます。

### 4.2 HTTP メソッド

**HTTP メソッド** プロパティは、REST エンドポイントを呼び出すときに使用する HTTP メソッドを定義します。 GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS.

### 4.3 リクエスト時にタイムアウトを使用

**リクエスト時のタイムアウトを** に **はい** に設定して、コールRESTのエンドポイントが応答するのを待つ時間を指定できます。

{{% alert type="warning" %}}
このセットは **はい** にしておくことをお勧めします。 (Mendix Cloudで使用されているものを含む)ほとんどのクラウドインフラストラクチャサービスは、数分間トラフィックがない場合、自動的にHTTP接続を閉じます。 活動がまだ反応を待っていてもね これは、アクティビティがWebサービスを呼び出す場合、応答に長い時間がかかることを意味します。 これを認識せずに接続が切断される可能性があります。あなたのアクティビティには応答がありません。 このような状況では、 **リクエスト時のタイムアウトを使用する** が **いいえ**に設定されている場合 データが届くのを無期限に待ってるんだ
{{% /alert %}}

既定値: *はい* (Studio Pro [8.5.0](/releasenotes/studio-pro/8.5#850)の時点で; 以前のバージョンでは、デフォルト値は No でした)

### 4.4 タイムアウト

もし REST エンドポイントが **タイムアウト (s)**の秒数の後に応答していない場合 例外が発生し、microflow がロールバックまたはカスタムエラーハンドラに移動します。

Default value: *300 seconds* (as of Studio Pro [8.5.0](/releasenotes/studio-pro/8.5#850); in earlier versions, the default value for **Use timeone on request** was No)

### 4.5 プロキシ設定

ほとんどの場合、この設定は無視できます。 **プロジェクト設定を使用する** は良いデフォルト値です。

必要に応じて、リクエストにプロキシを使用するかどうかを設定できます。 選択肢は以下の通りです:

* **プロジェクト設定を使用する** – プロジェクトレベルで定義されているすべての設定を使用する (デフォルト)
* **オーバーライド** – このアクションのプロジェクトレベルの設定を上書きする
* **プロキシなし** – このアクションにプロキシを使用しないでください

**Override**を選択すると、プロキシを使用するかどうかを動的に設定できます。 その後、プロキシのホスト、ポート、ユーザー名、およびパスワードの設定を指定します。

### 4.6 クライアント証明書

{{% alert type="warning" %}}
この機能は Mendix 8.18.0 以降で使用できます。
{{% /alert %}}

ほとんどの場合、デフォルトの **プロジェクト設定を使用する** が使用できます。

ただし、 **上書き** をクリックすることで、リクエストに使用するクライアント証明書を指定することができます。 次のいずれかから選択します:

* **プロジェクト設定を使用する**(デフォルト) – プロジェクトレベルで定義されている設定を使用する
* **オーバーライド** – このアクションのプロジェクトレベルの設定を上書きする

**Override**を選択すると、使用されるクライアント証明書を構成することができます。 **編集** をクリックして、 **クライアント証明書識別子** を指定します。 この識別子は、アプリのデプロイ先によって異なる場所で設定できます。

* Mendix クラウドにアプリをデプロイする場合、 [クライアント証明書をピン留めするときに識別子が設定されます](/developerportal/deploy/certificates#outgoing-client-certificates)
* アプリケーションを他の場所にデプロイする場合、その識別子はカスタム設定 [ClientCertificateUsages](custom-settings#ca-certificates) で設定されます。

When this identifier is not set (either not pinned or not present in _ClientCertificateUsages_), the default settings will be used (as if **Use project settings** were selected).

## 5 HTTP ヘッダータブ {#http-headers}

![](attachments/integration-activities/http-headers-tab.png)

### 5.1 HTTP 認証を使用する

**HTTP 認証を使用する** チェック ボックスは、基本認証を使用するかどうかを定義します。

### 5.2 ユーザー名

**User name** プロパティは、HTTP を介した認証に使用されるユーザー名を定義します。 ユーザー名は [microflow Expressions](expressions) を使用して入力する必要があります。 microflow 式は文字列になります。

### 5.3 パスワード

**Password** プロパティは、HTTP を介した認証に使用されるパスワードを定義します。 パスワードは [式](expressions) を使用して入力する必要があります。 microflow 式は文字列になります。

### 5.4 カスタム HTTP ヘッダー

これらのヘッダは HTTP リクエストヘッダに追加されます。 各カスタムヘッダーは、キーと値(マイクロフロー式)のペアです。

## 6 リクエストタブ {#request}

![](attachments/integration-activities/request-tab.png)

以下のセクションでは、リクエストを生成するためのドロップダウンメニューのオプションについて説明します。

{{% alert type="info" %}}
リクエストは HTTP メソッド POST、PUT、PATCH、および OPTIONS に対してのみ生成できます。
{{% /alert %}}

### 6.1 リクエスト全体のエクスポートマッピング

このオプションを使用すると、リクエストの本文に単一の [エクスポート マッピング](export-mappings) を使用できます。

#### 6.1.1 マッピング

適用するマッピングを選択します。

#### 6.1.2 パラメータタイプ

[エクスポート マッピング](export-mappings) が入力を必要とする場合、このフィールドは入力の型を表示します。

#### 6.1.3 パラメータ

[エクスポート マッピング](export-mappings) が入力を必要とする場合、正しい型のパラメータを選択することができます。

#### 6.1.4 コンテンツタイプ

[エクスポート マッピング](export-mappings) がメッセージ定義に基づいている場合、XML または JSON をエクスポートすることができます。 必要な出力タイプを選択します。

{{% alert type="info" %}}
**Content-Type ヘッダー** がデフォルトでは設定されていません。 設定するには、 **Custom HTTP Headers** タブを使用します。
{{% /alert %}}

### 6.2 リクエスト全体のバイナリ

このオプションを使用すると、バイナリデータ(例えば、FileDocumentの内容)を送信できます。

### 6.3 フォームデータ

このオプションを使用すると、複数の部品の multipart/form-data リクエストを生成できます。 各パートはキーと値(マイクロフロー式)のペアです。

このオプションでは、マイクロフロー式の変数として使用される場合、FileDocuments とイメージもサポートされます。

#### 6.3.1 Content Type

Setting up a **Content-Type header** for a form-data request will result in a consistency error, as it will automatically be set to **multipart/form-data**.

FileDocument パートの content type は **application/octet-stream** です。

### 6.4 カスタムリクエストテンプレート

このオプションを使用すると、文字列テンプレートを使用して要求を生成できます。 テンプレートはプレーンテキストでリクエストの構造を定義します。

テンプレートから文字列を構築するための詳細については、上記の [文字列テンプレート](#string-template)を参照してください。

## 7つの応答タブ {#response}

![](attachments/integration-activities/response-tab.png)

### 7.1 対応処理

これらは、応答を処理するためのドロップダウンメニューのオプションです。

* **Apply import mapping** – if the response is JSON or XML, it can be transformed directly into objects using an [import mapping](import-mappings); the fields that you can choose here are described in the [Import Mapping action](import-mapping-action)
* **Store in an HTTP response** – any successful HTTP response can be stored directly in an [HttpResponse](http-request-and-response-entities#http-response) object, and the [$latestHttpResponse](#latesthttpresponse) variable is also updated
* **Store in a file document** – if the response contains binary content (for example, a PDF), it can be stored in an object of an entity type which inherits from `System.FileDocument`
* **文字列に保存** – 応答が文字列の場合 (CSVなど)、文字列変数に直接格納することができます。
* **変数に格納しないでください** - 呼び出しが役に立つものを返さない場合、このオプションを使用してください

### 7.2 タイプ

**Type** フィールドは、出力の型を定義します。

### 7.3 変数

**変数** フィールドは、操作の結果の名前を定義します。

### 7.4 メッセージ本文を $latestHttpResponse 変数に保存します。 {#latesthttpresponse}

If HTTP response status code is not successful (for example, `[4xx]` or `[5xx]`), the flow will continue in an [error handler](error-event#errorhandlers).

{{% alert type="warning" %}}
RESTサービス [をコールする](/refguide8/call-rest-action) アクションに対して常にエラーハンドラを追加する必要があります。
{{% /alert %}}

## 8つの共通セクション{#common}

{{% snippet file="refguide8/microflow-common-section-link.md" %}}
