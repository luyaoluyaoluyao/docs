---
title: "XPath クエリ関数"
parent: "xpath"
tags:
  - "studio pro"
---

以下の XPath クエリ集約関数を使用できます。

* [avg](xpath-avg)
* [カウント](xpath-count)
* [最大](xpath-max)
* [分](xpath-min)
* [sum](xpath-sum)

これらの関数は引数として完全なクエリを含める必要があります。 However, the `avg`, `max`, `min`, and `sum` functions must specify a column in the query to aggregate.

{{% alert type="warning" %}}
これらの関数はJavaコードでのみ使用することができます。
{{% /alert %}}
