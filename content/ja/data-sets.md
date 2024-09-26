---
title: "Datasets"
parent: "リソース"
menu_order: 50
tags:
  - "studio pro"
  - "データセット"
  - "dataset"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/data-sets.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

データセットは、 [ページ](report-widgets) の [レポート ウィジェット](pages) に表示されるデータを定義するために使用できます。

データセットは、 [OQL クエリ](oql) またはカスタム [Java アクション](java-actions) を使用して定義されます。 データセットを制限するには、OQL クエリまたは Java アクションで使用できるパラメータを定義できます。

データセットの項目は以下に記載されています。

## 2つの全般

* **Name** – データセットの名前。
* **説明** – データセットの説明、これはドキュメントとしてのみ関係がある。

## 3 ソース

* **OQL クエリ** - データセットを定義する [OQL クエリ](oql)。
*  **Javaアクション** – データセットを返すJavaアクションのインタフェース。 列の列と [データ型](data-types) をStudio Proで指定する必要があります。 この仕様に基づいて、Studio Proはこのアクションのテンプレートを作成します。

以下は、特定の顧客グループの顧客のすべての注文の集計総注文額を計算するOQL クエリの例です。

```sql
FROM CRM.Customers As CustomerObj
INNER JOIN CustomerObj/CRM.Orders_Customer/CRM.Orders As OrderObj
WHERE CustomerObj/CRM.Customer_Group = $ParGroup
GROUP BY CustomerObj/Name
SELECT CustomerObj/Name As Name, SUM(OrderObj/TotalAmount) As TotalAmount
```

## 4つのパラメータ

データセットは複数のパラメータを持つことができます。 パラメータはデータセットのフィルタリングや操作に使用されます。 データセットのセキュリティは、パラメータに基づいて設定されます。 Javaアクションでは、生成されたテンプレートでパラメータが使用されます。

{{% alert type="info" %}}

OQL では、パラメータは **$** 記号を使用して呼び出すことができます。例: **$Month**。

{{% /alert %}}

パラメータには以下の設定可能なプロパティがあります。

* **Name** – パラメータの名前
* **Type** – パラメータのタイプ: Object、列挙、プリミティブ(日付と時刻、整数、ブール値など)。 使用可能なパラメータ型については、 [Data Types](data-types) を参照してください。
* **制約** – パラメータの制約。 これらの制約は、エンドユーザーがパラメータ入力値に対して選択できる値に影響します。 制約は、データセットセキュリティのユーザーロールに関連付けることができます。 拘束には、数値と日付のパラメーターに適用される範囲と、オブジェクトパラメーターに適用される XPath 条件式があります。
* **Ranges** – パラメータが範囲として定義されている場合、レポートのドロップダウンボックスは範囲内のすべての値の代わりに各範囲を表示します。 小数パラメータは常に範囲です。
* **XPath 制約** – XPath 制約は [XPath](xpath) を使用して定義することができます。 複数の制約をパラメータに定義することができ、それぞれの制約は [ユーザー ロール](user-roles) に関連付けることができます。
