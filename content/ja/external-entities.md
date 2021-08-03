---
title: "外部エンティティ"
parent: "ドメインモデル"
menu_order: 15
tags:
  - "ドメインモデル"
  - "エンティティ"
  - "エンティティ"
  - "属性"
  - "外部エンティティ"
  - "ハンドラーさえも"
  - "アクセスルール"
  - "studio pro"
  - "消費されたOData Service"
---

## 1つの紹介

外部エンティティは [データ ハブ ペイン](data-hub-pane) を介してドメイン モデルに追加することができます。 Domain Model では *パープル* エンティティコンテナとして表示されます。 外部エンティティは、 [Mendix Data Hub](/data-hub/) に登録されている共有データソースを通じて利用できるデータセットへのリンクを表します。 データソースは、OData サービスに公開されるエンティティセット(データセットと呼ばれる)のコレクションです。

データセットは、ソースアプリケーションでメンテナンスおよび更新されます。 アプリ開発の外部エンティティを通じて、これらのデータセットを *または* 使用できます そして、元のアプリのデータに対する変更は、使用するアプリで自動的に更新されます。

ただし、外部エンティティはローカルエンティティと一緒に使用できます。 ソースアプリケーションでデータセットが維持されているため、使用するアプリケーションですべてのプロパティを変更することはできません。

**Data Hub** ペインから外部エンティティを追加する方法に従うには、 [外部エンティティの追加](#adding-external-entities) を参照してください。

{{% alert type="info" %}}
Mendix Data Hubを使用し、アプリ内で消費されたODataサービスを介して外部データソースに接続するには、ライセンスが必要です。
{{% /alert %}}

## 2 アプリに外部エンティティを追加する {#adding-external-entities}

アプリモデルに外部エンティティを追加するには、以下の手順に従ってください:

1. アプリで使用するエンティティまたはデータソースの **データハブ** ペインでアプリモデルを検索します。

    {{% alert type="info" %}} [Data Hub Catalog](/data-hub/data-hub-catalog/search)にある OData サービスは、バージョン番号が異なる場合や、異なる環境にデプロイされる場合があります。 使用したいエンティティ(データセット)がすべて公開されます。 データハブカタログを最初に検索し、アプリの要件に最も関連するものを見つけます。{{% /alert %}}

3. ドメインモデル内の図形をドラッグ&ドロップします。

4. エンティティとその属性がアプリに追加され、 **App Explorer** に2つのドキュメントが追加されます:

    * OData サービスとメタデータの詳細を含む **消費された OData サービス** ドキュメント 表示されたロゴは、サービスの起点となるアプリを識別します
    * サービスの場所定数を指定する **OData Location**

    ![ 仮想エンティティおよびOData サービスファイル](attachments/external-entities/consumed-service-docs.png)

{{% alert type="info" %}}
ドメインモデルに既に同じサービスからエンティティに関連付けられているエンティティをドラッグすると、 エンティティの間に協会が表示され設立されます 外部エンティティ間の関連付けの詳細については、 [Associations](#properties) を参照してください。
{{% /alert %}}

詳細については、 [消費されたOData Service](consumed-odata-service) を参照してください。

**Data Hub** ペインの **App** セクションには、現在のアプリで使用されているエンティティが表示されます。

![ 仮想エンティティおよびOData サービスファイル](attachments/external-entities/data-hub-app.png)

{{% alert type="info" %}}
新しいバージョンの利用サービスがある場合は、Data Hub Catlog で利用できます。 これは、 **Data Hub** ペインにサービス名に対する更新矢印によって表示されます。 詳細については、 [OData Service](consumed-odata-service#updating) の *使用済みの OData Service* セクションを参照してください。
{{% /alert %}}

データの使用方法にのみ影響を与える外部エンティティのプロパティをローカルで変更することができます。 他のすべてのプロパティはソースアプリケーションで定義されており、変更することはできません。 同一の OData サービスからの複数の外部エンティティがモジュールまたはアプリで使用される場合 (ソース・アプリで作成された)エンティティ間の関連付けは、ローカル・モジュールで自動的に行われます。

{{% alert type="info" %}}
ドメインモデルから外部エンティティを削除する場合 サービス ドキュメントは App Explorer リストに残り、サービスは Data Hub アプリペインに引き続き表示されます。 消費されたサービスからエンティティを使用しない場合は、2つのサービスドキュメントを削除できます。
{{% /alert %}}

For more information on using published OData services and entities through the Data Hub Catalog, see [How to Consume Registered Assets](/data-hub/data-hub-catalog/consume) in the *Data Hub Guide*.

## 2 外部エンティティのプロパティ {#properties}

ローカルエンティティと比較して、外部エンティティには変更可能なプロパティが限られています。 残りのプロパティは元のアプリケーションで定義されているため、読み取り専用です。

{{% alert type="info" %}}
外部エンティティのプロパティに加えられた変更は、使用するアプリでのみ行われます。 元のアプリは変更の影響を受けません。
{{% /alert %}}

### 2.1 全般

このタブには外部エンティティの一般的なプロパティが表示されます。 元のアプリで定義されている値は表示されますが、編集できません。 編集可能な値は、ローカルアプリにのみ適用されます。

![外部エンティティのプロパティ](attachments/external-entities/external-entity-properties.png)

* **Name** – ローカルアプリ内のエンティティの名前
* **元の名前** - これは読み取り専用で、消費されたODataサービスで定義されているエンティティの名前を表示します
* **サマリー** - これは読み取り専用フィールドで、元のアプリ内のエンティティの説明を表示します

### 2.2 属性 {#attributes}

外部エンティティの OData サービスに公開されている [属性](attributes) がここにリストされています。 属性と属性リストに加えられたすべての変更は、エンティティのローカルインスタンスに適用されます。 彼らが消費されるように。 これらの変更は、エンティティが公開されている使用中のサービスのメタデータや、元のアプリ内のエンティティの属性には影響しません。

{{% alert type="info" %}} [データハブペイン](data-hub-pane#association-attributes) では、Mendixモデルでサポートされていない関連性と属性は、選択できない(グレー)として表示され、ドメインモデルにドラッグしたり、エンティティプロパティに含められるときには含まれません。 詳細については、 [Data Hub Pane](data-hub-pane#association-attributes).{{% /alert %}} を参照してください。

表示された属性リストでは、次の操作が行えます。

* **追加** - エンティティの OData サービスで公開され、このローカルインスタンスに対して以前に削除された属性を追加
* **編集** – [属性の編集](#edit-attribute) フォームから選択した属性を編集します。
* **Remove** - リストから属性を削除

#### 2.2.1 属性の編集 {#edit-attribute}

**属性の編集** ボックスは、属性のローカル名を指定し、ローカル説明を追加するために使用できます。

![属性を編集](attachments/external-entities/edit-attributes.png)

* **一般タブ**
    * **Name** – 属性のローカル名を指定できる。
    * **元の名前** - 元のアプリで与えられた属性の元の名前を表示する読み取り専用の値です。
    * **Summary** – a read-only summary displaying the description for the attribute in the originating app; to enter a local description, add this in the [Documentation tab](#documentation)
    * **** と **** と **長さ** と **最大値を入力します。 元のアプリで定義されている属性の長さ**
* **ドキュメント** - 現在のアプリのユーザーに表示される属性の説明

### 2.3 関連 {#associations}

このタブには、外部エンティティが同じサービスで公開されている他のエンティティと、ローカルエンティティで作成されたすべての関連が表示されます。 Studio Pro での関連プロパティの詳細については、 [](association-member-properties) タブを参照してください。

![属性を編集](attachments/external-entities/external-entity-associations.png)

以下は外部エンティティとのすべての関連付けに適用されます:

**Name** – name of the association as displayed in the current app **Type** – read-only for associations between two external entities **Owner** – read-only for associations between two external entities **Parent** – read-only for associations between two external entities **Child** – read-only for associations between two external entities

ローカルエンティティを持つ外部エンティティに **** と **** の関連付けを編集できます。 ただし、 *から* を外部エンティティにローカルエンティティにすることはできません。ローカルエンティティはアソシエーションの所有者でなければなりません。

アプリで外部エンティティを使用していて、このエンティティがアプリで同じODataサービスから他の外部エンティティに関連付けられている場合。 関連付けは自動的にドメインモデルに追加され、ここにリストされます。

{{% alert type="info" %}}
自動的に追加されたドメインモデル内の2つの外部エンティティ間の関連を **削除** することが可能です。 後の段階で、関連付けを復元したい場合は、 ドメインモデルで外部エンティティのいずれかを右クリックし、 **追加** > **関連** をクリックすることでこれを行うことができます。
{{% /alert %}}

{{% alert type="info" %}}
元のアプリに接続されていない2つの外部エンティティを接続する場合 データとの関係が局所的に影響を受けることができないため、これは不可能です。 ただし、ローカルエンティティを追加し、このローカルエンティティを両方の外部エンティティと接続することを検討してください。 この場合、ローカルエンティティは両方のアソシエーションの所有者でなければなりません。
{{% /alert %}}

### 2.3.1 関連プロパティ

**編集** 同一の OData サービスに公開されている 2 つのエンティティに対して含まれている関連を。 以下のプロパティが表示され、ローカル変更のみがローカル名になります:

![外部の関連付けを編集](attachments/external-entities/association-properties.png)

* **Name** – 関連付けのローカル名
* **元の名前** - 元のアプリで与えられた関連付けの読み取り専用名
* **概要** – 元のアプリからの関連付けの読み取り専用説明
* **Multiplicity** - 元のアプリからの読み取り専用多重度
* **ドキュメント** – 外部エンティティアソシエーションのローカル説明を追加するには、このタブに移動します。

### 2.3.2 二つの外部エンティティの接続

元のアプリに接続されていない2つの外部エンティティを接続する場合 データとの関係が局所的に影響を受けることができないため、これは不可能です。 ただし、ローカルエンティティを追加して、このローカルエンティティを両方の外部エンティティと接続できます。 この場合、ローカルエンティティは両方のアソシエーションの所有者でなければなりません。

### 2.4 ドキュメント {#documentation}

このタブでは、外部エンティティに関するローカル情報を追加できます。

## 3 外部エンティティの制限

外部エンティティとは、公開された OData サービスで元のアプリケーションから定義されるエンドポイントです。 消費された OData サービス ドキュメントは、 **データ ハブ** ペインを介して外部エンティティが使用された場合にサービスメタデータの値を表示します。 外部エンティティの制限は、彼らが消費のみのエンティティであるということです。 エンティティに関連付けられたデータセットは、元のアプリで維持されます。

For more details on consuming services and exposed entities, including operations that can be performed on external entities, see [How to Consume Registered Assets](/data-hub/data-hub-catalog/consume) in the *Data Hub Guide*.
