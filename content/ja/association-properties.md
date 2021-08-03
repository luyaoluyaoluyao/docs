---
title: "関連のプロパティ"
parent: "関連"
menu_order: 10
tags:
  - "ドメインモデル"
  - "関連"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/association-properties.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

[アソシエーション](associations) のプロパティを編集するには2つの方法があります。 このページでは、ドメインモデルの関連付けのプロパティ ペインで編集できるプロパティについて説明します。 または、関連プロパティの format@@0 タブから直接関連プロパティダイアログを開きます。

また、エンティティプロパティの format@@0 タブで直接関連を編集することもできます。 詳細については、 [関連タブプロパティ](association-member-properties) を参照してください。

{{% alert type="info" %}}
関連付けられた外部エンティティの属性プロパティは、元のアプリで定義され、これらのエンティティに適用できる唯一のローカル変更は、ローカルの名前と説明です。 詳細については、 [外部エンティティ](external-entities#attributes) の *属性* セクションを参照してください。
{{% /alert %}}

## 2つの関連プロパティ

関連付けプロパティの例を以下の画像に示します。

![関連のプロパティ](attachments/associations/association-properties.png)

関連付けには以下のプロパティがあります。

* [名前](#name)
* [ドキュメント](#documentation)
* [多重度](#multiplicity)
* [ナビゲーション](#navigability)
* [動作を削除](#delete-behavior)

### 2.1 名前 {#name}

関連付けを参照するために使用される名前 例えば、フォームやマイクロフローで。

### 2.2 ドキュメント {#documentation}

メモとドキュメントは、 **ドキュメント** プロパティで書くことができます。

### 2.3 多重性 {#multiplicity}

多重度には以下のタイプがあります:

| 多重度            | 意味                                      | 次のとおり：                                                      |
| -------------- | --------------------------------------- | ----------------------------------------------------------- |
| 1 対 1          | 1 つの X オブジェクトが 1 つの Y オブジェクトに関連付けられています | 所有者が **両方** に設定されたタイプ **参照**の関連付け。                          |
| 1対多の *(デフォルト)* | 1 つの X オブジェクトが複数の Y オブジェクトに関連付けられています   | 所有者が **デフォルト** に設定された **参照タイプの関連付け**                        |
| 多対多で           | 複数の X オブジェクトが複数の Y オブジェクトに関連付けられています    | **参照セット** の関連付け。この場合、所有権は **Navigability** プロパティによって設定されます。 |

For more information about association types, see the [Type](association-member-properties#type) section in *Association Tab Properties*, and for information on ownership, see the [Owner](association-member-properties#owner) section in *Association Tab Properties*.

### 2.4 Navigability {#navigability}

| ナビゲーション                             | 意味              | 次のとおり：                                   |
| ----------------------------------- | --------------- | ---------------------------------------- |
| X オブジェクトは Y オブジェクト *(デフォルト)* を参照します | 協会の所有者はXです      | 所有者が **デフォルト** に設定された **参照セット**タイプの関連付け。 |
| XオブジェクトとYオブジェクトは互いを参照します            | 両方のエンティティは所有者です | 所有者が **両方** に設定された **参照セット**型の関連付け。      |

**Reference sets** の **Owner** プロパティに対応します。 ナビゲーションの変更による影響の詳細については、 [](association-member-properties#owner) *関連タブ* の</em> のformat@@4 オーナーセクションを参照してください。

名前にもかかわらず、ナビゲーションは通常、関連付けを追加または変更する場合にのみ重要です。 関連付けの 1 つのオブジェクトの所有者を作成することで、その関連付けを非 owner 端から読み取ることができません。

### 2.5 動作の削除 {#delete-behavior}

| 値                                                                                                    | 説明                                     |
| ---------------------------------------------------------------------------------------------------- | -------------------------------------- |
| {name of entity} オブジェクトを削除しますが、 {name of other entity} オブジェクトを保持します *(デフォルト)*                        | オブジェクトが削除されると、関連するオブジェクトは削除されません。      |
| {name of entity} オブジェクトと {name of other entity} オブジェクトを削除<sup><small>[1]</small></sup>               | オブジェクトが削除されると、関連するオブジェクトも削除されます。       |
| {name of entity} オブジェクトを {name of other entity}<sup><small>[2]</small></sup> オブジェクトに関連付けられていない場合のみ削除 | オブジェクトは他のオブジェクトと関連付けられていない場合にのみ削除できます。 |

<sup><small>[1]</small></sup>この削除動作は、関連する **プロファイル** **顧客** が削除されたときに使用されます:

![](attachments/associations/association-delete-both.png)

<sup><small>[2]</small></sup>この削除動作は、 **顧客** が **注文** に関連付けられていない場合にのみ使用されます。 この場合、「顧客」オブジェクトを削除できない場合は **エラーメッセージを入力するよう求められます。** エンドユーザーに、この顧客は削除できず、次のアクションを提案することができます：

![](attachments/associations/association-prevent-delete.png)

## 3 続きを読む

* [関連](関連)
