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

この機能はバージョン7.10.0で導入されました。

{{% /alert %}}

## 1つの紹介

公開された REST 操作は、 [公開された REST リソース](published-rest-resource) の一部であり、クライアントが取得するために呼び出すことができるエンドポイントを定義します。 リソースからアイテムを追加、投稿、パッチ適用、削除します。

このドキュメントでは、 *リソースの追加操作* ポップアップダイアログを介してREST操作を構成する際のオプションについて説明します。

## 2つの全般

### 2.1 方法

このメソッドは、マイクロフローによって実行される操作の種類を指定します。

* 'GET' – 指定された場所のエントリまたはエントリを取得します
* 'PUT' – 操作は、指定された場所にエントリまたはエントリを置き換えるか、存在しない場合にそれらを作成します
* 'POST' – 操作は、指定された場所にコレクション内のエントリを作成します
* 'PATCH' – 指定された場所のエントリを更新する操作（一部）
* 'DELETE' – 指定された場所のエントリまたはエントリを削除します
* 'HEAD' - 指定された場所のエントリまたはエントリに関する情報を取得します。 これは _GET_と同じですが、メッセージ本文を返さないことを除きます
* 'OPTIONS' - 操作は利用可能な通信オプションに関する情報を返します

### <a name="operation-path"></a>2.2 操作パス

操作が行える場所は、リソースの場所から始まります。

操作パスは、操作の残りの場所を指定します。 リソースの場所を使用するには、空のままにしておいてください。

[パスパラメーター](published-rest-path-parameters) を使用して、ロケーションの一部をマイクロフローパラメーターとして、またはインポートマッピングのパラメーターとしてキャプチャすることができます。 '{' and '}' の間の操作パスにパスパラメータを指定します。 pathパラメータの場所にあるURL内にあるものは、マイクロフローまたはインポートマッピングに渡されます。

The method and operation path determine [which operation gets executed for a given request URL](published-rest-routing).

### <a name="example-location"></a>2.3 場所例

場所の例では、操作に到達できる URL の例を示します。 これは '{' and '}' の間のパスパラメータとクエリパラメータ値をプレースホルダとして表示します。

### 2.4 マイクロフロー

{{% alert type="info" %}}

これらのマイクロフローでの **File Documents** のサポートは、バージョン 7.13.0 で導入されました。

{{% /alert %}}

操作に異なるパラメータがあります。

 * [パスパラメータ](published-rest-path-parameters)(URL のパスの一部)
 * [クエリパラメータ](published-rest-query-parameters), `の形式でURLの末尾にあるもの? ame1=value1&name2=value2` (microflow パラメータがパスになく、オブジェクトではない場合、クエリパラメータと見なされます)
 * リクエストの HTTP ヘッダーから来るヘッダーパラメータ
 * 操作へのリクエストの本文内にあるbodyパラメータ(オプション)（「GET」） 'HEAD'と'DELETE'演算はbodyパラメータを持っていません)。 *List* または *Object* 型を持つことができるのは、body パラメータのみです。

オペレーションのマイクロフローは、これらのオペレーションパラメータを入力とします。

*リスト* または *オブジェクト* 型を持つマイクロフローパラメータは、body パラメータを示します。 インポートマッピングを指定して、受信する JSON または XML を変換できます。 パラメーターがファイルドキュメントである場合、またはファイルドキュメントから継承される場合、インポートマッピングは必要ありません。

オペレーションマイクロフローは、 [HttpRequest](http-request-and-response-entities#http-request) パラメータを取ることもできます。 リクエストされたURLとヘッダを調べたい場合は、このパラメータを追加できます。

To set the status code, reason phrase, and headers, you should add an [HttpResponse](http-request-and-response-entities#http-response) object parameter and set the attributes of that object, or return an *HttpResponse*.

マイクロフローの結果は、操作の結果です。 ここにはいくつかのオプションがありますが、以下で説明します。

最初のオプションは *** *リスト* または ***オブジェクト****** を返します。 XML または JSON に変換するには、エクスポートマッピングを指定する必要があります。

2 番目のオプションは **がプリミティブ** を返すことです。 microflow が文字列、整数、Booleanなどを返すと、その操作への応答がその値になります。 microflowから空でない値を返す場合、 *HttpResponse* オブジェクトの *Content* 属性は無視されます。 If you return an empty value from the microflow, then the *Content* of the *HttpResponse* is taken as the result.

3つ目のオプションは、 **ファイルドキュメント**を返すことです。 ファイルであるデータ(PDFや画像など)を返却したい場合 マイクロフローにファイルドキュメントを返してもらうことができます。

最後のオプションは **が [HttpResponse](http-request-and-response-entities#http-response)**を返すことです。 *HttpResponse*では、ステータスコード、理由フレーズ、およびコンテンツ(文字列として)を設定できます。 例えば、マッピングの結果、または別のソースからの文字列を使用してコンテンツを埋めることができます。 レスポンスにヘッダーを追加することもできます。 設定すべき重要なヘッダの一つは *Content-Type* です。 *空の* *HttpResponse*を返さないでください。なぜなら、それは常にエラーになるからです。

マイクロフローが未処理の例外を投げた場合、レスポンスは **500: Internal server error** です。

セキュリティが有効になっている場合、マイクロフローにアクセスできるように少なくとも1つのロールが設定されている必要があります。

### 2.5 非推奨

このボックスにチェックを入れると、この操作はサービスの [OpenApi (Swagger) ドキュメント ページ](published-rest-services#interactive-documentation) で非推奨としてマークされます。 これはクライアントにもはやそれを使用しないように指示します。

### 2.6 パラメータ

{{% alert type="info" %}}

この機能はバージョン7.12.0で導入されました。

バージョン7.17.0でパラメータの編集機能が導入されました

{{% /alert %}}

このリストでは、操作 [の](published-rest-operation-parameter)パラメータの追加、更新、削除ができます。

<a name="import-mapping"></a>

### 2.6.1 インポートマッピング

{{% alert type="info" %}}

この機能はバージョン7.14.0で導入されました。 バージョン 7.17.0 では、パラメータを取るインポートマッピングを使用することが導入されました。

{{% /alert %}}

body パラメータの場合、リクエストの本文をオブジェクトに変換する [import mapping](import-mappings) を選択できます。 ファイルドキュメント以外のすべてのオブジェクトとリストパラメータは、インポートマッピングを選択する必要があります。 インポートマッピングを選択するには、パラメーターをダブルクリックするか、パラメーターを選択した後にグリッド内の **編集** をクリックします。 インポートマッピングを選択すると、マッピングのコミット動作を選択することもできます。 コミット、イベントなしでコミット、またはインポートされたオブジェクトのいずれかを選択できます。

パラメータを取らないインポートマッピング、またはプリミティブパラメーター (文字列、整数など) を取るインポートマッピングを選択することができます。 プリミティブパラメータでインポートマッピングを選択した場合、同じ型の [パスパラメータ](published-rest-path-parameters) を1つだけ持つ必要があります。 そのパスパラメータはインポートマッピングに渡されます。

**オブジェクトが見つからなかった場合、** インポートマッピングがチェックされたとき、 **マッピングが使用される場所でこれを決定する**.

XML と JSON の両方をサポートするインポートマッピングを選択した場合 (インスタンス) メッセージ定義に基づくマッピング)、操作は XML と JSON リクエストの両方を処理することができます。

有効なリクエストには *Content-Type* ヘッダーを含める必要があります。 インポート マッピングによって理解されるメディア 型のリストについては、 [テーブル 1: 認識されたメディア 型](#table1) を参照してください。 サポートされていないコンテンツ型が使用されている場合、操作は "400 Bad Request" レスポンスになります。

インポートマッピングは、 [JSON スキーマ](published-rest-services#interactive-documentation) に基づいて [OpenAPI (Swagger) ドキュメンテーションページ](published-rest-service-json-schema) 内で操作応答のためのオブジェクトスキーマを生成するためにも使用されます。

### 2.7 対応

{{% alert type="info" %}}

**OpenAPI (Swagger)** でのエクスポートマッピングとモデルのサポートが 7.14.0 で追加されました。

{{% /alert %}}

これは、操作の応答に関する情報を表示します。 マイクロフローの結果の型を見ることができますし、(存在する場合) 適用されたエクスポートマッピングも見ることができます。

#### 2.7.1 Type

これは、マイクロフローの結果の種類を示しています。

#### 2.7.2 エクスポートマッピング

microflow がオブジェクトまたはオブジェクトのリストを返す場合、この結果が JSON または XML にマップされる方法を指定する必要があります。 マイクロフローの結果を入力として取得するエクスポートマッピングを選択します。

If you select an export mapping that supports both XML and JSON (for instance, a mapping that is based on a message definition), then the output depends on whether the microflow has a parameter of type *System.HttpResponse* and adds a *Content-Type* header to it. 以下のシナリオが考えられます:

* マイクロフローが *Content-Type* ヘッダーに XML のメディアタイプを設定する場合 (次を参照してください: [テーブル 1: 認識されたメディア タイプ](#table1)) その後、操作はXMLを返します
* マイクロフローが *Content-Type* ヘッダーを他のヘッダーに設定すると、操作は JSON を返します。
* When the microflow does not set the *Content-Type* header, then the output is determined by inspecting the *Accept* header in the request: the first media type that is understood to be XML or JSON (see see [Table 1: Recognized media types](#table1)) determines the operation result, and the *Content-Type* is *application-xml* (when it's XML) or *application-json* (when it's JSON)
* When there is no *Accept* header or the *Accept* header does not contain a recognizable media type, then the operation returns JSON and the *Content-Type* is *application/json*

| メディアタイプ            | 次のユーザとして再割り当て: |
| ------------------ | -------------- |
| *application/xml*  | XML            |
| *text/xml*         | XML            |
| *+xml* で終わるもの      | XML            |
| *application/json* | JSON           |
| *+json* で終わるもの     | JSON           |

<a name="table1"></a>**表1: 認識されたメディアタイプ**

エクスポートマッピングは、 [JSON スキーマ](published-rest-services#interactive-documentation) をベースにした [OpenAPI (Swagger) ドキュメント ページ](published-rest-service-json-schema) 内の操作応答のためのオブジェクトスキーマを生成するためにも使用されます。

## 3 公開ドキュメント

公開ドキュメントは、サービスの [OpenAPI (Swagger) ドキュメント ページ](published-rest-services#interactive-documentation) で使用されます。

### <a name="summary"></a>3.1 Summary

要約には、操作の動作についての簡単な説明があります。

### <a name="description"></a>3.2 説明

この説明では、操作が何をするかの完全な概要を示します。 リッチテキストには、 [GitHub風味のマークダウン](gfm-syntax) を使用できます。

## 4つの例

**MendixでネイティブにRESTを公開する方法**

{{% youtube HzrFkv0U4n8 %}}
