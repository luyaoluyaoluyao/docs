---
title: "OQL キャスト"
parent: "oql-functions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-cast.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

CAST 関数は、式を特定のデータ型に変換します。

構文は以下の通りです:

```
CAST ( expression AS data_type )
```

* `式` - 変換する式を指定します
* `data_type` – 式を変換するデータ型を指定します。データ型は次のいずれかになります:
  * BOOLEAN
  * 日時
  * DECIMAL
  * インテガー
  * 長さ:
  * 文字列

## 2対応の変換

以下の表は、サポートされている CAST 変換を示しています。

* ✔ – 変換はサポートされています
* ✔* – 変換はサポートされていますが、データベースごとに動作が異なります (下記の発言を参照してください)
* 【 変換はサポートされていません 】

| From \ To | BOOLEAN | 日時 | DECIMAL | インテガー | 長さ: | 文字列（無制限） |            文字列（制限）            |
| ---------- |:-------:|:--:|:-------:|:-----:|:---:|:--------:|:-----------------------------:|
| BOOLEAN    |    ✔    | ✘  |    ✘    |   ✘   |  ✘  |    ✔*    | ✔*<sup><small>1</small></sup> |
| 日時         |    ✘    | ✔  |    ✘    |   ✘   |  ✘  |    ✔*    | ✔*<sup><small>2</small></sup> |
| DECIMAL    |    ✘    | ✘  |   ✔*    |  ✔*   | ✔*  |    ✔*    | ✔*<sup><small>2</small></sup> |
| インテガー      |    ✘    | ✘  |    ✔    |   ✔   |  ✔  |    ✔     |               ✔               |
| 長さ:        |    ✘    | ✘  |    ✔    |   ✔   |  ✔  |    ✔     |               ✔               |
| 文字列        |    ✘    | ✘  |    ✔    |   ✔   |  ✔  |    ✔     |               ✔               |
* [1] – 文字列へのBOOLEAN(制限)は、文字列の長さが5以上である場合にのみサポートされます。
* [2] – 値が文字列の長さに完全に適合する場合にのみ、DATETIMEおよびDECIMALの文字列への変換(制限)がサポートされます。 文字列の長さが 20 未満の場合、変換は失敗する可能性があります。
