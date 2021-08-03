---
title: "Webサービスを利用する"
parent: "統合"
---

{{% alert type="warning" %}}

このドキュメントでは、インポートされた Web サービスについて説明します。 消費されたWebサービスの画面で特定の情報を探している場合は、 [利用されたWebサービス](consumed-web-service) ドキュメントを確認できます。

{{% /alert %}}

## Web サービス

Webサービス( [wikipedia](http://en.wikipedia.org/wiki/Web_service)も参照)は、システム間で関数やデータエンティティを公開または吸収する方法です。 これらは、アプリケーションがネットワーク(またはインターネット)を介して互いに「話す」ことを可能にするために使用できます。

MendixはSOAPを使用してサーバー間の相互作用をサポートしています。 これはMendix-to-Mendix、Mendix-to-ThirdPartyまたはThirdParty-Mendixのいずれかです。

### 使用済みのウェブサービス

MendixではサードパーティのWebサービスを使用するのは簡単です。 別のシステムでWebサービスを呼び出し、Mendixデータベース内でXMLをインポートするマイクロフローアクティビティが利用できます。

### 公開された Web サービス

Mendixサーバの機能を公開するには(他のシステムが特定の機能を利用できるようにするため)、マイクロフローをWebサービスとして簡単に公開することができます。 [公開された Web サービス](published-web-services) を参照してください。

## XML

システムがお互いを理解できるようにするためには、標準的な「エンコード」データの方法が必要です。 XML(eXtensible Markup Language)は、両当事者がメッセージの意味を理解できるように、データがエンコード(またはラップ)されるフォーマットです。 簡単な例:

```xml
<person>
    <name>John Smith</name>
    <age>23</age>
    <address>
        <street>Dopeylane 14</street>
        <city>Worchestire</city>
    </address>
</person>
```

オブジェクト 'person' の上には、属性 'name' 、'age' 、参照されるオブジェクト 'address' に対応する値が記述されています。

XMLは、データをエクスポートおよびインポートするために、シリアル化およびデシリアライゼーションのためにMendixで使用することができます。

XSD をアプリケーションにインポートする方法については、 [XML スキーマ](xml-schemas) を参照してください。 ドメインエンティティへの XML ドキュメントのマッピングに関する情報については  [マッピングのインポート](import-mappings) を、ドメインエンティティを XML としてエクスポートする情報については [マッピングのエクスポート](export-mappings) を参照してください。

## SOAP

エンタープライズ市場では、SOAP は Web サービスの一般的なプロトコルです ( [wikipedia](http://en.wikipedia.org/wiki/SOAP_(protocol))も参照)。 システムが互いに通信する方法を知る標準的な方法を定義します。 XML はメッセージフォーマットとして使用されます。

## XSD

XSD (XML スキーマ定義) ドキュメントは、XML がどのように構造化されるかを記述するドキュメントであり、両当事者がメッセージの意味を知ることができます。 XSD 自体は XML で記述されています。

## WSDL

WSDL (Web Service Definition Language) ドキュメントは、クライアントがそれを公開するサーバーと対話する方法を記述するドキュメントです。 メッセージの種類(受信と送信)と、メッセージが送信されるべき場所(エンドポイント URL)を記述します。

インポートされたWebサービスを使用すると、外部アプリケーションからWebサービスをインポートして、独自のアプリケーションで使用できるようにできます。 サードパーティー（ [w3schools example service](http://www.w3schools.com/xml/tempconvert.asmx?WSDL)など）や他のmendixプロジェクトからウェブサービスをインポートすることができます。

インポートされたWebサービスをマイクロフローで実際に使用するには、 [Web Service Action](call-web-service-action) を参照してください。

## プロキシ

ファイアウォールの背後にいる場合は、Webサービスを呼び出すためにプロキシを使用する必要があります。 プロキシを使用するようにJVMを構成する方法に関する具体的な情報はこちら [](using-a-proxy-to-call-a-webservice)

## Protocols

Mendixは、次のプロトコルに従ってWebサービスデータを消費することをサポートしています。

*   SOAP 1.1
*   SOAP 1.2
*   MTOM/XOP
*   WS-MetadataExchange v1.1
*   WS-Policy v1.2
*   WS-Policy v1.5
*   WSポリシー別紙1.5
*   WS-ReliableMessaging 1.1

Microsoft .NET Web サービスに接続するには、基本的な HttpBinding (SOAP 1.1) または wsHttpBinding (SOAP 1.2) を使用するように Web サービスを設定する必要があります。 セキュアな接続のためには、SSL を構成し、「web.config」ファイル内の clientCredentialType 'Basic' を使用してセキュリティモードを 'Transport' に設定する必要があります。 ユーザーの資格情報は、モデラーでここで説明されている [として構成することができます](call-web-service-action) (「HTTP 認証を使用する」を参照してください)。
