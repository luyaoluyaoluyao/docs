---
title: "XPath クエリ関数"
parent: "xpath"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-query-functions.pdf) をクリックしてください。
{{% /alert %}}

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
