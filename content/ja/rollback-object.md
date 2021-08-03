---
title: "オブジェクトをロールバックする"
parent: "object-activity"
---

## 1つの紹介

format@@0 アクションを使用すると、アクティビティの前にあるフローの部分でオブジェクトに加えられた (コミットされていない) 変更を取り消すことができます。 さらに、作成されたがコミットされていないオブジェクトを削除します。

{{% alert type="info" %}}

Rollback オブジェクトアクションがサブマイクロフローで実行されると、サブマイクロフローとその親マイクロフローの両方の変更がロールバックされます。

{{% /alert %}}

{{% alert type="info" %}}

すべてのマイクロフローアクティビティが共有するプロパティ(図表など)については、 [Microflow Element Common Properties](microflow-element-common-properties) を参照してください。 このページでは、アクションに固有のプロパティのみを記述します。

{{% /alert %}}

クライアントからマイクロフローが呼び出された場合、ロールバックされたオブジェクトの属性を示す [入力ウィジェット](input-widgets) は自動的に更新されます。 これには、可視性と編集性 [条件](conditions) の更新が含まれます。

## 2つの入力プロパティ

### 2.1 オブジェクト

オブジェクトはロールバックする必要があるオブジェクトを定義します。

### 2.2 クライアントで更新

マイクロフローがクライアントから呼び出された場合 **クライアントで更新** が *いいえ*に設定されている場合、ロールバックはクライアントに反映されません。 If Refresh in client is set to *Yes*, the object is refreshed across the client, which includes reloading of relevant [data sources](data-sources).

{{% alert type="info" %}}

7.19.0では、ロールバック属性値は常にクライアントに反映されます。 [データ ソース](data-sources) は **クライアントで更新** が *はい* に設定されている場合にのみ再読み込みされます。

{{% /alert %}}

{{% alert type="warning" %}}

When inside a [nanoflow](nanoflows), the Rollback object action reloads [data sources](data-sources) as if **Refresh in client** was set to *Yes*.

{{% /alert %}}

_デフォルト値_: いいえ
