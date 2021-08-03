---
title: "Webサービスを利用する"
parent: "統合"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-web-services.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、インポートされた Web サービスについて説明します。 使用した Web サービスの画面の詳細については、 [消費された Web サービス](consumed-web-service) を参照してください。


## 2 Web サービス

Webサービス( [Wikipedia](http://en.wikipedia.org/wiki/Web_service)も参照)は、システム間で関数やデータエンティティを公開または吸収する方法です。 これらは、アプリケーションがネットワーク(またはインターネット)を介して相互に「話す」ことを可能にするために使用することができます。

MendixはSOAPを使用してサーバー間の相互作用をサポートしています。 これはMendix-to-Mendix、Mendix-to-ThirdPartyまたはThirdParty-Mendixのいずれかです。

### 2.1 消費された Web サービス

MendixではサードパーティのWebサービスを使用するのは簡単です。 別のシステム上でWebサービスを呼び出し、Mendixデータベース内でXMLをインポートする、利用可能なマイクロフローアクティビティがあります。

### 2.2 公開された Web サービス

Mendix Server の機能を公開するには (他のシステムが特定の機能を利用できるようにするため)、マイクロフローを Web サービスとして簡単に公開することができます。 詳細については、 [公開された Web サービス](published-web-services) を参照してください。

## 3 XML

システムがお互いを理解できるようにするためには、標準的な「エンコード」データの方法が必要です。 XML(eXtensible Markup Language)は、両当事者がメッセージの意味を理解できるように、データがエンコード(またはラップ)されるフォーマットです。 以下は、XML コーディングの簡単な例です。

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

この場合、オブジェクト 'person' は、属性 'name', 'age' と参照されるオブジェクト 'address' に対応する値で説明されます。

XMLは、データをエクスポートおよびインポートするために、シリアル化および非シリアル化のためにMendixで使用することができます。

XSD をアプリケーションにインポートする方法については、 [XML スキーマ](xml-schemas) を参照してください。 ドメインモデルエンティティへの XML ドキュメントのマッピングに関する詳しい情報については、  [マッピングのインポート](import-mappings) を、ドメインエンティティを XML としてエクスポートするための詳細については、 [マッピングのエクスポート](export-mappings) を参照してください。

## 4 SOAP

エンタープライズ市場では、SOAP は Web サービスの一般的なプロトコルです ( [Wikipedia](http://en.wikipedia.org/wiki/SOAP_(protocol))も参照)。 システムが相互に通信するための標準的な方法を定義します。 XML はメッセージフォーマットとして使用されます。

## 5 XSD

XSD (XML スキーマ定義) ドキュメントは、XML がどのように構造化されているかを記述するドキュメントであり、両当事者がメッセージの意味を知ることができます。 XSD 自体は XML で記述されています。

## 6WSDL

WSDL (Web Service Definition Language) ドキュメントは、クライアントがそれを公開するサーバーと対話する方法を記述するドキュメントです。 メッセージの種類(受信と送信)と、メッセージが送信されるべき場所(エンドポイント URL)を記述します。

インポートされたWebサービスを使用すると、外部アプリケーションからWebサービスをインポートして独自のアプリケーションで使用できます。 サードパーティー（ [w3schools example service](http://www.w3schools.com/xml/tempconvert.asmx?WSDL)など）や他のMendixプロジェクトからWebサービスをインポートすることができます。

これらのインポートされたWebサービスをマイクロフローで使用するには、 [Web サービスを呼び出す](call-web-service-action) を参照してください。

## 7 プロキシ

ファイアウォールの背後にいる場合は、Webサービスを呼び出すためにプロキシを使用する必要があります。 プロキシを使用するように JVM を構成する方法に関する具体的な情報は、 [プロキシを使用して Web サービスを呼び出すには](using-a-proxy-to-call-a-webservice) を参照してください。

## 8 Protocols

Mendixは、次のプロトコルに従ってWebサービスデータを消費することをサポートしています。

*   SOAP 1.1
*   SOAP 1.2
*   MTOM/XOP
*   WS-MetadataExchange v1.1
*   WS-Policy v1.2
*   WS-Policy v1.5
*   WSポリシー別紙1.5
*   WS-ReliableMessaging 1.1
*   WS-Addressing 1.0 (Mendix version 8.16から)

Microsoft .NET Web サービスに接続するには、基本的な HttpBinding (SOAP 1.1) または wsHttpBinding (SOAP 1.2) を使用するように Web サービスを設定する必要があります。 For a secure connection, you have to configure SSL and to set the security mode to `Transport` with clientCredentialType `Basic` in the **web.config** file. ユーザーの資格情報は、Studio Pro で **Web Service** アクティビティを呼び出す [HTTP 認証を使用する](call-web-service-action#http-headers) で説明されているように設定できます。
