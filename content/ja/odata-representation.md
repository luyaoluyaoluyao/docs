---
title: "OData の表現"
parent: "published-odata-services"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/odata-representation.pdf) をクリックしてください。
{{% /alert %}}

このドキュメントでは、エンティティが公開された OData サービスでどのように表現されるかについて説明します。

## 1つの属性

| Mendix Data Type                | Edmタイプ             | 属性値                                  | Atom XML 表現                          |
| ------------------------------- | ------------------ | ------------------------------------ | ------------------------------------ |
| Id <sup>1</sup> <sup>2</sup>    | Edm.Int64          | 3940649673954387                     | 3940649673954387                     |
| Autonumber                      | Edm.Int64          | 1                                    | 1                                    |
| バイナリ (サポートされていません) <sup>3</sup> |                    |                                      |                                      |
| Boolean                         | Edm.Boolean        | true                                 | true                                 |
| 日付と時刻                           | Edm.DateTimeOffset | 金曜日、2014年12月19日 10:27:27 GMT         | 2014-12-19T10:27:27.000Z             |
| 列挙型                             | Edm.String         | カラー.ブルー                              | 青                                    |
| 小数点以下の大きさ                       | Edm.Decimal        | 0.3333333333333333333333333333333333 | 0.3333333333333333333333333333333333 |
| ハッシュ文字列                         | Edm.String         | HashPassword                         | HashPassword                         |
| 整数                              | Edm.Int64          | 50                                   | 50                                   |
| Long <sup>2</sup>               | Edm.Int64          | 3940649673954387                     | 3940649673954387                     |
| String <sup>4</sup>             | Edm.String         | ジョン                                  | ジョン                                  |

<sup>1</sup>In the service's metadata, IDs are marked with `isAttribute="false"` (using a Mendix-specific XML attribute in the `http://www.mendix.com/Protocols/MendixData` namespace) in order to indicate that these are not attributes that appear in the domain model. Note: the `isAttribute="false"` feature was introduced in Studio Pro [8.6.0](/releasenotes/studio-pro/8.6#860).<br /> <sup>2</sup>When using Excel to import an OData source, long numbers may seem cut off. これは、Microsoftが使用するデータタイプの制限によるものです。 For more information, see [Last digits are changed to zeroes when you type long numbers in cells of Excel](https://support.microsoft.com/en-us/kb/269370).<br /> <sup>3</sup>Even though the binary data type is not supported, the FileDocument and Image system entities are supported and represented as Base64-encoded strings with the `Edm.Binary` type.<br /> <sup>4</sup>When the string attribute has a limited length, the `MaxLength` attribute is specified. 注意: この機能は Studio Pro [8.16.0](/releasenotes/studio-pro/8.16#8160) で導入されました。

さらに、OData のエントリの `updated` 項目は、エンティティの system changedDate 属性に由来します。 この属性が使用できない場合 (公開されていないため、ユーザーはアクセス権を持っていません) またはデータベースでは空白の場合、デフォルトの日付(1-1-1970)が使用されます。

## 2つの関連 {#associations}

OData サービスの設定で、関連付けがどのように表示されるかを選択できます。 以下に2つの選択肢があります。

### 2.1 リンクとして

関連付けをリンクとして表すことを選択すると、各オブジェクトは各関連付けのリンクを含みます。 関連するオブジェクトはこれらのリンクを介して取得できます。

これは、反対側のエンティティがこのサービスのリソースである場合にのみ関連付けを公開できることを意味します。 これはまた、同じサービス内で同じエンティティを複数回発行することができないことを意味します(その場合のため)。 リンクがどこに向けるべきかは明らかではありません)。

このメソッドを使用すると、関連付けの両側を公開し、多対多の関連付けを公開することができます。

### 2.2 関連オブジェクトIDとして

assocations を関連付けられたオブジェクト ID として表すように選択した場合、関連付けられたオブジェクトの ID は `Edm.Int64` プロパティとして表されます。 関連付けが複数のオブジェクトを参照している場合、その側から関連付けを公開することはできません。
