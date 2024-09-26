---
title: "公開されたREST操作"
parent: "published-rest-service"
menu_order: 10
description: "公開された REST 操作を構成するオプション。"
tags:
  - "公開されたREST"
  - "操作"
  - "method"
  - "小道"
  - "場所の例"
  - "マッピング"
  - "操作パラメータ"
  - "どうやって?"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-operation.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

公開された REST 操作は、 [公開された REST リソース](published-rest-resource) の一部であり、クライアントが GETに呼び出すことができるエンドポイントを定義します。 リソースからアイテムをPUT、POST、PATCH、または削除します。

**公開されたRESTサービス** ドキュメントでは、 **リソース**としてサービスに含めるアイテムを追加することができます:

![公開されたRESTサービス](attachments/published-rest-operation/publshed-rest-service.png)

## 2 操作の定義

When you **Add** or **Edit** a resource, you can define the resource in the **Operation** definition dialog box for the selected item as follows:

![REST 操作](attachments/published-rest-operation/operation-definition.png)

### 2.1 全般

**一般** タブでは、このセクションで説明されている操作の詳細を入力できます。

#### 2.1.1 メソッド

このメソッドは、マイクロフローによって実行される操作の種類を指定します。 ドロップダウンメニューから、次のいずれかを選択できます。

* **GET** – 指定された場所のエントリまたはエントリを取得
* **PUT** - 指定された場所のエントリまたはエントリを置き換えるか、存在しない場合はそれらを作成します
* **POST** – 指定された場所にコレクション内のエントリを作成する
* **PATCH** - 指定された場所のエントリを更新
* **DELETE** – 指定された場所のエントリまたはエントリを削除する
* **HEAD** - retrieve information about the entry or entries at the specified location; this is identical to **GET**, except that a message body is not returned
* **OPTIONS** - 利用可能な通信オプションに関する情報を返す

#### 2.1.2 操作パス{#operation-path}

操作が到達できる場所は、リソースの URL から始まり、 **Operation path** は、操作のパスの残りを指定します。 リソースの場所を使用するには、空のままにしておいてください。

[パスパラメーター](published-rest-path-parameters) を使用して、ロケーションの一部をマイクロフローパラメーターとして、またはインポートマッピングのパラメーターとしてキャプチャすることができます。 `{` と `}` の間の操作パスにパスパラメータを指定します。 path パラメーターの URL 内にある値は、マイクロフローまたはインポートマッピングに渡されます。

**メソッド** および **オペレーションパス** は、 [公開された残りのルーティング](published-rest-routing)に記述されているように、指定されたリクエストURLに対して実行される操作を定義します。

#### 2.1.3 場所例{#example-location}

**場所例** は、操作に到達できる URL の例を示します。

#### 2.1.4 マイクロフロー

操作は以下のパラメータを持つことができます。

 * [クエリパラメータ](published-rest-query-parameters), `?name1=value1&name2=value2`
   {{% alert type="info" %}}
   microflow パラメータがパス内になく、オブジェクトでない場合は、クエリーパラメータと見なされます。
   {{% /alert %}}
* [URL のパスの一部を形成するパスパラメータ](published-rest-path-parameters)
* 操作へのリクエストの本文にあるbodyパラメータ（任意）
   {{% alert type="info" %}}
   **GET**, **HEAD**, および **DELETE** 操作には、bodyパラメータがありません。
   {{% /alert %}}
* リクエストの HTTP ヘッダーから来るヘッダーパラメータ
* マルチパートフォームリクエストの本文の一部であるフォームパラメータ (オプション)

オペレーションのマイクロフローは、これらのオペレーションパラメータを入力とします。

*List* または *Object* 型を持つマイクロフローパラメータは、body パラメータを示します。 インポートマッピングを指定して、受信する JSON または XML を変換できます。 *FileDocument* タイプのパラメータ (または *FileDocument*から継承する) は特別です: フォームパラメータにも使用できます。 インポートマッピングは必要ありません

オペレーションマイクロフローは、 [HttpRequest](http-request-and-response-entities#http-request) パラメータを取ることもできます。 要求されたURLとヘッダを調べたい場合は、このパラメータを追加できます。

ステータスコード、フレーズ、ヘッダを設定する [HttpResponse](http-request-and-response-entities#http-response) オブジェクトパラメータを追加し、そのオブジェクトの属性を設定するか、 *HttpResponse* を返します。

マイクロフローの結果は、操作の結果であり、以下を含めることができます:

1. **Return a** ***list*** **or an** ***object***– you must specify an export mapping to convert it to XML or JSON.
2. **プリミティブを返す** – マイクロフローが値を返す場合など。 文字列、整数、またはブール値を指定すると、操作への応答がその値になります。
   {{% alert type="info" %}}
   microflow から空でない値が返された場合、 *HttpResponse* オブジェクトの *Content* 属性は無視されます。 microflow から空の値が返された場合、 *HttpResponse* の *Content* が結果として取得されます。
   {{% /alert %}}
3.  **ファイルドキュメントを返す** – ファイルであるデータ(PDFや画像など)を返却する場合 その後、マイクロフローはファイルドキュメントを返します。
4. **** [HttpResponse](http-request-and-response-entities#http-response) を返します – *HttpResponse*に ステータスコード、理由フレーズ、コンテンツ(文字列として)を設定できます。 例えば、マッピングの結果、または別のソースからの文字列を使用してコンテンツを埋めることができます。 レスポンスにヘッダーを追加することもできます。
   {{% alert type="info" %}}
   設定すべき重要なヘッダの一つは *Content-Type* です。 *空の* *HttpResponse* を返さないでください。なぜなら、それは常にエラーになるからです。
   {{% /alert %}}

マイクロフローが未処理の例外を投げた場合、レスポンスは **500: Internal server error** です。

セキュリティが有効になっている場合、マイクロフローにアクセスできるように少なくとも1つのロールが設定されている必要があります。

#### 2.1.5 非推奨

Check this box to mark the operation as deprecated in the service's OpenApi (Swagger) documentation page as described in the [Documentation](published-rest-services#interactive-documentation) section of [Published REST services](published-rest-services). これにより、クライアントはもはやそれを使用しないように通知します。

#### 2.1.6 パラメータ

You can **Add**, **Update** or **Delete** the parameters of the operation which is described in [Operation Parameters for Published REST](published-rest-operation-parameter).

##### 2.1.6.1 インポートマッピング {#import-mapping}

body パラメータの場合、リクエストの本文をオブジェクトに変換する [import mapping](import-mappings) を選択できます。 ファイルドキュメント以外のすべてのオブジェクトとリストパラメータは、インポートマッピングを選択している必要があります。

インポートマッピングを選択するには、パラメーターをダブルクリックするか、パラメーターを選択した後にグリッド内の **編集** をクリックします。 インポートマッピングを選択すると、マッピングのコミット動作を選択することもできます: コミットを選択することができます。 イベントなしでコミットするか、インポートされたオブジェクトをコミットしません。

パラメーターを取らないインポートマッピング、またはプリミティブパラメーターを取るインポートマッピングを選択することができます (例えば、文字列、整数)。 プリミティブパラメータでインポートマッピングを選択した場合、同じ型の [パスパラメータ](published-rest-path-parameters) を1つだけ持つ必要があります。 そのパスパラメータはインポートマッピングに渡されます。

**オブジェクトが見つからなかった場合、** インポートマッピングがチェックされたとき、 **マッピングが使用される場所でこれを決定する**.

XML と JSON の両方をサポートするインポートマッピングを選択すると、 (例えば、 メッセージ定義に基づくマッピング)、操作は XML と JSON リクエストの両方を処理することができます。

有効なリクエストには *Content-Type* ヘッダーを含める必要があります。 インポート マッピングによって理解されるメディア 型のリストについては、 [認識されたメディア 型](#table1) を参照してください。 サポートされていないコンテンツ型が使用されると、この操作は "**400 Bad Request**" 応答になります。

インポートマッピングは、 [JSON スキーマ](published-rest-services#interactive-documentation) に基づいて [OpenAPI (Swagger) ドキュメンテーションページ](published-rest-service-json-schema) 内で操作応答のためのオブジェクトスキーマを生成するためにも使用されます。

#### 2.1.7 対応
これは、操作の応答を定義します。 (存在する場合) マイクロフロー結果のタイプとエクスポートマッピングを指定することができます。

##### 2.1.7.1 Type
これは、マイクロフローの結果の種類を示しています。

##### 2.1.7.2 エクスポートマッピング
microflow がオブジェクトまたはオブジェクトのリストを返す場合、この結果が JSON または XML にマップされる方法を指定する必要があります。 マイクロフローの結果を入力として取得するエクスポートマッピングを選択します。

If you select an export mapping that supports both XML and JSON (for example, a mapping that is based on a message definition), then the output depends on whether the microflow has a parameter of type *System.HttpResponse* and adds a *Content-Type* header to it. 考えられるシナリオは以下の通りである。

* マイクロフローが XML のメディアタイプで *Content-Type* ヘッダーパラメーターを設定する場合。 次に、操作は以下の表のようにXMLを返します。

    <a name="table1">**メディアタイプを認識しました**</a>

    | メディアタイプ            | 認識された |
    | ------------------ | ----- |
    | *application/xml*  | XML   |
    | *text/xml*         | XML   |
    | *+xml* で終わるもの      | XML   |
    | *application/json* | JSON  |
    | *+json* で終わるもの     | JSON  |

* マイクロフローが *Content-Type* ヘッダーを別のものに設定すると、この操作は JSON を返します。

* When the microflow does not set the *Content-Type* header, then the output is determined by inspecting the *Accept* header in the request. (上のテーブルで指定されているように) XML または JSON であることが認識される最初のメディア型は、オペレーション結果を決定します: *Content-Type* は (XML である場合) *application/xml* または *application/json* (JSON である場合) です。

* When there is no *Accept* header or the *Accept* header does not contain a recognizable media type, then the operation returns JSON and the *Content-Type* is *application/json*.

エクスポートマッピングは、 [JSON スキーマ](published-rest-services#interactive-documentation) をベースにした [OpenAPI (Swagger) ドキュメント ページ](published-rest-service-json-schema) 内の操作応答のためのオブジェクトスキーマを生成するためにも使用されます。

### 2.2 公開ドキュメント

**公開ドキュメント** タブでは、サービスの [OpenAPI (Swagger) ドキュメント ページ](published-rest-services#interactive-documentation) で使用するドキュメントを指定できます。

#### 2.2.1 Summary {#summary}
操作の簡単な説明を提供します。

#### 2.2.2 説明 {#description}
操作の概要を入力します。 [GitHub風味のマークダウン](gfm-syntax) 構文を使用してテキストのスタイルを設定できます。

## 3つの例

**Studio Pro 8 で REST を公開する方法**

{{% youtube Ff_P84NOcZk %}}

