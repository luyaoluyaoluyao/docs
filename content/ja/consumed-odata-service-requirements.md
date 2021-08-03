---
title: "消費された OData サービス要件"
parent: "consed-odata-services"
menu-order: 20
description: "Mendixで消費されるODataサービスの要件。"
tags:
  - "studio pro"
---

## 1つの紹介

このドキュメントでは、消費される予定の OData サービスの要件について説明します。 これらの要件は、実行時にさらに検証されず、保持することが期待されます。 これらの要件が満たされない場合、エラーが発生する可能性があります。

## 2消費されたODataサービスの要件

Mendix アプリで使用される消費された OData サービスの要件は次のとおりです。

* OData サービスは、Atom XML を返すOData v3 サービスまたは Atom XML または JSON を返すOData v4 サービスである必要があります。
* It should support queries on the OData feed, including `$filter`, `$orderby`, `$top`, `$skip`, `$expand`, and `$count` (or `$inlinecount`)

## サービスエンティティおよび属性に関する3つの要件

このセクションでは、Mendix アプリでサポートされている消費された OData サービスの機能について説明します。 これらの機能は、ドメインモデルで外部エンティティが使用される前にチェックされます。

### 3.1 エンティティ

サービスでは、サポートされていない機能を示すために語彙注釈を使用できます。 以下の語彙のアノテーションがエンティティセットに認識されます:

* **Countable** - `Countable="false"` に設定されたエンティティをマークすると、ユーザーがエンティティをアプリに追加できなくなります
* **フィルタ可能** - `Filterable="false"` は、すべてのプロパティをフィルタリング不可能として設定します。
* **ソート可能** - エンティティセットを `Sortable="false"` はすべてのプロパティをソート不可能として設定します
* Marking an entity set as `Filterable="false"` and `Sortable="false"` sets all properties as non-filterable and non-sortable; marking properties with the `NonFilterableProperties` annotation or the `NonSortableProperties` annotation sets specific attributes as non-filterable or non-sortable

エンティティはエンティティセットを介してアクセス可能な場合にのみ使用できます。

さらに、エンティティはキーで一意に識別できる場合にのみ使用できます。 キーは、次の条件が満たされている限り、1 つ以上のプロパティで構成できます。

* プロパティは nullable にできません ( `isNullable="false"` が指定されている必要があります)。
* Only the following types are allowed: `Byte`, `SByte`, `Int16`, `Int32`, `Int64`, `Boolean`, `Decimal`, `Single`, `Double`, and `String`.
* key プロパティの型が `String`の場合、長さが制限されていなければなりません。 これは、すべてのデータベースが文字列上で無制限の長さのインデックスをサポートしているわけではないからです。 コントラクトで `MaxLength` が指定されている場合に十分です。 ただし、 `MaxLength` が指定されていない場合、文字列の長さが制限されていることがわかります。 ドメインモデルで属性の最大長を指定することで、エンティティを使用できます。

{{% alert type="info" %}}
コントラクトで指定された最大長を持たないキーを持つエンティティを使用するこの機能は、バージョン 9.3.0 以降に適用されます。 Studio Pro の以前のバージョンでは、 `MaxLength` が指定されていることを確認するために、コントラクトを変更する必要があります。
{{% /alert %}}

### 3.2 属性

{{% alert type="warning" %}}
`FC_KeepInContent=false` としてマークされた属性は使用できません。
{{% /alert %}}

属性型はプリミティブでなければなりません (複合体、コレクション、列挙ではありません)。 アプリの属性の種類は、OData メタデータの属性の種類に基づきます。 次の表に示すようになります。

| OData Type                     | Mendix Type                           |
| ------------------------------ | ------------------------------------- |
| バイナリ                           | バイナリ (ただし、3.4を参照)                     |
| Boolean                        | Boolean <sup><small>[1]</small></sup> |
| Byte, SByte, Int16, Int32      | 整数                                    |
| DateTime, DateTimeOffset, Time | 日付/時刻                                 |
| 小数、ダブル、シングル                    | 小数点 <sup><small>[2]</small></sup>     |
| Int64                          | 長い順                                   |
| 文字列、Guid                       | 文字列                                   |
| (その他)                          | （非接触）                                 |

{{% alert type="warning" %}}
OData エンドポイントに操作が含まれている場合、これらは消費された OData サービスにインポートされません。 これらの操作を呼び出すには、 [REST サービスを呼び出す](call-rest-action) アクティビティを使用できます。
{{% /alert %}}

<sup><small>[1]</small></sup>: Mendix では、Boolean は null にできません。 サービスが null を返した場合、Mendix では false になります。

<sup><small>[2]</small></sup>: [Mendix decimal の範囲外の小数](attributes#type) は現在サポートされていません。 サービスが範囲外の値を返す場合、エラーが発生します。

### 3.3 一般化

消費された OData サービスは、一般化および専門化のインポートをサポートしていません。 つまり、元のアプリから公開された OData サービス契約は、専門化されたエンティティの属性とともに一般化の属性を含む離散エンティティとしての専門化を表示します。

つまり、Mendix OData エンドポイントを消費する場合、一般化とその特殊化の両方を消費する必要はありません。 専門化は、一般化のすべての属性と関連性を持つエンティティになります。

パブリッシュされた OData サービス内の他のエクスポーズされたエンティティとの一般化に関連付けられるものは、今や離散的な "特殊化された" エンティティに含まれます。

{{% alert type="warning" %}}
一般化と特殊化されたエンティティが同じサービスで公開される場合。 両方のエンティティが使用されている場合、一般化の関連付けのみが表示されます。 現在の離散的な専門化には、継承された関連があります。 これに対する回避策として、一般化せずに専門性を持つサービスを公開することがあります。 代わりに、汎用化の関連付けが公開されるべきではなく、専門化における継承された関連付けが保存されるようにします。
{{% /alert %}}

### 3.4 バイナリ属性

バイナリデータ形式は *メディア エンティティ* の形式でサポートされています。 メディア エンティティがドメイン モデルにドラッグされると、対応する外部エンティティが作成されます。 エンティティは `contents` 属性とバイナリデータを持ちます。

現在、バイナリデータはJavaアクションでのみアクセスできます。

### 3.5 関連付け

OData v3 アソシエーションは、2つのエンドがある場合にのみ使用できます。

OData v4 navigation プロパティは、パートナーを持つ場合のみ関連として使用できます。

## 4 Data Hub ライセンスの制限 {#license-limitations}

Mendix Data Hubは別途ライセンスされた製品です。

ライセンスがなければ、アプリケーションは各ランタイムインスタンスに対して1日あたり合計1000 個の OData オブジェクトを取得できます。 この制限を超えると、ユーザーがより多くのデータを取得しようとするとエラーが発生します。 1日あたりの消費されるオブジェクトの数は、Mendix Runtime スケジューラのタイムゾーンで真夜中にリセットされます (アプリで定義することができます [プロジェクト設定](project-settings#scheduled))。

データハブのライセンスでは、アプリは制限されません。

{{% alert type="info" %}}開発環境(およびStudiosから実行している場合)で実行されているアプリには、この制限はありません。 これは、データハブのライセンス制限なしにStudiosからアプリを実行できることを意味します。{{% /alert %}}

組織が持っているデータハブのライセンスの種類については、 [Mendix管理者](/developerportal/control-center/#company) またはデータハブ管理者にお問い合わせください。
