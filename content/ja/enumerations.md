---
title: "列挙型"
parent: "リソース"
menu_order: 40
tags:
  - "studio pro"
  - "列挙型"
  - "列挙値"
  - "列挙値"
aliases:
  - /refguide8/enumeration-values.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/enumerations.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

列挙は定義済みの値のリストを定義します。 列挙型は列挙型に使用されます。 例えば、注文のステータスは **、 *クローズ*、または *進行中* となります。 ですから、注文ステータスの列挙は、3つの値で構成されます: **, *閉じた*, および *In_Progress*.

列挙は、1 つまたは複数の [列挙値](enumerations#enum-properties) で構成されます。 各値は1つのオプションを表します。 列挙型の属性は、初期化されていない状態を表すこともできます: 例えば、 注文にステータスを割り当てない場合、注文ステータスは *空*になります。

## 2 列挙の作成

新しい列挙を作成するには、次の手順を実行します。

1.  In the [Project Explorer](project-explorer), right-click the module or a folder you want to add enumeration to and in the list of actions, select **Add other** > **Enumeration**:

    ![](attachments/enumerations/add-enumeration.png)

2. **列挙の追加** ダイアログボックスで列挙の名前を入力します。

3.  **列挙値** ダイアログボックスで、 **新規** をクリックして列挙値を作成します。

    a  列挙値については **名前** と **図表番号** を入力してください。 必要に応じて **イメージ** を設定できます。 列挙プロパティの詳細については、 [列挙プロパティ](#enum-properties) セクションを参照してください。 <br />

    ![](attachments/enumerations/add-enum-value.png)

    B  **OK** をクリックして列挙値を保存します。

4. 作成する各列挙値について、ステップ 3 を繰り返します。

5. **OK** をクリックして列挙を保存します。

プロジェクトに新しい列挙を追加しました。 プロジェクトの列挙型の異なる属性に同じ列挙を使用できます。

## 3 列挙プロパティ {#enum-properties}

列挙型には以下のプロパティがあります。

* **名前** – 列挙の名前

*  **列挙値** - 列挙値は1つ以上の列挙値を持つ。 各値はオプションのいずれかを表します。 列挙値とそれらのプロパティの詳細については、 [列挙値プロパティ](#enum-value-properties) のセクションを参照してください。

    ![](attachments/enumerations/enumeration-properties.png)

### 3.1 列挙値のプロパティ {#enum-value-properties}

列挙値プロパティを以下に示します。

* **図表番号** - 列挙値のキャプションは、エンドユーザーがこの列挙値に対して見ているテキストです。 これは翻訳可能なテキストです。 詳細については、 [言語メニュー](translatable-texts) を参照してください。

* **名前** - 列挙値の名前は、プロジェクト内の列挙値を参照するために使用される値の技術的な名前です。

    {{% alert type="warning" %}}列挙値の名前は、列挙値をデータベースに格納するためにも使用されます。 そのため、列挙値の **名前** を変更することはできません。データベース内のデータは無効になります。 The **Caption**, however, can be changed and this is the text that is displayed to the end-users.<br />The name of an enumeration value must be a technical name without spaces and special characters. 列挙値のキャプションは任意の文字を使用できます。 例えば、列挙値は *In_Progress* を名前に、 *In Progress* をキャプションにすることができます。
    {{% /alert %}}

* **イメージ** – 列挙値で選択した画像をデータグリッド列に表示できます。 この場合、列の列挙形式は *イメージ* でなければなりません。 データグリッド列の詳細については、 [グリッド列](columns) を参照してください。

## 4 続きを読む

* [属性](attributes)
* [エンティティ](エンティティ)

