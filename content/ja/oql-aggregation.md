---
title: "OQL Aggregation"
parent: "oql-expression"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-aggregation.pdf) をクリックしてください。
{{% /alert %}}

集計は、取得された列の値に対して特定の計算を実行します。 集約関数は次のとおりです。

| AVG  | 平均   |
| ---- | ---- |
| カウント | カウント |
| MAX  | 最大   |
| MIN  | 最小   |
| SUM  | sum  |

SELECT 句内で集約式を使用する場合。 SELECT 句内のすべての式は、クエリーの GROUP BY 句内の集約または部分でなければなりません。
