---
title: "関連"
parent: "エンティティ"
menu_order: 30
tags:
  - "ドメインモデル"
  - "関連"
---

## 1つの紹介

**関連** タブは、エンティティプロパティのタブであり、以下の設定があります。

* [名前](#name)
* [タイプ](#type)
* [所有者](#owner)
* [親/子要素](#parent-child)

![](attachments/associations/dm-entity-properties-associations-tab.png)

関連付けの詳細については、 [関連付けとプロパティ](association-properties) を参照してください。

## 2名 {#name}

関連付けの名前はフォーム、マイクロフロー、XPath 制約などから参照するために使用されます。

## 3種類 {#type}

このプロパティは、関連付けが参照(単一)であるか、参照セット (複数)であるかを定義します。

| 値         | 説明                                                        |
| --------- | --------------------------------------------------------- |
| 参照        | 単一: 所有しているエンティティのオブジェクトは、ゼロまたは他のエンティティの 1 つのオブジェクトを参照します。 |
| リファレンスセット | 複数: 所有しているエンティティのオブジェクトは、他のエンティティの 0 個以上のオブジェクトを参照します。    |

* *デフォルト値*: 参照

{{% alert type="info" %}}

このプロパティの例は、以下の owner プロパティの例と組み合わせています。

{{% /alert %}}

## 4 所有者 {#owner}

このプロパティは、関連付けに1つまたは2つの所有者があるかどうかを定義します。 1つの所有者がいる場合、所有者は矢印の先頭に位置します。

| 値     | 説明                   |
| ----- | -------------------- |
| デフォルト | 唯一のエンティティは、所有者(親)です。 |
| 両方とも  | 両方のエンティティは所有者です。     |

* *デフォルト値*: デフォルト

## 5種類の種類と所有者の多重性とナビゲーション性との関係

**Type** and **Owner** properties of an entity are related to **[Multiplicity](association-properties#multiplicity)** and **[Navigability](association-properties#navigability)** properties of an association. **Type** または **Owner**を変更すると、 **Multiplicity** と **Navigability** も変更されます。

以下の表の **タイプ**/**オーナー** と **マルチプリシティー**/**ナビゲビリティ** の間で対応しています。

|                                                              | タイプ       | 所有者   |
| ------------------------------------------------------------ | --------- | ----- |
| **多重性**: 1対1 <br />**ナビゲーション性**: 利用不可                  | 参照        | 両方とも  |
| **多重度**: 1対多 <br />**ナビゲーション**: 利用不可                   | 参照        | デフォルト |
| **多重度**: 多対多 <br />**ナビゲーション性**: XオブジェクトはYオブジェクトを参照する  | リファレンスセット | デフォルト |
| **多重度**: 多対多 <br />**ナビゲーション性**: X と Y オブジェクトは互いを参照します | リファレンスセット | 両方とも  |

For more information on multiplicity and navigability, see section [2.3 Multiplicity](association-properties#multiplicity) and section [2.4 Navigability](association-properties#navigability) in *Associations and Their Properties*.

## 6 親/子要素 {#parent-child}

親と子の設定には、関連付けの方向が表示されます。 親は、関連付けが開始されるエンティティを定義し、子は関連付けが終了するエンティティを定義します。

## 7つの関連例

**Order** エンティティから **Customer** エンティティへの関連付けを描画すると、以下の結果になります:

![](attachments/domain-model-editor/918217.png)

type プロパティにはデフォルト値の `Reference` があります。 この例では、顧客は複数の注文を持つことができ、注文は1つの顧客しか持つことができません。

XML では、これらのエンティティとその関連付けのインスタンスは以下のようになります (関連付けは **Order** 要素にのみ保存されていることに注意してください)。

```xml
<Order id="101">
    <number>1</number>
    <date>9/30/2008</date>
    <Order_Customer>id_201</Order_Customer>
</Order>

<Customer id="201">
    <fullname>Apple Inc.</fullname>
    <address>1 Infinite Loop</address>
    <telephonenumber>1-800-MY-APPLE</telephonenumber>
</Customer>

```

デフォルトの所有権を持つ多対多の関連付けは、関連を描画し、 `Type` プロパティを `Reference set` に設定することによって作成されます。

In this example, a **Customer** can have multiple **Groups**, and a **Group** can have multiple **Customers**:

![](attachments/domain-model-editor/918127.png)

XML では、これらのエンティティとその関連付けのインスタンスは以下のようになります (関連付けは **顧客** 要素にのみ保存されます)。

```xml
<Customer id="201">
    <fullname>Apple Inc.</name>
    <address>1 Infinite Loop</address>
    <telephonenumber>1-800-MY-APPLE</telephonenumber>
    <Customer_Group>id_301 id_302</Customer_Group>
</Customer>

<Group id="301">
    <name>Multinational corporations</name>
</Group>

<Group id="302">
    <name>Hardware suppliers</name>
</Group>

```

owner プロパティを `both` に設定することで、1 対 1 の関連付けが作成されます (typeプロパティはデフォルト値の `Reference` のままにします)。

In this example, a **Customer** can have one **Profile**, and a **Profile** can have one **Customer**:

![](attachments/domain-model-editor/918128.png)

XML で これらのエンティティとその関連のインスタンスは以下のようになります (関連付けは **プロファイル** 要素と **顧客** 要素の両方に格納されていることに注意してください)。

```xml
<Profile id="401">
    <religion>Buddhism</religion>
    <job>Chief Executive Officer</job>
    <website>http://www.apple.com/ </website>
    <Customer_Profile>id_201</Customer_Profile>
</Profile>

<Customer id="201">
    <fullname>Steve Jobs</fullname>
    <address>1 Infinite Loop</address>
    <telephonenumber>1-800-MY-APPLE</telephonenumber>
    <Customer_Profile>id_401</Customer_Profile>
</Customer>

```

オーナープロパティを `` に設定し、type プロパティを `参照集合` に設定することで、両方のエンティティがオーナーである多対多の関連付けを作成します。

この例では、 **Accountant** は複数の **グループ** を持ち、 **グループ** は複数の **Accountants を持つことができます。**

{{% image_container width="500" %}}![](attachments/domain-model-editor/918125.png)
{{% /image_container %}}

XML で これらのエンティティとその関連付けのインスタンスは以下のようになります (関連付けは **Accountant** 要素と **Group** 要素の両方に格納されていることに注意してください)。

```xml
<Accountant id="501">
    <idnumber>1</idnumber>
    <name>Earl Grey</name>
    <telephonenumber>1-800-EARL-GREY</telephonenumber>
    <Accountant_Group>id_301 id_302</Accountant_Group>
</Accountant>

<Accountant id="502">
    <idnumber>2</idnumber>
    <name>Scrooge McDuck</name>
    <telephonenumber>1-800-SCROOGE-MCDUCK</telephonenumber>
    <Accountant_Group>id_301 id_302</Accountant_Group>
</Accountant>

<Group id="301">
    <name>Multinational corporations</name>
    <Accountant_Group>id_501 id_502</Accountant_Group>
</Group>

<Group id="302">
    <name>Hardware suppliers</name>
    <Accountant_Group>id_501 id_502</Accountant_Group>
</Group>

```

## 8 続きを読む

* [関連付けとプロパティ](association-properties)
* [エンティティ](エンティティ)