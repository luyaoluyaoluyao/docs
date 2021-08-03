---
title: "OQL Aggregation"
parent: "oql-expression"
tags:
  - "studio pro"
---


集計は、取得された列の値に対して特定の計算を実行します。 集約関数は次のとおりです。

| 式    | 説明   |
| ---- | ---- |
| AVG  | 平均   |
| カウント | カウント |
| MAX  | 最大値  |
| MIN  | 最小   |
| SUM  | Sum  |

When you are using an aggregate expression in the `SELECT` clause, all expressions in the `SELECT` clause have to be either an aggregation *or* part of the `GROUP BY` clause of the query.
