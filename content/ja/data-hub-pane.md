---
title: "データハブペイン"
parent: 表示メニュー
menu_order: 15
description: "Mendix Studio Proのデータハブペインについて説明します。"
tags:
  - "studio Pro"
  - "データハブ"
  - "データハブペイン"
  - "データハブカタログ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/data-hub-pane.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

[Mendix Data Hub](/data-hub/) を使用すると、組織内のさまざまなアプリケーションから利用可能なデータソースを Mendix アプリに統合できます。 これは、 [Data Hub Catalog](/data-hub/data-hub-catalog/) に登録されている共有データセットを使用して新しいアプリケーションを作成できることを意味します。 Studio Pro では、 **Data Hub** ペインを通じて、Data Hub Catalog の統合機能を使用できます。

{{% alert type="info" %}}
Studio Pro で Data Hub を使用するには、ライセンスが必要です。 詳細については、 [Data Hub License](consumed-odata-service-requirements#license-limitations) を参照してください。
{{% /alert %}}

[ **Data Hub** ] ペインからデータハブカタログを検索して、プロジェクトで使用できるデータ ソースを検出できます。 このペインを使用すると、データハブの **データ ソース** と呼ばれる登録済みの OData サービスに公開されているエンティティをアプリケーションのドメイン モデルに追加できます。 これらのエンティティは [外部エンティティ](external-entities) と呼ばれ、元のアプリでエンティティに関連付けられているデータへの接続を有効にするために異なります。

{{% alert type="info" %}}
In the Data Hub Catalog, registered published services are referred to as *data sources* and exposed entities will show the **Entity set** name and are called *datasets.*
{{% /alert %}}

**Data Hub** ペインを表示するには、 **View** > **Data Hub**:

{{% image_container width="300" %}}![data-hub-pane](attachments/data-hub-pane/data-hub-pane-empty.png){{% /image_container %}}

## 2領域モデルのデータハブペイン

データハブペインは、アプリでドラッグして使用できるエンティティと、現在のモデルで消費されている外部エンティティと関連するサービスを表示するためにデータハブカタログを検索するために使用されます。

### 2.1 データハブ検索

{{% image_container width="300" %}}![](attachments/data-hub-pane/data-hub-pane.png){{% /image_container %}}

ペインでは、次の機能を使用できます。

* [検索](#search) – データハブカタログで検索する英数字の検索文字列を入力します。 検索は、カタログのサービス、エンティティ、属性、関連付け、および説明で実行されます。

* [フィルター](#search) – デフォルトでは、 **プロダクション** 環境のアセットに対して検索が実行されます。 Click the **Filter** icon to include all other environments such as test, acceptance and also the Mendix free app environment **Sandbox** in the search.

* [検索結果](#viewing) – 検索結果は、検索文字列を満たすカタログ内のすべての要素を表示します。 「ヒット」ごとに表示される情報には、サービス名、サービスのバージョンが含まれます。 サービスがデプロイされた環境と、検索文字列に一致する要素。 検索条件を満たす属性または関連性があれば、それらが表示されます。 検索結果からドメインモデルにドラッグすると、 [外部図形](external-entities)として表示されます。

![](attachments/data-hub-pane/external-entity.png)

  現在のドメインモデルで使用されているサービスとエンティティは、検索結果に緑色のチェックマークが表示されます。

### 2.2 データハブプロジェクトペイン

**Data Hub** ペインで検索文字列が指定されていない場合、 **プロジェクト** ペインが表示されます。 これは、現在のプロジェクトで使用されている使用済みサービスと外部エンティティを示します。 使用したサービスのエンティティ、関連付け、属性のリストは、検索結果として表示されます。

{{% image_container width="300" %}}![Project Section](attachments/data-hub-pane/project-section.png){{% /image_container %}}

プロジェクトモデルにエンティティを追加するには、 [プロジェクトへの外部エンティティの追加](external-entities#adding-external-entities) を参照してください。

## 3 データハブカタログの検索 {#search}

検索語句を入力すると、検索文字列を満たす[Data Hub Catalog]内のすべての項目が検索結果に表示されます。 これには、サービス内の単語、エンティティ、データハブペインに表示されない属性説明が含まれます。 詳細については、 [Data Hub Catalog asset details](/data-hub/data-hub-catalog/search#search-details) を参照してください。

### 3.1 ワイルドカード検索
検索エリアに `*` と入力することでワイルドカード検索ができます。

{{% alert type="info" %}}
検索文字列は英数字3文字以上でなければなりません。 検索語句はワイルドカード文字 `*` データハブカタログで「空」検索を実行する場合を除き、検索語句の一部として使用できません。 他の文字と組み合わせてワイルドカードを使用することはできません。 詳細については、 [登録資産を検索する方法](/data-hub/data-hub-catalog/search) を参照してください。
{{% /alert %}}

### 3.2 サービス環境
By default, the search will be performed on assets in the **Production** environment. To include all other environments such as test, acceptance, and also the Mendix free app environment, **Sandbox** in the search, click the **Filter** icon and check **Show development environments**:

{{% image_container width="300" %}}![Filter Icon](attachments/data-hub-pane/filter-icon.png){{% /image_container %}}

{{% alert type="info" %}}
**開発環境を表示** にチェックが入っている場合、以降の検索結果はすべて非本番環境でも表示されます。
{{% /alert %}}

## 検索結果とプロジェクトペインの4つの情報 {#viewing}

以下の情報が表示されます。

### 4.1 サービス

検索結果とプロジェクトペインには次のものがサービスレベルで表示されます:

* **サービス名**

*  **サービスのアプリケーション アイコン** (例えば、Mendix、SAP、Siemens Teamcenter、または上のスクリーンショット、カスタムアイコンに表示されているように)

* **サービスのバージョン**

*  **非生産環境の環境名**

    {{% alert type="info" %}}非本番環境の名前のみが表示されます。 **Production** のサービスには環境名は表示されません。 {{% /alert %}}

* **プロジェクト内でサービスまたはエンティティが消費されている場合、緑色のチェックマーク**。 使用中のサービスを右クリックすると、次の操作ができます。

  {{% image_container width="250" %}}![info on a Service](attachments/data-hub-pane/data-hub-pane-menu.png){{% /image_container %}}

  * **View in Data Hub Catalog** – クリックすると **Data Source Details** ページに移動します
  * **接続設定に移動** - これをクリックして [OData サービスを使用](consumed-odata-service) ドキュメントを開きます

*  **Blue** **Update Service** アイコンは、Data Hub で利用可能な消費されたサービスの別のバージョンがあることを示します。 クリックして、プロジェクトで使用されているサービスを、現在利用可能な限月に更新します。

    ![データハブペインの更新](attachments/data-hub-pane/data-hub-pane-update.png)

    {{% alert type="info" %}}OData Service の更新が利用可能な場合。 リストされているエンティティは、そのバージョンの OData サービスで利用可能なエンティティです。 これらのエンティティは、プロジェクトで消費される *現在の* コントラクトがこれらのエンティティを持たないため、ドメインモデルにドラッグできないことを示すために「グレーアウト」になります。 **Update** をクリックして、検索結果に表示されるバージョンにコントラクトを更新する必要があります。 アロー! {{% /alert %}}

  {{% alert type="info" %}}The version number that is shown for the OData service is the latest one that is available in the Data Hub Catalog at the service endpoint—in the example above version 1.0.11 of **Theatre_service** is currently consumed in the project, but version **1.0.12** is now available in the Data Hub Catalog. 検索結果には、新しいサービスで利用可能なエンティティ(ローカルで消費されるエンティティも表示されます)が表示されますが、それらはグレーアウトされており、ローカルサービスが **アップデート** されるまで選択できません。 {% /alert %}}

* **情報アイコン** は、サービスの詳細とデータハブカタログの [サービス詳細](/data-hub/data-hub-catalog/search#search-details) 画面に直接移動するリンクを表示します。

  {{% image_container width="250" %}}![Data Hub Pane Information](attachments/data-hub-pane/data-hub-pane-info.png){{% /image_container %}}

### 4.2 エンティティ、属性、および関連 {#association-attributes}

検索文字列を満たすエンティティ、属性、関連性が検索結果に表示されます。

リスト内の任意のサービスに対応 **:詳細を表示する** をクリックすると、公開されたエンティティとそのサービスの関連付けと属性の完全なリストが表示されます。

{{% alert type="info" %}}Mendixモデルでサポートされていない関連付けと属性は選択できない(グレー)として表示され、ドメインモデルにドラッグすると含まれません。 {% /alert %}}

{{% image_container width="250" %}}![Data Hub Pane Information](attachments/data-hub-pane/expand-service-list.png){{% /image_container %}}

### 4.2.1 エンティティ
If you right-click an entity and select **View in Data Hub Catalog**, it will take you to the entity details page in the [Data Hub Catalog](/data-hub/data-hub-catalog/).

消費されたエンティティを右クリックして **エンティティ**に移動すると、ドメインモデル内のエンティティに移動します。

### 4.2.2 関連

サービスに公開されている関連は、属性の前にアルファベット順にリストされています。 **+** をクリックすると、関連付けられているエンティティが表示されます。

**同一エンティティ間のマルチプル関連**s は、単一の関連付けの前に表示される。

次の例では、エンティティ **顧客** はエンティティと複数の関連を持っています。 **注文** これらの関連付けはサポートされておらず、モデルでは使用できません」

{{% image_container width="250" %}}![multiple associations](attachments/data-hub-pane/multiple-assocs.png){{% /image_container %}}

### 4.2.3 属性

サービスの属性はアルファベット順に表示されます。 使用されたエンティティの属性を右クリックし、 **属性に移動**、 ドメインモデルの属性に移動します

上の例では、2つの属性があります。 **アドレス** および **お気に入り** はサポートされていないため、モデルには含まれません。

{{% image_container width="300" %}}![multiple associations](attachments/data-hub-pane/unsupported-attributes.png){{% /image_container %}}

## 5 続きを読む

* [データハブカタログ](/data-hub/data-hub-catalog)
* [外部エンティティ](external-entities)
* [消費されたODataサービス](consumed-odata-service)
* [登録資産を消費する方法](/data-hub/data-hub-catalog/consume)
