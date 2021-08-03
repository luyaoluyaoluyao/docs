---
title: "テキスト"
parent: "コモンウィジェット"
menu_order: 10
tags:
  - "studio pro"
  - "テキスト"
  - "テキストウィジェット"
  - "共通ウィジェット"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/text.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

テキストウィジェットには、必要に応じてパラメータを含めることができるテキストが表示されます。 すべての属性はこの属性の値に置き換えられます。 例えば、 [データ ビュー](data-view) にテキストウィジェットを配置し、パラメータを追加することで、ユーザーに挨拶メッセージを表示できます。

![テキストウィジェット](attachments/common-widgets/text.png)

空のコンテナに入力し始めると、Studio Pro は自動的にテキストウィジェットを生成してテキストを表示します。

## 2つのプロパティ

以下の画像にテキストプロパティの例を示します。

{{% image_container width="300" %}}![テキストのプロパティ](attachments/common-widgets/text-properties.png)
{{% /image_container %}}

テキストプロパティは以下のセクションで構成されています:

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般セクション {#general}

#### 2.3.1 図表番号 {#caption}

**図表番号** は表示されるテキストを定義します。 図表番号には、たとえば、 {1} のように、括弧間で書かれたパラメータを含めることができます。

パラメータの使用に関する詳細は、以下の [パラメータ]() セクションを参照してください。

#### 2.3.2 パラメータ {#parameters}

パラメータは、その値が表示される属性です。 **パラメータ**を表示するには、次のいずれかを実行します。

* プロパティの **図表番号** 設定をダブルクリックします。

*  Double-click the text widget on the page and click **Edit** in the **General** section > **Caption**:

    ![パラメータを開く](attachments/common-widgets/caption-edit-button.png)

パラメータには以下の設定があります:

* **Index** - パラメータの識別番号

* **属性 (path)** - 値が表示される属性

*  **書式** - 属性値を表示するフォーマット

    ![パラメーターの設定](attachments/common-widgets/parameter-settings.png)

##### 2.3.2.1 新しいパラメータの追加

パラメータを使用するには、次の操作を行います。

1. **テキスト** ウィジェットを、 [データ ウィジェット](data-widgets) 内側のように、エンティティのコンテキスト内に配置する必要があります。

2. テキストウィジェットのプロパティで **図表番号** 設定をダブルクリックします。

3.  **図表番号の編集** ダイアログ ボックス > **パラメータ** セクションで **新規作成**:

    ![新しいパラメータの追加](attachments/common-widgets/adding-parameter.png)

4. **テンプレートパラメータの編集** ダイアログボックスで、 **を選択**をクリックし、属性を選択して選択を確定します。

5.  In the **Caption** setting, write the text you would like to display and type **Index** of the parameter you would like to include. In the example below, to include a full name of your customer and a number of unread messages, you need to use indexes {1} for the *FullName* attribute, and {2} for the *NrOfUnread* attribute:

    ![パラメータの例](attachments/common-widgets/parameters-example.png)

##### 2.3.2.2 パラメータに対するその他のアクションの実行

新しいパラメータの追加に加えて、パラメータに対して以下のアクションを実行できます。

* **削除** – パラメータを削除するには、削除をクリックするか、キーボードの <kbd>削除</kbd> を押します

* **編集** – パラメータをダブルクリックして編集するか、編集をクリックします

* **Move up** – to move a parameter up in the list of parameters and also to change its index, click **Move up**

*  **Move down** – to move a parameter down in the list of parameters and also to change its index, click **Move down**

    ![パラメーターアクション](attachments/common-widgets/parameter-actions.png)

#### 2.3.3 レンダリングモード

レンダリングモードでは、テキストの表示方法を決定します。

| 値               | 説明                                                                                                  |
| --------------- | --------------------------------------------------------------------------------------------------- |
| テキスト  *(デフォルト)* | テキストは、ページ上の前/次のテキストとともにインラインでレンダリングされます (`<span>` HTMLのタグ)。                                   |
| 段落              | テキストは別の段落としてレンダリングされます (`<p>` HTMLのタグ)。                                                       |
| 見出し 1 - 見出し 6   | テキストは選択された見出しとしてレンダリングされます (例えば、HTMLの `<h1>` タグ)。 **見出し1** は見出しの最大タイプです。 **見出し6** は最も小さいものです。 |

### 2.4 表示セクション {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 続きを読む

* [ページ](page)
* [一般的なウィジェット](コモンウィジェット)
* [ページエディターで共通のプロパティ](common-widget-properties)