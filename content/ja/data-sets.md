---
title: "Datasets"
parent: "リソース"
menu_order: 50
tags:
  - "studio pro"
  - "データセット"
  - "dataset"
---

## 1つの紹介

データセットは、 [ページ](report-widgets) の [レポート ウィジェット](pages) に表示されるデータを定義するために使用できます。

データセットは、 [OQL クエリ](oql) またはカスタム [Java アクション](java-actions) を使用して定義されます。 データセットを制限するには、OQL クエリまたは Java アクションで使用できるパラメータを定義できます。

## 2つの全般

データセットのフィールドには、次のプロパティがあります。

* **Name** – これはデータセットの名前です。
* **説明** – これはデータセットの説明であり、ドキュメントとしてのみ関連します。

## 3 ソース

* **OQL クエリ** - これは、データセットを定義する [OQL クエリ](oql) です。
* **Javaアクション** – データセットを返すJavaアクションのインタフェースです。 列の列と [データ型](data-types) をStudio Proで指定する必要があります。 この仕様に基づいて、Studio Proはこのアクションのテンプレートを作成します。

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

* **名前** – パラメータの名前です。
* **Type** – The type of the parameter can be: **Boolean**, **Date and time**, **Enumeration**, **Decimal**, **Integer/Long**, or **String**.
* **制約事項** – エンドユーザーがパラメータ入力値に対して値を選択できるパラメータ影響に対する制約。 制約は、データセットセキュリティで [ユーザー ロール](user-roles) に関連付けることができます。 制約には2つの種類があります:
  * 数値パラメータと日付パラメータに適用される範囲
  * オブジェクトパラメータに適用される XPath 制約
* **Ranges** – パラメータが範囲として定義されている場合 レポートのドロップダウン ボックスには、範囲内のすべての値ではなく、各範囲が表示されます。 小数パラメータは常に範囲です。
* **XPath 制約** – XPath 制約は [XPath](xpath) を使用して定義することができます。 複数の制約をパラメータに定義することができ、各制約をユーザのロールに関連付けることができます。
