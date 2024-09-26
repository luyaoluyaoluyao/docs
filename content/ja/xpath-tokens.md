---
title: "XPath トークン"
parent: "xpath"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-tokens.pdf) をクリックしてください。
{{% /alert %}}

XPath クエリでは以下のトークンが使用されます:

| トークン  | 定義                                                                                                                                                                                                                                                               |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `//`  | XPath クエリは常にトークン `//` から始まります。 これらのスラッシュの後に、照会されている [オブジェクト](entities) の名称が続きます。 たとえば、すべての顧客を取得したい場合、クエリは以下のようになります: `//Customers`。                                                                                                                              |
| `.`   | このドットは [モジュール](modules) 名と [エンティティ](entities) 名を区別するために使用されます。 例えば、salesモジュール内のすべての顧客 (objects) を取得したい場合は、 `//Sales.Customer` でクエリを開始します。                                                                                                                        |
| `/`   | スラッシュは、新しいエンティティや関連付けを参照したいときに使用されます。 例えば、 `//Sales.Customer/Sales.Customer_Order/Sales.Order`. このクエリは、 [エンティティ](entities) `顧客` からエンティティ `注文` [アソシエーション](associations) `Customer_Order` のパスに従います。 ドメインモデルで利用可能な潜在的な関連がある限り、クエリはスラッシュやエンティティや関連付けによって拡張することができます。 |
| `[ ]` | 制約は常に括弧の間に書き込まれます。 例えば、 `//Sales.Customer[TotalAmount > 1000]`. [属性](attributes) が制約されているのは `TotalAmount`で、制約は `> 1000` です。 したがって、€1000以上を費やしている顧客のみが取得されます。                                                                                               |
| `( )` | 制約は括弧でグループ化できます。 詳細に関しては、 [XPath 制約](xpath-constraints) を参照してください。                                                                                                                                                                                               |

システム変数とは、XPath 条件式で値を使用できるトークンです。 これらのトークンの詳細については、 [XPath キーワード & システム変数](/refguide8/xpath-keywords-and-system-variables) を参照してください。
