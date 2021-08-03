---
title: "パラメータ"
parent: "application-logic"
menu_order: 70
tags:
  - "studio pro"
  - "パラメータ"
  - "マイクロフロー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/parameter.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

パラメータは、マイクロフローの入力を使用する特別な種類の変数です。 マイクロフローがトリガーされると、パラメータは現在の値で埋められます。

マイクロフローで *顧客* エンティティのオブジェクトを使用する場合は、パラメータを使用します。 下の画像では、オブジェクト名は *EnclosingCustomer* で、黒色で表示されています。 データ型はオブジェクトであるため、エンティティ名はオブジェクト名の下に青色で表示されます。

![](attachments/parameter/parameter.png)

## 2つの出力プロパティ

### 2.1 名前

**名前** はパラメータの値を指します。

### 2.2 データ タイプ

パラメータのデータ型は、期待される値の型を定義します。 利用可能なデータ型については、 [Data Types](data-types) を参照してください。

デフォルト: *オブジェクト*
