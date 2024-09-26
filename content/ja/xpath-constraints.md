---
title: "XPath 制約"
parent: "xpath"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-constraints.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

取得されたデータをフィルタリングするために、任意の Xpath クエリに制約を追加することができます。 常に有効な [式](xpath-expressions) の形式をとる必要があります。 [演算子](xpath-operators)、 [関数](xpath-constraint-functions)、 [キーワード、またはシステム変数](xpath-keywords-and-system-variables) と組み合わせた1つ以上の変数で構成される必要があります。

例えば、このクエリはJansenと同じ名前のすべての顧客を取得します。

```java
//Sales.Customer[Name = 'Jansen']
```

The first half of the query is responsible for defining the entity to retrieve and the second half (between the brackets ) *constrains* the data to a certain attribute. この制約は括弧で囲まれている(そして常にそうであるべき)ことに注意してください。

単一のクエリに複数の制約を追加することができます。これは、 `id` クエリを除くすべてのクエリに当てはまります。 最も一般的には、最初のブラケットを閉じた後に新しいブラケットを開くという簡単な方法があります。

{{% alert type="warning" %}}
Studio Pro では、完全なクエリを記述せず、制約のみを記述します。 エンティティはコンテキストによって暗黙的に決定されます。 ですから、 `//Sales.Customer[Name='Jansen']`の代わりに、顧客のコンテキストで `[Name='Jansen']` を記述するだけです。 Java では、double スラッシュ (`//`) とエンティティ名を含む、クエリ全体を記述する必要があります。
{{% /alert %}}

## 2つの例

このクエリは、ヤンセンと同じ名前でロッテルダムに住んでいるすべての顧客を取得します。

```java
//Sales.Customer[Name = 'Jansen'][Sales.Customer_Address/Sales.Address/City = 'Rotterdam']
```

制約を `または` または `または` [演算子](xpath-operators) と組み合わせることもできます。 このクエリは、ロッテルダムに住んでいるJansen *と* に等しい名前のすべての顧客を取得します。

```java
//Sales.Customer[Name = 'Jansen and Sales.Customer_Address/Sales.Address/City = 'Rotterdam']
```

このクエリでは、ヤンセンまたはロッテルダムに住んでいるすべての顧客を取得します。

```java
//Sales.Customer[Name = 'Jansen または Sales.Customer_Address/Sales.Address/City = 'Rotterdam']
```

括弧を使用すると、制約をグループ化して優先順位を定義できます。 このクエリは、名前だけでなく、ロッテルダムに住んでいるすべての顧客を取得します。

```java
//Sales.Customer[( Name = 'Jansen or Name = 'Smit' ) and Sales.Customer_Address/Sales.Address/City = 'Rotterdam']
```

場合によっては、制約されているデータを制限するためにサブ制約を定義することも便利かもしれません。 これは、元の制約の括弧内にサブ制約を追加することで簡単に実現できます。 サブ制約は実際のクエリではなく、メタ制約にのみ適用されるため、2 つの個別の制約と混同しないでください。 そのため、括弧は次々に開かれ、閉じられることはありません。サブ制約は完全にメタ制約の範囲内でなければなりません。 十分に複雑なクエリでは、1つの制約が終了し、もう1つの制約が始まる場所が混乱する可能性があります。 これを防ぐために、ブラケットセットを注意深く追跡してください。

このクエリは、管理者ロールを持つすべてのユーザーを取得します。

```java
//Sales.User[id = '[%UserRole_Administrator%]']]
```

このクエリはロッテルダムまたはロスダンに住むすべての顧客を取得します。

```java
//Sales.Customer[Sales.Customer_Address/Sales.Address[City = 'Rotterdam' or City = 'Losdun']]
```

このクエリは、New Amsterdam、Guyanaに住んでいるすべての顧客を取得します(たとえば、New Amsterdam、Indianaなどに住んでいる顧客とは異なり)。

```java
//Sales.Customer[Sales.Customer_Address/Sales.Address[City = 'New Amsterdam']/Sales.Adress_Country/Sales.Country/Name = 'Guyana']
```

単一の制約で同じパスを複数回使用しないようにします。 例えば、ロッテルダムとロスダンの例は次のようになります。

```java
//Sales.Customer[Sales.Customer_Address/Sales.Address/City = 'Rotterdam' or Sales.Customer_Address/Sales.Address/City = 'Losdun']
```

ただし、このクエリは非効率的に実行されるため、クエリ処理が大幅に遅くなります。

