---
title: "REST 操作としてマイクロフローを公開"
parent: "published-rest-services"
menu_order: 30
description: "REST 操作としてマイクロフローを公開する方法"
tags:
  - "マイクロフロー"
  - "REST"
  - "操作"
  - "リソース"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/publish-microflow-as-rest-operation.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

RESTサービス操作としてマイクロフローを発行するには、マイクロフローエディタを右クリックし、 **Publish as REST service operation** を選択します。

microflow がオブジェクトまたはリスト型の 1 つ以上のパラメータを取る場合、REST 操作として公開することはできません。 公開しようとすると、一貫性エラーが発生します。

## 2 リソースの選択

**Publish as REST service operation**をクリックした後、マイクロフローを公開するリソースを選択する必要があります。 いくつかのオプションがあります:

* すでにマイクロフローを公開するサービスとリソースがある場合は、それを選択して **Select**
* すでにサービスを持っていてリソースを作成したい場合は、サービスを選択して **New** をクリックしてください。
* 新しいサービスを作成する場合は、モジュールまたはフォルダを選択し、 **New** をクリックします。

リソースの提案された名前は、マイクロフローのパラメータの実体またはマイクロフローの実体結果です。

## 3 操作の編集

サービスとリソースを選択または作成したら、操作を編集できます。

**メソッド** の推奨値は、microflow が object パラメータまたは list パラメータを取るときに **POST** です。 そうでなければ、それは **GET** です。
