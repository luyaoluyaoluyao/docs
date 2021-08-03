---
title: "関連"
parent: "ドメインモデル"
menu_order: 20
tags:
  - "ドメインモデル"
  - "関連"
  - "studio pro"
---

## 1つの紹介 {#intro}

関連付けはエンティティ間の関係を記述します。 ドメイン モデルでは、関連付けは、2 つのエンティティ間の線または矢印で表されます。

{{% alert type="info" %}}
同じデータソースから2つの外部エンティティ間の関連付けは、元のアプリで定義されるため、モデルでエンティティが使用されると自動的に確立されます。 詳細については、 [外部エンティティ](external-entities#properties) の *Associations* セクションを参照してください。
{{% /alert %}}

### 1.1 所有者 {#ownership}

関連付けの値は、アソシエーションの [所有者](association-member-properties#owner) であるエンティティのオブジェクトから参照し、編集する必要があります。 関連付け内の所有権は矢印によって表されます (矢印は方向を示しません)。 どちらか一方または両方のエンティティが関連付けの所有者になることができます。 あるエンティティが所有者である場合、所有者から他のエンティティを指す矢印があります。 両方のエンティティが所有者である場合、2つのエンティティの間に線がありますが、矢印はありません。 これは、矢印を制御することができる唯一の方法です。

所有権がなぜ存在するのかを理解することが重要です。 オーナーシップは Mendix に実装されているので、最初のデザインにこだわるのではなく、リレーションシップを動的に変更することができます。 例えば、 [1対多のアソシエーション](#one-to-many) としてデザインし、デフォルトのオーナーシップを持つ [多対多のアソシエーション](#many-to-many)にする必要がある場合 Mendixがそれを処理するので、データベースを再構築する必要はありません。

### 1.2 多重性

関連付けの [多重度](association-properties#multiplicity) (または参照オブジェクトの数) は、関連付けの両側の数 1 (`1`) または星 (`*`) で示されます。

In the example below, the arrow indicates that **Order** is the owner of the association, and the `1` and `*` indicate that one customer is associated with many orders:

![](attachments/associations/association-order-customer.png)

{{% alert type="info" %}}
持続可能エンティティと非持続可能エンティティの関連付けは、非持続可能エンティティで開始し、所有者が **デフォルト**でなければなりません。 持続可能で持続不可能なエンティティについての詳細は、 [持続可能性](persistability) を参照してください。
{{% /alert %}}

## 2 関連付けの作成 {#creating}

関連付けを作成する最も簡単な方法は、 [ドメインモデル](domain-model)内の2つのエンティティ間の関連付けを描画することです。 デフォルトでは、関連付けの所有者/多数の側から始まり、関連付けの片側で終わる1対多の関連付けが作成されます。 関連付けは、アンダースコアを持つ2つのエンティティの名前を結合することによって名前が付けられます。 次のセクションで説明したように、関連付けを編集できます。

アプリの異なるモジュール内のエンティティ間の関連付けを作成することもできます。 この場合、協会を描画することはできません。 関連付けを所有するエンティティの **関連付け** タブで新しい関連付けを作成することで、別のモジュールのドメインモデル内のエンティティへの関連付けを作成できます。 アプリ内のエンティティを関連付けのターゲットとして選択することができます。 詳細については、 [関連タブプロパティ](association-member-properties) を参照してください。

{{% alert type="info" %}}
外部エンティティとローカルエンティティ間のみの関連付けを作成および編集できます。 ただし、外部エンティティをローカルエンティティとの関連付けの [所有者](association-member-properties#owner) にすることはできません。
{{% /alert %}}

{{% alert type="info" %}}
2つの外部エンティティを接続する必要がある場合は、ローカルエンティティを追加し、このローカルエンティティを両方の外部エンティティに接続することを検討してください。 この場合、ローカルエンティティは両方のアソシエーションの所有者でなければなりません。
{{% /alert %}}

## 3つの関連付けの編集

関連付けを編集するには2つの方法があります。

### 3.1 関連付けを直接編集

関連付け自体を編集できます。 この場合、多重度とナビゲーションを使用して関連付けを定義します。

![](attachments/associations/edit-association.png)

詳細については、 [関連プロパティ](association-properties) を参照してください。

### 3.2 エンティティの関連付けから編集

エンティティのメンバーとしてその関連付けを編集できます。 この場合、typeとownerを使用して関連付けを定義します。

![](attachments/associations/edit-entity-association.png)

詳細については、 [関連タブプロパティ](association-member-properties) を参照してください。

### 3.3 関連付けの矢印を移動

関連付け矢印は削除せずに2つのエンティティ間で移動できます。 関連付け矢印の両側にある黒い点内をクリックし、新しい目的の場所にドラッグします。

{{% alert type="warning" %}}
マウスポインタは白い点を動かすべきではありません。 これは、新しい関連付けの作成を示しています。
{{% /alert %}}

![](attachments/associations/association-move-arrow.png)

## 4つの関連例 {#examples}

### 4.1 1対多の協会 {#one-to-many}

この例では、 **Order** エンティティから **Customer** エンティティへの関連付けを描画すると、次の結果になります:

![](attachments/associations/association-order-customer.png)

type プロパティにはデフォルト値 `リファレンス`があり、所有者 (注文エンティティ) は `デフォルト` です。 これは、 `1つの 'Customer' オブジェクトが複数の 'Order' オブジェクトに関連付けられているので、顧客が複数の注文を持つことができます。` しかし注文は1人の顧客しかいません

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

### 4.2 デフォルトの所有権を持つ多くの関連付け {#many-to-many}

デフォルトの所有権を持つ多対多の関連付けは、関連を描画し、typeプロパティを `参照セット` に設定し、所有者を `デフォルト`のままにすることによって作成されます。

In this example, a **Customer** can have multiple **Groups**, and a **Group** can have multiple **Customers**. これは、 `に多重度が設定されている場合と同じです。複数の 'グループ' オブジェクトが複数の '顧客' オブジェクト` に関連付けられており、 `'顧客' オブジェクトは 'グループ' オブジェクト` を参照します。

![](attachments/associations/association-customer-group.png)

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

### 4.3 ワンツーワン協会

owner プロパティを `both` に設定することで、1 対 1 の関連付けが作成されます (typeプロパティはデフォルト値の `Reference` のままにします)。

In this example, a **Customer** can have one **Profile**, and a **Profile** can have one **Customer**. これは、 `1つの 'Customer' オブジェクトが1つの 'Profile' オブジェクト` に関連付けられているのと同じです。

![](attachments/associations/association-customer-profile.png)

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

### 4.4 二重所有権を持つ多数の協会 {#many-to-many-both}

オーナープロパティを `` に設定し、type プロパティを `参照集合` に設定することで、両方のエンティティがオーナーである多対多の関連付けを作成します。

この例では、 **Accountant** は複数の **グループ** を持つことができ、 **グループ** は複数の **<unk>** を持つことができます。 これは、 `に多重度が設定されている場合と同じです。複数の「グループ」オブジェクトが複数の「会計」オブジェクト` に関連付けられており、 `「会計」と「グループ」オブジェクトが互いに参照している場合と同じです。`:

{{% image_container width="500" %}}![](attachments/associations/association-accountant-group.png)
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
