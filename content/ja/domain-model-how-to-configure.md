---
title: "ドメインモデルの設定"
description: "この方法では、Mendix Studio でドメイン モデルを構成するプロセスを説明します。"
menu_order: 30
tags:
  - "スタジオ"
  - "ドメインモデル"
  - "決定"
  - "ドメインモデル"
---

## 1つの紹介

この方法では、Mendix Studio でドメイン モデルを構成する方法を説明します。

**以下の方法を教えてくれます。**

* ドメインモデルに含めるデータを定義します
* 異なるタイプのエンティティを作成
* 属性を作成
* 関連付けを作成

この方法では、次のようなユースケースを説明します。

オンラインショッピングアプリのドメインモデルを設定しています。

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio/domain-models) を参照してください。

## 3 どのデータを含めるか定義する

典型的なプロセスを理解することで、どのデータをドメインモデルに含めるかを定義することができます。 オンラインショッピングアプリの新規顧客向けのワークフローは次のようになります。

1. 顧客はオンラインショッピングアプリに登録し、以下の詳細を入力します。
   1. フルネーム
   2. 住所
   3. Eメールアドレス
   4. 誕生日
2. 登録が完了すると、 *一意の ID* が顧客に割り当てられます。
3. 顧客が *製品* を閲覧し、次の製品詳細が表示されます:
   1. 商品画像
   2. 名前
   3. 説明
   4. 在庫状況
   5. 価格
   6. 仕入先
   7.  製品ID
4. 顧客はショッピングカートに商品を追加します。
5. ショッピング カートでは、すべてのアイテムは、1 行あたり *数量* と *価格* を示す別の行として表示されます。 顧客は注文をチェックし、支払いを行う そして、 *注文の詳細* と *注文の詳細* の確認 *日付* を取得します。

上記の説明に基づいて、データを次の要素に分割できます。

* [顧客](#customer)
* [商品](#product)
* [ご注文](#order)

## 4 製品の定義 {#product}

製品は、オンラインショッピングアプリの主な要素の一つであるとして ドメインモデルの製品を表すエンティティを作成する必要があります。 名前や価格などの製品を定義する情報は、 **Product** エンティティの属性である必要があります。

ドメインモデルに製品を追加するには、以下の手順に従ってください。

1. **製品** エンティティを作成します。 次の操作を行います:

    1. [ドメイン モデル](/studio/domain-models) を開きます。

    2. **ツールボックス**を開き、ドメインモデルで **エンティティ** をドラッグ&ドロップします。

       {{% image_container width="350" %}}![Adding a New Entity](attachments/domain-model-how-to-configure/adding-entity.png){{% /image_container %}}

    3. **新規エンティティの作成**、ダイアログボックスで、名前を **Product** に設定し、 **Create** をクリックします。

2. **製品** エンティティの属性を作成します。 次の操作を行います:<br />
    1. 図形を選択し、 **新規属性** をクリックします。

        {{% image_container width="250" %}}![Adding New Attribute](attachments/domain-model-how-to-configure/adding-new-attribute.png){{% /image_container %}}

    2. In the **Create New Attribute** dialog box, set the name to *Product_ID*, set the type to *Autonumber* (so that ID for a product will be assigned automatically), and click **Create**:

        {{% image_container width="450" %}}![Create New Attribute Dialog Window](attachments/domain-model-how-to-configure/create-new-attribute-dialog.png){{% /image_container %}}

    3. *Name* 属性を追加するには、ステップ 2a を繰り返します。

    4. In the **Create New Attribute** dialog box, set the name to *Name*, set the type to *String*, and click **Create**.

   5. *説明* 属性を追加するには、ステップ 2a を繰り返します。

   6. In the **Create New Attribute** dialog box, set the name to *Description*, set the type to *String*, and click **Create**.

   7. 製品が利用可能かどうかを示す属性を作成するには、ステップ 2 a を繰り返します。

   8. In the **Create New Attribute** dialog box, set the name to *Available*, set the type to *Boolean*, and click **Create**.

   9. ステップ2aを繰り返し、 *Price* 属性を作成します。

   10. In the **Create New Attribute** dialog box, set the name to *Price*, set the type to *Decimal*, and click **Create**.

   11. *ベンダー* 属性を作成するには、ステップ2aを繰り返します。

   12. In the **Create New Attribute** dialog box, set the name to *Vendor*, set the type to *String*, and click **Create**.

3. 各製品には *イメージ*がありますが、属性として作成していません。 イメージエンティティを格納できる特別なタイプのエンティティを作成する必要があります。 そして、その名前を *Product_Image* に設定します。 以下の手順に従ってください。

    1.  **Toolbox**を開き、 **Image Entity** をドメインモデルにドラッグ&ドロップします。

        {{% image_container width="300" %}}![Image Entity](attachments/domain-model-how-to-configure/adding-image-entity.png){{% /image_container %}}

    2. **Create New Image Attribute** ダイアログボックスで、名前を *Product_Image* に設定し、 **Create** をクリックします。
 {{% alert type="info" %}} *Name* と *Size* 属性は自動的に作成され、読み取り専用です。
        {{% /alert %}}

よくできました！ **製品** エンティティ、その属性、 **製品画像** イメージエンティティを作成しました:

{{% image_container width="500" %}}![Product and Product Image Entities](attachments/domain-model-how-to-configure/product-and-product-image.png){{% /image_container %}}

## 5 順序の定義 {#order}

注文情報は以下に分けることができます:

* **注文** – 注文の状況、注文番号、顧客の名前、住所などの一般的な情報。
* **Order line** – 注文された商品、数量、価格
* **注文の確認** – 注文が完了したことを確認する

したがって、3つのエンティティを作成する必要があります: *Order*, *Order_Line*, and *Order_Confirmation*.

次の操作を行います:

1. **Order** エンティティを作成します。 **Product** エンティティを作成するのと同じ方法を使用します。 詳細については、 [製品の定義](#product) セクションを参照してください。

2. **Order** エンティティの属性を作成: *Order_Number* と *Status*. 次の操作を行います:<br />
    1. 図形を選択し、 **新規属性** をクリックします。

    2. In the **Create New Attribute** dialog box, set the name to *Order_Number*, set the type to *Autonumber*, and click **Create**.

    3. ステップ2aを繰り返し、 *Status* 属性を作成します。

    4. 属性 **名前** を *ステータス* に、 **タイプ** を *列挙* に設定します。 列挙には、 *Placed* や *Shipped* など、さまざまなステータス値が含まれます。

    5. **Select enumeration** をクリックして、新しい [enumeration](/studio/domain-models-enumeration) を作成します。

        {{% image_container width="450" %}}![Select Enumeration](attachments/domain-model-how-to-configure/select-enumeration.png){{% /image_container %}}

    6. **列挙の選択** ダイアログボックスで、右上隅にあるプラスアイコンをクリックして新しい列挙を追加します。

    7. In the **Create new enumeration** dialog box, click **Add Item** (*Status* is filled out automatically for the **Name**).

        {{% image_container width="450" %}}![Create New Enumeration](attachments/domain-model-how-to-configure/create-new-enumeration.png){{% /image_container %}}

    8. *と* を **図表番号** (**名前** は自動的に *注文済み* として記入されます)。

    9. **Add Item** をクリックし、上記の手順を繰り返して、 **Paid**を作成します。 **出荷済み** , ** ** ステータス ****, **配信済み**, **キャンセル済み** ステータス.

        {{% image_container width="450" %}}![Create Enumeration Items](attachments/domain-model-how-to-configure/create-enumeration-items.png){{% /image_container %}}

    10. **Create** をクリックしてダイアログボックスを閉じ、属性を作成します。

3. 注文銘柄と数量を保持するために、 **Order_Line** エンティティを作成します。 **Product** エンティティを作成するのと同じ方法を使用します。 詳細については、 [製品の定義](#product) セクションを参照してください。

4. **Order_Line** エンティティの属性を作成します。 次の操作を行います:<br />

    1. *Quantity* 属性を作成するには、ステップ 2 a を繰り返します。
    2. In the **Create New Attribute** dialog box, set **Name** to *Quantity*, set **Type** to *Integer*, and click **Create**.
    3. *Order_Price* 属性を作成するには、ステップ 2a を繰り返します。
    4. In the **Create New Attribute** dialog box, set **Name** to *Order_Price*, set **Type** to *Decimal*, and click **Create**.

5. **Order_Confirmation** エンティティを作成します。 注文確認は、ファイルが顧客に送信されますので。 **ファイル** エンティティを格納できる特別なタイプのエンティティを作成する必要があります。 次の操作を行います:

    1. **Toolbox**を開き、 **File Entity** をドメインモデルにドラッグ&ドロップします。

        {{% image_container width="350" %}}![Image Entity](attachments/domain-model-how-to-configure/adding-file-entity.png){{% /image_container %}}

    2. **新規ファイル属性の作成** ダイアログボックスで、名前を *Order_Confirmation* に設定し、 **Create** をクリックします。

6. **Order_Confirmation** エンティティの属性を作成します。 次の操作を行います:<br />

    1. *Date_Sent* 属性を作成するには、ステップ 2a を繰り返します。

    2. In the **Create New Attribute** dialog box, set **Name** to *Date_Sent*, set **Type** to *Date and Time*, and click **Create**.

        {{% alert type="info" %}} *Name* と *Size* 属性は自動的に作成され、読み取り専用です。
        {{% /alert %}}

オンラインショッピングアプリで注文を定義する3つのエンティティを設定しました。

## 6 顧客の定義 {#customer}

顧客は、別のエンティティを必要とするオンラインショッピングアプリのもう一つの重要な部分です。 名前やアドレスなどの顧客を定義する詳細は、このエンティティの属性である必要があります。

以下の手順に従ってください。

1. **顧客** エンティティを作成します。 **Product** エンティティを作成するのと同じ方法を使用します。 詳細については、 [製品の定義](#product) セクションを参照してください。
2. Create attributes for the **Customer** entity (for more information on how to create an attribute, see the [Adding New Attributes](/studio/domain-models#adding-new-attributes) section in *Domain Model*). 次の操作を行います:<br />
1. 図形を選択し、 **新規属性** をクリックします。
    2. In the **Create New Attribute** dialog box, set **Name** to *Customer_ID*, set **Type** to *Autonumber*, and click **Create**.
3. *Name* 属性を作成するには、ステップ 2a を繰り返します。
    4. In the **Create New Attribute** dialog box, set **Name** to *Name*, set **Type** to *String*, and click **Create**.
5. *Address* 属性を作成するには、ステップ 2a を繰り返します。
    6. In the **Create New Attribute** dialog box, set **Name** to *Address*, set **Type** to *String*, and click **Create**.
7. *Email* 属性を作成するには、ステップ 2 a を繰り返します。
    8. In the **Create New Attribute** dialog box, set **Name** to *Email*, set **Type** to *String*, and click **Create**.
9. ステップ2aを繰り返し、 *Date_Of_Birth* 属性を作成します。
    10. In the **Create New Attribute** dialog box, set **Name** to *Date_Of_Birth*, set **Type** to *Date and Time*, and click **Create**.


**顧客** エンティティとその属性を作成しました。

{{% image_container width="200" %}}
![顧客エンティティ](attachments/domain-model-how-to-configure/customer_entity.png)
{{% /image_container %}}

## 7 関連付けの作成

すべてのエンティティとそれらの属性を作成しました:

<img src="attachments/domain-model-how-to-configure/entities.png" alt="エンティティ" />

これらのエンティティが相互に関連付けられている方法を定義し、関連付けを作成する必要があります。 関連付けの詳細については、 [Associations](/studio/domain-models-association-properties) を参照してください。

まず、図形間の接続方法を定義します。

1. 1つの製品イメージは1つの製品にのみ接続されています。つまり、1対1の関連付けがあることを意味します。
2. 1つの注文に複数の商品(注文行)を含めることができます。つまり、 **注文** と **Order_Line** は、1対多の関連付けを持っていることを意味します。
3. **Order_Line** は、製品に関する情報を使用します。 1つの銘柄は複数の注文行に関連付けることができるため、 **Product** と **Order_Line** は1対多の関連付けが必要です。
4. 注文ごとに1つの注文確認書が発行されます。 これは、 **Order** オブジェクトが **Order_Confirmation** オブジェクトに関連付けられ、1 対 1 の関連付けがあることを意味します。
5.  注文は顧客によって行われます。 複数の注文は1つの顧客に接続できるため、 **注文** と **顧客** には1対多の関連があります。

エンティティ間の接続を定義したので、これらの接続の作成を開始できます。 以下の手順に従ってください。

1. **Product_Image** から **Product** への関連付けを作成します。 次の操作を行います:

    1. **Product_Image** エンティティにカーソルを合わせ、ドットアイコンをクリックします:

       {{% image_container width="500" %}}![Product Image and Product Association](attachments/domain-model-how-to-configure/product-image-product-association.png){{% /image_container %}}

    2. ドットを **Product** エンティティにドラッグします。

        {{% alert type="info" %}}エンティティ間の関連付けを作成する別の方法は、エンティティを選択して矢印アイコンをクリックすることです。
        {{% /alert %}}

    3. **プロパティ** を開き、多重度を1対1に変更します。

        {{% image_container width="300" %}}![Product_Image and Product Association](attachments/domain-model-how-to-configure/product-image-and-product-association.png){{% /image_container %}}

2. **Order_Line** から **Order_Line** への関連付けを作成します。上記の手順 1a と 1b に従ってください。 (必要な1対多重度はデフォルトで作成されます)。
3. 上記の手順 1a と 1b の後に、 **Order** から **Customer** への関連付けを作成します。 (必要な1対多重度はデフォルトで作成されます)。

4. **Order** から **Order_Line** への関連付けを作成します。 次の操作を行います:
    1. 上のステップ1aと1bに従ってください。
    2. **プロパティ** を開き、多重度を1対1に変更します。

すべての関連付けが作成されます。

{{% alert type="info" %}}

あるいは、 **新しい属性** > **ファイルまたは画像を追加**をクリックしてイメージまたはファイルエンティティを作成できます。 この場合、関連付けはデフォルトで作成されます。 詳細については、 [ドメインモデル](/studio/domain-models#adding-image-or-file-entities) の *新規イメージまたはファイルエンティティの追加* セクションを参照してください。

{{% /alert %}}

おめでとうございます オンラインショッピングアプリのドメインモデルを設定しました！

![ドメインモデルオンラインショッピングアプリ](attachments/domain-model-how-to-configure/domain-model-online-shop.png)

[ページ](/studio/page-editor) を作成するか、 [Buzz](/studio/collaboration-buzz) を使用して、チームの開発者やデザイナーとコラボレーションし、アプリエクスペリエンスを構築することができます。

## 8 続きを読む

* [ドメインモデル](/studio/domain-models)
* [ページ](/studio/page-editor)
* [マイクロフロー](/studio/microflows)
* [Buzz](/studio/collaboration-buzz)