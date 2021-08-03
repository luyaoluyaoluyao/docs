---
title: "消費されたODataサービス"
parent: "consed-odata-services"
menu_order: 10
tags:
  - "studio pro"
  - "データハブ"
  - "データサービス"
  - "消費されたodata サービス"
---

## 1つの紹介

[データハブ ペイン](data-hub-pane)を介してアプリモジュールで外部エンティティが使用されている場合 消費された OData サービス ドキュメントは、消費されたサービスの詳細を指定して追加されます。 これは公開アプリへのAPIとエンティティに関連付けられたデータです。

## 2 消費された OData サービス画面

**使用済みの OData Service** ドキュメントには、次の情報が含まれています。

![接続タブ](attachments/consumed-odata-service/consumed-odata-doc-connection-tab.png)

* 元のアプリのソースアプリケーションのサービス名とアイコン

* 消費されたサービスのバージョン番号

* **View in Data Hub Catalog** link to the **Service Details** where you can see the full service details that are registred

* **更新/切り替え** - 使用中のサービス契約を、 [Mendix Data Hub](/data-hub/) で同じアプリとサービスで検出された別のバージョンに更新できます。 このボタンは、Data Hubで消費された契約に対して何が返されたかに応じて、以下を表示します。
    * **Update** – **Update** the contract that is currently consumed (and showed **Consumed OData Service** document). 現在サービスエンドポイントにある契約が表示されます。 同じエンドポイントには、小規模な非破壊的な変更のみが展開されることが良い方法です。
    *  **スイッチ** - このボタンは、同じサービスの他の登録済みインスタンスの場合に表示されます (同じ名前で)。 データハブで利用可能であり、さまざまなエンドポイントにデプロイされます (例えば、 他の環境へのアクセスや、既存のアプリの使用を妨げる変更により、以前のバージョンのアプリが使用される可能性があります)

    {{% alert type="info" %}} Studio Pro は常に **Update** オプションを表示します。 **Consumed OData Service** では、アップデートが利用可能かどうかを確認できます。 データ ハブ検索と **アプリ**  ペインで、サービス終了時に異なるコントラクトが検出されたとき。 これはサービスの更新矢印で示されます。 サービスの更新と切り替えの詳細については、このドキュメントの [更新またはOData サービスの切り替え](#updating) セクションを参照してください。 {{% /alert %}}

    {{% alert type="info" %}} **Data Hub** ペインで利用可能な **Update** を持つサービスを消費した場合、以下を示す更新矢印が表示されます。
    {{% image_container width="300" %}}![update data hub pane](./attachments/data-hub-pane/data-hub-pane-update.png){{% /image_container %}}

    {{% /alert %}}

### 2.1 接続タブ

**接続** タブには、使用した OData サービスの接続値が表示されます。

### 2.2 サービスURL {#service-url}

**サービス URL** は、サービス エンドポイントの URL を表示します。

* **Select** to select another [constant](/refguide/constants) for the service
* **表示** をクリックして、サービス URL またはエンドポイントを表示する **定数** ダイアログボックスを表示します。

    ![接続タブ](attachments/consumed-odata-service/consumed-service-constant.png)

### 2.3 タイムアウト

**タイムアウト** は、サービスエンドポイントからデータを取得するための応答時間です。 **タイムアウト**の秒数の後にエンドポイントが応答しない場合、例外が発生します。 これがマイクロフローのアクティビティ中に発生した場合、マイクロフローはロールバックされるか、カスタム [エラー処理](/howto/logic-business-rules/set-up-error-handling) に移動します。

デフォルト値: *300秒*

### 2.4 プロキシ設定

**プロキシ設定** リクエストにプロキシを使用するかどうかを設定できます。

* **アプリ設定を使用する** – アプリレベルで定義されている設定を使用する (デフォルト)
* **Override** - プロキシのホスト、ポート、ユーザー名、およびパスワード設定を指定することで、このアクションのアプリレベルの設定を上書きする
* **プロキシなし** – アプリレベルで設定されたプロキシがある場合でも、このサービスのプロキシを使用しないでください

{{% alert type="info" %}}
ほとんどの場合、この設定は無視することができ、デフォルトの **アプリ設定を使用する** が使用できます。
{{% /alert %}}

### 2.5 認証

**HTTP 認証を使用する** チェック ボックスは、基本認証を使用するかどうかを指定します。 チェックされている場合、次の詳細を指定する必要があります:

* **ユーザー名** - 認証に使用されるユーザー名を定義します
* **パスワード** - 認証に使用するパスワードを定義します。

基本認証に加えて、カスタム認証を使用できます。 詳細については、以下の [HTTP ヘッダー](#http-headers) を参照してください。

### 2.6 HTTP ヘッダー {#http-headers}

You can specify additional HTTP request headers to be passed to the endpoint in this list by clicking **Add**, **Edit**, or **Delete** for custom HTTP headers for authentication. 各カスタムヘッダーは、キーと値のペアです。

Microflow ****からのformat@@2 ヘッダーを使用して、動的な値のキーと値のペアを作成するためのマイクロフローを指定できます。 microflow は **System.HttpHeader** オブジェクトのリストを返す必要があります。

{{% alert type="info" %}}
より柔軟な HTTP リクエストヘッダーを使用するには、 **System.HttpHeader** のリストを返すマイクロフローを選択します。 このマイクロフローは、 **System.HttpResponse** 型のパラメータを取ることができます。 リクエストが行われるたびにマイクロフローが呼び出されます。 最初はHTTPレスポンスパラメータが空になります。 レスポンスが **401 Unauthorized**の場合 マイクロフローはそのHTTPレスポンスで呼び出され、別の呼び出しは新しいHTTPヘッダーで行われます。
{{% /alert %}}

{{% alert type="info" %}}
カスタム認証は、(SSOなどの)認証値が取得されるマイクロフローで行うことができます。 アクセスと認証の詳細については、 [データハブガイド](/data-hub/data-hub-catalog/security#http-header-validation) の *公開エンティティのカスタム HTTP ヘッダー検証の使用* を参照してください。
{{% /alert %}}

## 3 Metadata Tab {#metadata}

**メタデータ** タブでは、メタデータファイルを選択するか、URL で取得したメタデータを使用できます。

![Metadata Tab](attachments/consumed-odata-service/metadata-tab.jpg)

### 3.1 メタデータエディター

メタデータエディタでは、ファイルまたは URL から OData コントラクトを開くことができます。 すでにコントラクトを使用している場合、このエディターを使用して、ファイルまたはURLから新しいバージョンを使用して既存のコントラクトを更新できます。

**メタデータ エディター**を開くには、 **** をクリックします。 エディタでメタデータの URL またはファイルを指定できます:

![メタデータエディター](attachments/consumed-odata-service/metadata-editor.jpg)

次の設定を使用できます。

* **** からインポート - メタデータの場所に **URL** または **ファイル** を選択します:
    * **URL** – **Edit** をクリックしてメタデータの URL を指定します
    * **ファイル** – **参照** をクリックして XML メタデータファイルを選択します

URLからメタデータをダウンロードする場合、サーバーはユーザー名とパスワード(基本認証)を要求することができます。 その場合、ダイアログボックスにユーザー名とパスワードの入力を求められます。 メタデータファイルが同じレルム内の同じサーバー上の他のメタデータファイルを参照する場合、ユーザ名とパスワードが再利用されます。

{{% alert type="info" %}}
この情報は保存されないため、同じサーバーからメタデータを再度ダウンロードした場合。 もう一度ユーザー名とパスワードを入力する必要があります。
{{% /alert %}}

メタデータをインポートする場合、 [データハブペイン](data-hub-pane) で、消費された OData サービスから外部エンティティを追加できます。

### 3.2消費されたOData サービスプロパティ

OData サービス ドキュメントで定義されたプロパティと以下の追加プロパティを表示する OData サービスの **プロパティ** タブをクリックします。

{{% image_container width="300" %}}![](attachments/consumed-odata-service/consumed-odata-service-doc-properties.png){{% /image_container %}}

* **エンティティ** – エンティティと関連するデータセットを定義するメタデータの URL
* **ドキュメント** - 現在のアプリのこのサービスに関する追加説明
* **サービス名** – 消費される公開された OData サービスの名前
* **サービスバージョン** – 消費されるサービスのバージョン
* **Service ID** – データハブカタログのサービスの一意の識別子
* **アプリケーション ID** - サービスがデータハブカタログから公開されたアプリケーションの一意の識別子
* **メタデータ** – サービスを定義するメタデータファイルの内容
*  **OData version** – OData version: can be OData 3 or OData 4

## 4 消費されたOData サービスの更新または切り替え {#updating}

### 4.1 サービスエンドポイントからの消費{#consume-service-endpoints}

アプリに外部エンティティを追加する時 特定のバージョンのサービス（ *サービスエンドポイント*）からエンティティを消費し、指定された環境にデプロイしています。 サービスのメタデータ ファイルまたはコントラクトは、このエンドポイントにあります。

同じサービス 別の環境にデプロイされるのは、別のサービス エンドポイントになり、これはデータ ハブ カタログに異なるアセットとして登録されます。 In the following example, there are three endpoints for the **Sales 1.0.0** which is deployed to the production environment and the **Acceptance** and **Test** environments:

{{% image_container width="250" %}}![2 endpoints](attachments/consumed-odata-service/same-service-different-endpoints.png){{% /image_container %}}

When you drag the **Customer** entity from **CustomerApi version 1.0.0** deployed to the **Acceptance** environment into your app, Studio Pro will retrieve the information it requires from the contract that is at that endpoint.

### 4.2 サービスバージョンのセマンティック番号付け {#semantic}

サービスのパブリッシャーは、他のユーザーが消費する公開された OData サービスに変更を加えた場合、厳格なリビジョンプロセスを採用することが重要です。

サービスへの更新を発行する際には、厳格なバージョン管理システム(例えばセマンティック番号付け)が使用されることをお勧めします。 サービスバージョンは、サービスが更新され、以下のガイドラインに従って導入されたときに行われた変更のレベルと重大度を明示する必要があります。

#### 4.2.1 マイナーサービスの更新

*マイナー* サービスの更新は、例えば、 サービスに追加された追加項目または以前のバージョンを使用するアプリを壊さない新しい操作が含まれます。

セマンティック番号が使用される場合、サービスへのマイナー/非ブレイクの変更は、バージョン番号の小数部の増加によって示すことができます。 例えば、1.0.11、1.0.12、1.1、1.2。

マイナーなサービスのアップデートは、同じサービス エンドポイントにデプロイすることができます。これにより、消費するすべてのアプリが最新バージョンのサービスを使用できるようになります。

#### 4.2.2 メジャーサービスの更新

*主要な* サービスの更新は、エンティティまたは属性が削除された場合などです。 または入力パラメータが必要ですが、それは消費アプリには互換性がなく、消費アプリの「ブレーク」になります。

公開されたサービスに大きな変更が加えられた場合、新しいサービスバージョン番号と共に、サービスが *異なるエンドポイント* にデプロイされることをお勧めします。意味的な番号付けは全体の増加になります。

この場合、新しいサービスは別のサービスとして Data Hub カタログに登録する必要があります。 カタログに別の資産として表示されます 以下の例では、 **OrderManagementService**の4つの登録発生があります。

{{% image_container width="250" %}}![4 endpoints](attachments/consumed-odata-service/consume-major-service-update-version.png){{% /image_container %}}

**1.0.0** から **2.0.0** までのバージョン番号の変更で示されるメジャーなサービス更新があります。 さらに、 両方のメジャーバージョンは **承認** にも導入されており、別のエンドポイントでデータハブカタログに個別に登録されたアセットにもなります。

{{% alert type="info" %}}
Mendix 以外の OData サービスのエンティティは、1 つまたは複数のフィールドのキーで識別されます。 サービスの更新でキーフィールドが変更された場合、これはまた破壊的な変更と見なされます。
{{% /alert %}}

### 4.3 アップデートまたは切り替え

消費エンドポイントでのコントラクトの変更が検出された場合 (マイナーな変更による可能性があります) 同じ名前のサービスがメジャーバージョン番号で別のエンドポイントにデプロイされた場合 **OData Service** 画面では、以下のオプションが利用できます。

#### 4.3.1. 更新

**Update** オプションは、Studio Pro がカタログエンドポイントのコントラクトがアプリで現在使用されているコントラクトとは異なることを検出した場合に使用できます。 **Update** オプションが選択されている場合、新しいコントラクトはアプリにロードされます。

##### 4.3.1.1 アプリペインとデータハブ検索ペイン

**App** と **Data Hub 検索ペイン** で、カタログエンドポイントに異なるコントラクトがあるかどうかを示す更新矢印が表示されます。

![update service app-pane](attachments/consumed-odata-service/project-pane-update-available.png)

* *現在消費されている* サービスバージョンが表示されます（この例では **1.0.0**）
* Blue **Update** - クリックして **Update Service** ボックスを開き、コントラクトを新しいものに更新します。 Studio Proは、Data Hubカタログエンドポイントで新しいコントラクトを取得し、これはアプリにロードされます。
* この新しいバージョンのデータハブ内のエンティティのリストが表示されます。 緑色のチェックマークが付いているローカルで消費されているエンティティを含む。 ただし、これらのエンティティはあります。 以前のバージョンのコントラクトが消費されているため、ドメインモデルにドラッグできないことを示すグレー表示されています。 唯一のオプションは、 **Update** をクリックして更新された OData サービスを取得することです。

##### 4.3.1.2 サービスの更新ダイアログ ボックス

When you click **Update** on the **Consumed OData Service** document or the update icon in the **Data Hub** and **App** sections, the **Update** dialog box is displayed.

![更新サービス dhpane](attachments/consumed-odata-service/update-service-dialog-box.png)

The consumed OData service that is currently consumed in the app (**1.0.0**) is shown on the left, and you can click **Update** to retrieve the new contract from the Data Hub (**2.0.0**).

#### 4.3.2. 切り替え

OData サービスが別のエンドポイントまたは別の環境に公開されると、データハブカタログに別のアセットとして登録されることになります。

In the example given in the [Consuming from Service Endpoints](#consume-service-endpoints) section above, if you are consuming the service from the **Acceptance** environment, the Consumed OData service screen will display the **Switch** button to enable you to consume the same service from the **Production**.

#### 4.3.3 消費したサービスの切り替え

複数の環境にデプロイされている、または主要なサービスアップデートで公開されている公開済みの OData サービスは、 **Data Hub** ペインの検索結果に別の項目として表示されます。

以下の例では、 **Orders** バージョン **1.0.0** を **Test** 環境にデプロイした場合、アプリで使用されます。 しかし、同じサービスは **Acceptance** 環境にデプロイされます。

![大きな変化環境](attachments/consumed-odata-service/consume-major-service-update.png)

**Acceptance 環境**にデプロイされたサービスを利用するには、以下の手順に従ってください。

1. **Update** > **Switch** on the **Consumed OData Service** document:

    ![大きな変化環境](attachments/consumed-odata-service/update-switch.png)

2. On the **Switch** dialog box, from the drop-down list, select the service that you want to consume from (note that an endpoint is also detected that is deployed to **Production**) and click **Switch**:

    ![大きな変化環境](attachments/consumed-odata-service/switch-environment.png)

3. 消費されたサービスは、選択された新しい環境から消費されます。 **消費された OData Service** ドキュメントの情報に変更されたサービスの詳細が表示され、 **データハブ** ペインに、選択した環境から消費していることが表示されます。

    {{% image_container width="300" %}}![major change environment dh pane](attachments/consumed-odata-service/switch-new-environment.png){{% /image_container %}}

## 5 続きを読む

* [データハブペイン](data-hub-pane)
* [消費されたODataサービス](consumed-odata-service)
