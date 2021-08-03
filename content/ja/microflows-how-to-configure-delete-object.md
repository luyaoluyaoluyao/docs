---
title: "オブジェクトの削除アクションを設定する"
category: "マイクロフロー"
menu_order: 80
description: "この方法では、データビューで削除オブジェクトアクションを設定し、Mendix Studio でリストビューを設定するプロセスを説明します。"
tags:
  - "スタジオ"
  - "ページエディタ"
  - "オブジェクトの削除"
  - "リスト表示"
  - "データビュー"
  - "どうやって?"
---

## 1つの紹介

この方法では、Mendix Studio で削除オブジェクトアクションを設定する方法を説明します。

**以下の方法を教えてくれます。**

* **リスト ビュー** で [オブジェクト](page-editor-data-view-list-view#list-view-properties) を削除する
* **データビュー** で [オブジェクト](page-editor-data-view-list-view#data-view-properties)を削除するアクションを設定する

この方法では、以下のユースケースを説明します。顧客のリストから顧客名を削除します。

{{% alert type="info" %}}

ボタンや静止画像などのウィジェットのクリック操作で **Delete Object** を設定できます。 この方法では、 **Delete** ボタンをクリック操作で **Delete Object** を持つウィジェットの例として使用します。 詳細については、ウィジェットの [イベントセクション](page-editor-widgets-events-section#delete-object-action) 内の *Object Action* のセクションを参照してください。

{{% /alert %}}

## 2 ドメインモデルの設定とページの作成

To list customers' names and to show a more detailed information under the list, you need to create an entity *Customer*, add attributes *Name* and *Address* to it, and then create a page where you will list names of customers.

ドメインモデルを設定してページを作成するには、次の操作を行います。

1. [ドメイン モデル](domain-models) を開きます。

2. エンティティ *顧客* を作成する。 For more information on how to create the entity, see section [3 Adding New Entities](domain-models) in *Domain Models Overview*.

3.  For the **Customer** entity, create an attribute (for more information on how to create an attribute, see section [4 Adding New Attributes](domain-models) in *Domain Models Overview*) and do the following:<br/>

    a 属性の **名前** を *名前* に設定します。<br/>

    B [**Type**](domain-models-attributes) を **String** に設定します。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/name-attribute.png)<br/>    
   C **Create** をクリックして新しい属性を追加します。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/customer-entity.png)

4. 文字列型の属性 *アドレス* を作成するには、ステップ 3 を繰り返します。

5.  今、あなたは顧客の名前が表示されるページが必要です。 空白のページを作成し、 *顧客* に名前を付けます。 ページの作成に関する詳細については、 [ページ](page-editor) の *3.2 新規ページ* の作成 を参照してください。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/create-page.png)

新しい空白ページが作成されます。

![](attachments/microflows-how-to-configure-delete-object/blank-page-created.png)

## 3 リストビューでのオブジェクト削除アクションの設定

これでリストビューを構成し、ユーザーがボタンをクリックしたときに対応する顧客を削除する [**オブジェクト** アクション](page-editor-widgets-events-section#delete-object-action) でボタンを追加します。 次の操作を行います:

1. 作成したページ *顧客* を開きます。

2.  **Building Blocks** > **Lists** find **List 1**, drag and drop it to the page. このBuilding Blockはデフォルトでリストビューを含んでいます。

    ![](attachments/microflows-how-to-configure-delete-object/list-1.png)

3.  次に、リスト ビューを構成する必要があります。 リストビューのプロパティを開き、次の操作を行います。 <br/>

    a  **データベース** を **データ ソース** として選択します。<br/>

    B  **エンティティ** を **顧客** に設定します。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/list-view-properties.png) <br/> 今、リスト ビューは、 **顧客** エンティティに接続されています。 <br/>

4.  テキスト *名前* を選択し、 **プロパティ** で以下を行います:<br/>

    a **コンテンツ**で、 *名前* というテキストを削除します。<br/>

    B **属性の追加** をクリックし(または <kbd>Ctrl</kbd> + <kbd>スペース</kbd>を押して)、 **Name** 属性を選択します。 <br/>

    ![](attachments/microflows-how-to-configure-delete-object/text-content.png)<br/> テキストウィジェットが **Name** 属性に接続され、リスト内の顧客名が表示されます。<br/>

5.  矢印として表示されているボタンをクリックして削除します。

    ![](attachments/microflows-how-to-configure-delete-object/arrow-button.png)

6.  In **Toolbox** > **Widgets** > **Buttons** find **Delete Object**, 矢印ボタンから左にあるコンテナ内にドラッグ&ドロップします。

    ![](attachments/microflows-how-to-configure-delete-object/container-for-the-delete-button.png)

7.  In **Properties** for the **Delete** button, you can see that the **On Click** action is set to **Delete Object** automatically, and caption is set to **Delete**, because the widget is preconfigured in Studio.

    ![](attachments/microflows-how-to-configure-delete-object/delete-button-properties.png)

顧客名を一覧表示するページを作成していること。 ユーザーが **削除** 行のいずれかをクリックした場合。 この行に記載されているお客様は、お客様の詳細とともにアプリから削除されます。 詳細については、ウィジェットの [イベントセクション](page-editor-widgets-events-section#delete-object-action) の *オブジェクトアクション* のセクション を参照してください。

## 4 データビューでのオブジェクト削除アクションの設定

データ ビューで [**Object** アクション](page-editor-widgets-events-section#delete-object-action) を削除することもできます。 この場合、 **Delete Object** は接続されたオブジェクトを削除します。 データビューとページの **削除** ボタンを設定するには、以下を行います:

1.  On the page named *Customers*, open the **Layout Grid** properties (use a breadcrumb at the bottom of the screen to find the layout grid).

    ![](attachments/microflows-how-to-configure-delete-object/breadcrumb.png)

2.  **プロパティ** > **行を追加**, データビューをそこに配置する必要がある行を追加するボタンをクリックします。

    ![](attachments/microflows-how-to-configure-delete-object/add-row.png)

3. In **Toolbox** > **Widgets** > **Data Containers**, データビューを検索し、列内にドラッグ&ドロップします(新しい行と一緒に追加されました)。

4.  次に、データ ビューを構成する必要があります。 データ ビューの **プロパティ** で、次の操作を行います。 <br/>

    a **データ ソース** を **リスト ウィジェット** に設定します。<br/>

    B **ウィジェット** を **エンティティ顧客との一覧表示** に設定します。 現在、データ ビューのデータ ソースは、同じページに配置されているリスト ビューになります。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/data-view-list-widget.png)

5. データビューをデータで埋める必要があります。 In **Toolbox** >**Widgets** > **Typography**, select **Text**, drag and drop it inside data view content.

6.  先ほど追加した **テキスト** ウィジェットから見出しを作成します。 **テキスト** の **プロパティ** を開き、次の操作を行います:<br/>

    a **コンテンツ**で、 *テキスト* という単語を削除し、 *Customer Details* と入力します。<br/>

    B **レンダリングモード** を **H4** に設定します。 <br/>

    ![](attachments/microflows-how-to-configure-delete-object/text-heading4.png)<br/>

7. 選択した顧客の詳細を表示するテキストボックスを追加します。 **ウィジェット** > **入力要素**で、 **テキストボックス**を選択し、データビューコンテンツ内にドラッグ&ドロップします。

8.  Open the **Properties** of the **Text Box**, and in **Data Source**, set **Attribute** to **Name** (the label for the text box will be changed to **Name** automatically).

    ![](attachments/microflows-how-to-configure-delete-object/text-box-name.png)

9. ステップ7を繰り返して、もう1つ **テキストボックス** をページに追加します。

10. Open the **Properties** of the **Text Box**, and in **Data Source**, set **Attribute** to **Address** (the label for the text box will be changed to **Address** automatically).

    ![](attachments/microflows-how-to-configure-delete-object/text-box-address.png)

11. In **Toolbox** > **Widgets** > **Buttons** find **Delete Object**, データビューの中にドラッグ&ドロップします。

12. The button is already preconfigured: its **On Click Action** is set to **Delete Object**, and **Caption** is set to **Delete**. しかし、あなたはそれにいくつかのスタイリングを追加します。 次の操作を行います:<br/>

    a **General** セクションで、 **Style** を **Danger** に設定します。<br/>

    B **Design** セクションで、 **Align Self** を **Right** に設定します。<br/>

これで、リストでこの顧客を選択すると、顧客の名前と住所が表示されるデータビューを設定できます。

![](attachments/microflows-how-to-configure-delete-object/configured-page.png)

The workflow for the **Delete** button in the data view (the red **Delete** button) is the following:

1. ユーザーはリスト内の顧客の名前を選択します。

2. 顧客の詳細(名前と住所)は、以下のデータビューに表示されます。

3. ユーザーは **削除** をクリックします。

4. 顧客のレコード全体が削除されます。

   ![](attachments/microflows-how-to-configure-delete-object/published-page-example.png)

詳細については、ウィジェットの [イベントセクション](page-editor-widgets-events-section#delete-object-action) の *オブジェクトアクション* のセクション を参照してください。

おめでとうございます リスト ビューとデータ ビューで **削除** ボタンを設定しています。 
