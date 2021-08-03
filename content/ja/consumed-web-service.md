---
title: "利用済みのWebサービス"
parent: "consed-web-services"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-web-service.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このドキュメントでは、インポートされた Web サービスのプロパティについて説明します。 インポートされた Web サービスの概要については、 [Web サービス](consumed-web-services) の概要ドキュメントを参照してください。

## 2つのWSDL ソース

WSDL は URL またはディスクに保存された WSDL ファイルからロードすることができます。

{{% alert type="warning" %}}

認証が必要なURLからWSDLファイルをロードしようとすると、ユーザー名とパスワードが要求されます。

{{% /alert %}}{{% alert type="warning" %}}

WSDL ファイルには複数のサービスが含まれていて、サービスには複数のポートが含まれている場合があります。 WSDLをロードすると、ダイアログボックスで複数のポートを含む各サービスのポートを選択するように求められます。

{{% /alert %}}

## 3つのサービス

この部分は、WSDL で見つけるサービスを指定します。

* **Name** – サービスの名前。
* **ポート** – 選択したポート。
* **場所** - サービスがある場所。
* **ロケーション定数** - の場合、サービスの追加のロケーションを追加するために使用できます。 たとえば、開発環境から本番環境へ移動すると、SOAP サービスの URL が変更される場合などです。 [定数](constants) も参照してください。

WSDLに複数のポートサービスが定義されている場合、ポップアップダイアログボックスで使用するポートを選択できます。

## 4つの操作

この部分は、WSDLで見つかったすべての操作を示しています。 リストを展開し、右側のペインで個々の操作に関する追加情報を表示できます。

## 5つの詳細設定

**添付ファイル(MTOM)** でバイナリデータを送信する (_メッセージ送信最適化メカニズム_):Webサービスとの間でバイナリデータを効率的に送信する方法。 詳細は [w3.org](https://www.w3.org/TR/soap12-mtom/) をご覧ください。

{{% alert type="warning" %}}

メッセージの最適化は、呼び出しの Web サービスアクション内でリクエストボディを作成するために 1 つまたは複数のエクスポートマッピングを使用する場合にのみ適用されます。

{{% /alert %}}

## 6 Web サービスを通話中

使用している Web サービスを呼び出す方法については、 [Web サービスを呼び出す](call-web-service-action) を参照してください。
