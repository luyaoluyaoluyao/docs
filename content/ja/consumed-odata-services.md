---
title: "消費されたODataサービス"
parent: "統合"
description: "Studiosで消費されるODataサービスの概要"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-odata-services.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

データは、 [公開されたOData services](published-odata-services)を通じて他のアプリが使用するためにアプリから公開することができます。 消費された OData サービスを使用して、 [Mendix Data Hub](/data-hub/) を介してアプリケーションに外部データソースを統合できます。

Mendix Data Hubを使用すると、組織内のさまざまなソースからの利用可能なデータソースをMendixアプリに統合できます。  [Data Hub Catalog](/data-hub/data-hub-catalog/) に登録された OData サービスは、外部エンティティとして [Data Hub ペイン](data-hub-pane) を介してドメインモデルにドラッグアンドドロップできるエンティティを公開します。 プロジェクトに追加された OData サービス ドキュメントは、サービスおよび公開されているエンティティのメタデータを取得するための情報を提供します。

使用済みの OData サービス ドキュメントとプロジェクト内の使用済みの OData サービスの更新の詳細については、 [消費された OData サービス](consumed-odata-service) を参照してください。

{{% alert type="info" %}}
Mendix Data Hubはライセンスされた製品です。 外部エンティティを使用して OData サービスを利用するには、ライセンスが必要です。 を選択すると、ライセンスの種類によって、データレコードの消費数が定義されます。  詳細については、 [OData サービス要件](consumed-odata-service-requirements#license-limitations) の *データハブライセンス制限* セクションを参照してください。 Data Hub ライセンスの詳細については、 [Mendix Support](https://support.mendix.com) までお問い合わせください。
{{% /alert %}}

公開された OData サービスがサポートしなければならない機能の詳細と、Mendix データモデルからの変換とその仕組みについての詳細。 [消費された OData サービス要件](consumed-odata-service-requirements) を参照してください。

## 2 OData サービスおよび外部エンティティ

外部エンティティがアプリで使用されている場合 エンティティに関連付けられたデータセットは、消費された OData サービス契約内の情報から取得され、返されます。

### 2.1 外部エンティティ

外部エンティティには持続可能エンティティと比較していくつかの制限があります:

* 外部エンティティは読み取り専用です
* 集計関数（平均、合計、最大、最小）は外部エンティティでは使用できません
* XPath の制約には、外部エンティティには一定の制限があります(例えば、 持続可能エンティティと外部エンティティの関連付けをフィルタリングすることはできません)
* 外部エンティティはデータセットでは使用できません
* [外部エンティティのアクセスルールの XPath 制約](/refguide8/xpath-constraints) を設定することはできません

外部エンティティ(元のアプリで定義されている)間の関連付けは、ドメインモデルに表示されます。 双方が露出している団体のみを使用できます。

ローカル [持続可能エンティティ](persistability#persistable) と外部エンティティの間の関連付けを作成できます。 これらの関連付けの場合、持続可能エンティティは所有者である必要があります。

### 2.2 消費されたOData サービス

外部エンティティがドメインモデルにドラッグされたとき。 モデルに追加された  **消費されたOdata** ドキュメントには、サービスエンドポイントからメタデータコントラクトの値が表示されます。

**Data Hub** ペインでは、サービスとエンティティは、検索結果ペインと **プロジェクト** パネルの両方で使用されていると表示されます。

指定したサービス エンドポイントのメタデータ コントラクトが現在のプロジェクト モデルのコントラクトと異なる場合。 これは、青 **データ ハブ** ペインの検索結果と、  **プロパティ** ペイン **更新** 矢印:

![データハブペインの更新](attachments/data-hub-pane/data-hub-pane-update.png)

![update service project-pane](attachments/consumed-odata-service/project-pane-update-available.png)

つまり、消費されたサービスは新しいコントラクトに **更新** する必要があります。 これが行われていない場合は、古い契約に基づいてデータをエンドポイントから取得する必要がある場合にエラーが発生します。 消費された OData サービス契約の変更は、 [消費された OData サービスの更新または切り替え](consumed-odata-service#updating) で詳しく説明されています。

## 3つのランタイムについての考慮事項

サービスエンドポイントは、消費されたODataサービスのすべての検索に対して呼び出されます。 したがって、消費された外部エンティティのデータ検索は、ローカルの持続可能エンティティよりも遅くなる可能性があります。
