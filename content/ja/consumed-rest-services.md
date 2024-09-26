---
title: "利用可能なRESTサービス"
parent: "統合"
description: "Mendixで消費されたRESTサービスとJSONの概要を提示します。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-rest-services.pdf) をクリックしてください。
{{% /alert %}}

## 1 REST

Representational state transfer (REST) は、リソースを消費または公開するアプローチです。 エンドポイント間でデータを転送するために広範なスキーマや契約が必要ないため、そのシンプルさのために人気を博しています。 以下を使用します。

* リソースを見つけるための HTTP URL
* (XML や JSON などの) コンテンツ型を認証および指定する HTTP ヘッダー
* GET (データの取得) や POST (データの送信) などのリソースの操作を識別する HTTP メソッド

契約とスキーマの不足により、RESTの使用が容易になります。 しかし、多くのRESTエンドポイントは複雑なデータを返します。

The [JSON Structure](json-structures) document helps with giving structure to JSON data: from an example JSON snippet, a lightweight schema is extracted that is used in [Mapping Documents](mapping-documents). The [Import Mapping](import-mappings) document converts JSON (or XML) to Mendix objects, and the [Export Mapping](export-mappings) document serializes Mendix objects to JSON (or XML).

## 2 JSON

JavaScriptオブジェクト表記(JSON)は、データの軽量表現です。

```js
{
    "name": "John Smith",
    "age": 23,
    "address": 
    {
        "street": "Dopeylane 14",
        "city": "Worchestire"
    }
}
```

Above, the object `person` is described with the corresponding values for the attributes `name`, `age`, and the referred object `address`.

## 3つの例

**Mendix Studio Pro 8 で REST を消費する方法**

{{% youtube OhzWTa1kZ00 %}}
