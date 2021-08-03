---
title: "決定"
parent: "意思決定|意思決定|意思決定|意思決定|意思決定|意思決定|意思決定||意思決定|意思決定|"
menu_order: 3
tags:
  - "studio pro"
  - "決定"
  - "排他的分割"
aliases:
  - /refguide8/exclusive-split.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/decision.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

判断は、条件に基づいて選択を行い、出力シーケンスの1つだけが流れる要素です。 たとえば、異なる成績を持つ顧客に対して異なる注文フォームを表示するには、決定を使用する必要があります。 ブロックされた顧客が注文するのを防ぐためです

## 2つのプロパティ

以下の図に、決定プロパティの例を示します。

{{% image_container width="50%" %}}
![](attachments/decisions/decision-properties.png)
{{% /image_container %}}

デシジョン プロパティ ペインは以下のセクションで構成されています:

* [一般的な](#common)

### 2.1 Common {#common}

#### 2.1.1 図表番号

詳細については、 [Common Properties](microflow-element-common-properties#caption) の *図表番号* セクションを参照してください。

#### 2.1.2 決定タイプ

**Decision type** は、決定の条件を定義するために式または規則を使用するかどうかを定義する。 考えられる決定の種類については、以下の表を参照してください。

| Option           | 説明                                                                                                                   |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| [式](#expression) | 式は、ロジックに基づいてオブジェクトや変数を作成または変更するために使用できます。                                                                            |
| [ルール](#rule)     | ルールは特別な種類のマイクロフローです その結果は、サブマイクロフローを呼び出すのではなく、そのサブマイクロフローのリターン変数を使用することができます。 複雑な決断をルールにまとめて、さまざまな場所で再利用できるという考え方です。 |

##### 2.1.2.1 式 {#expression}

**Type** プロパティが **Expression**に設定されている場合 ここで入力された式は、決定の条件を定義するために使用されます。 式の詳細については、 [Microflow Expressions](expressions) を参照してください。

式はブール値または列挙値を返します。

ブール値を生成する式では、 **true** と **false** の 2 つのフローが使用できます。 たとえば、顧客のメールアドレスが検証されているかどうかを確認したい場合は、結果としてブール値になる式を使用できます。

列挙型で利用可能な条件の数は、対応する列挙値によって異なります。 There is also the *empty* condition available for enumeration: if the enumeration parameter or an attribute of an object is unassigned, the sequence flow with the caption **(empty)** is followed.

顧客の成績ごとに異なる注文フォームを開く場合は、決定を使用できます。 microflow パラメータは *Customer* です。 顧客が持っているグレードに応じて、異なるシーケンスフローがフォローされ、異なる注文フォームが開かれます。 エンドユーザーが顧客の成績を選択する必要がありますが、そうしない場合。 **(空)** と表示されるフローがフォローされ、エンドユーザーにエラーメッセージが表示されます。

{{% image_container width="400" %}}
![](attachments/decisions/decision-example.png)
{{% /image_container %}}

列挙型の値ごとに異なる方向に移動したいので、列挙型を含む属性のみを使用する必要があります。 上記の例の式は`$Customer/Grade` です。

##### 2.2.2.2 ルール {#rule}

If the **Type** property is set to **Rule**, a [rule](rules) can be selected to define the condition of the decision. サブマイクロフローを呼び出し、そのサブマイクロフローの戻り値を使用する代わりに、ルールの結果を決定に使用できます。

**ルール** 意思決定タイプのプロパティは次のとおりです。

* **ルール** – ルールを選択できます。

* **パラメータ** - ルールの各パラメータについては、 [表現](expressions) を使用して引数を指定する必要があります。 たとえば、顧客が特定のステータスに値するかどうかを決定するルールは、顧客オブジェクトをパラメータとして持つことになります。

    {{% image_container width="350" %}} ![](attachments/decisions/rule-properties.png)  {{% /image_container %}}

#### 2.1.3 エラー処理タイプ

詳細については、 [Common Properties](microflow-element-common-properties#error-handling) の *Error Handling Type* セクションを参照してください。