---
title: "関連 & そのプロパティ"
parent: "ドメインモデル"
tags:
  - "ドメインモデル"
  - "関連"
---

## 1つの紹介

関連付けはエンティティ間の関係を記述します。 ドメイン モデルでは、関連付けは、2 つのエンティティ間の線または矢印で表されます。

関連付けの値は、関連付けの _[所有者](associations#owner)_ であるエンティティのオブジェクトからのみ表示または編集できます。 どちらか一方または両方のエンティティが関連付けの所有者になることができます。 あるエンティティが所有者である場合、所有者から他のエンティティを指す矢印があります。 両方のエンティティが所有者である場合、2つのエンティティの間に行があります。

関連付けの [多重度](#multiplicity) (または参照オブジェクトの数) は、関連付けの両側の数 1 (`1`) または星 (`*`) で示されます。

In the example below, the arrow indicates that **Order** is the owner of the association, and the `1` and `*` indicate that one customer is associated with many orders:

![](attachments/domain-model-editor/918217.png)

{{% alert type="info" %}}

持続可能エンティティと非持続可能エンティティの関連付けは、非持続可能エンティティで開始し、所有者が **デフォルト**でなければなりません。 持続可能で持続不可能なエンティティについての詳細は、 [持続可能性](persistability) を参照してください。

{{% /alert %}}

## 2つの関連プロパティ

関連付けをダブルクリックすると、そのプロパティが開きます。

![関連のプロパティ](attachments/association-properties/dm-association-properties.png)


関連付けには以下のプロパティがあります。

* [名前](#name)
* [ドキュメント](#documentation)
* [多重度](#multiplicity)
* [ナビゲーション](#navigability)
* [動作を削除](#delete-behavior)

### 2.1 名前 {#name}

関連付けの名前は、フォーム、マイクロフロー、等からそれを参照するために使用されます。

### 2.2 ドキュメント {#documentation}

このフィールドでは、この要素にメモとドキュメントを書くことができます。

### 2.3 多重性 {#multiplicity}

多重度は参照可能なオブジェクトの数を定義します。 これは、連想の両側でナンバーワン(`1`)またはスター(`*`)で示されています。

多重度には以下のタイプがあります:

* 1 対1 – 1 X オブジェクトが 1 つの Y オブジェクトに関連付けられています
* 1対多のXオブジェクトが複数のYオブジェクトに関連付けられています
* 多対多―複数の X オブジェクトが複数の Y オブジェクトに関連付けられています

関連が1対多または多対多のタイプの場合は、関連付けの所有者と方向が表示されます。 関連が1対1の場合、両方のエンティティは所有者です。 所有権についての詳細は、 [関連](associations#owner) の *オーナー* セクションを参照してください。

### 2.4 Navigability {#navigability}

Navigability は、多対多の関連付けの所有者を変更します。 Navigability には、次のオプションがあります:

* XオブジェクトはYオブジェクトを参照します – 関連付けの所有者はXです
* X と Y オブジェクトは互いを参照します – どちらのエンティティも所有者です

### 2.5 動作の削除 {#delete-behavior}

削除動作は、オブジェクトが削除されたときに関連するオブジェクトに何が起こるかを定義します。 以下のオプションは、関連付けの各端に設定できます。

| 値                                                                                                 | 説明                                     |
| ------------------------------------------------------------------------------------------------- | -------------------------------------- |
| {name of entity} オブジェクトを削除しますが、 {name of other entity} オブジェクトを保持します                               | オブジェクトが削除されると、関連するオブジェクトは削除されません。      |
| {name of entity> object and {name of other entity} object(s) 同様に削除します                             | オブジェクトが削除されると、関連するオブジェクトも削除されます。       |
| delete {name of entity> object only if it is not associated with {name of other entity} object(s) | オブジェクトは他のオブジェクトと関連付けられていない場合にのみ削除できます。 |

* *Default value*: delete {name of entity} object but keep {name of other entity} objects(s)

この削除動作は、 **顧客** が削除されたときに関連する **プロファイル** を削除する場合に使用されます。

![](attachments/domain-model-editor/918143.png)

この削除動作は、 **顧客** が **注文** に関連付けられていない場合にのみ使用されます。

![](attachments/domain-model-editor/918146.png)

## 3 続きを読む

* [関連](関連)