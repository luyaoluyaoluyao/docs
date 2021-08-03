---
title: "OQL Aggregation"
parent: "oql-expression"
---


集計は、取得された列の値に対して特定の計算を実行します。 集約関数は次のとおりです。

| AVG  | 平均   |
| ---- | ---- |
| カウント | カウント |
| MAX  | 最大   |
| MIN  | 最小   |
| SUM  | sum  |

SELECT 句内で集約式を使用する場合。 SELECT 句内のすべての式は、クエリーの GROUP BY 句内の集約または部分でなければなりません。
