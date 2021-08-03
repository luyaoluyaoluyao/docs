---
title: "ループ"
category: "マイクロフロー"
menu_order: 30
description: "Mendix Studioでループを説明します。"
tags:
  - "スタジオ"
  - "マイクロフロー"
  - "ループ"
  - "ループ"
---

## 1つの紹介

ループは、オブジェクトのリストを反復処理し、 [microflow](microflows) を構築するときにリストの各項目に対してアクションを実行するために使用されます。 たとえば、データベースから注文のリストを取得し、次にこのリストをループし、処理済みとして注文をマークできます。 ユースケースの詳細については、 [ループの設定](#loop-example) セクションを参照してください。

ループはフレームとして視覚化されます。 ループ内のフローは、オブジェクトごとに実行されます。 つまり、ループに複数のアクティビティを追加すると、各項目に対してフルフローが実行されます。 たとえば、注文が支払われていない場合に注文が処理されないようにするループを追加できます。

![](attachments/microflows-loop/loop.png)

ループには、開始イベントと終了イベントを除く、マイクロフローで使用されるすべてのタイプの要素を含めることができます。 さらに、ループのみが [break events](/refguide/break-event) と [continue events](/refguide/continue-event) を含めることができます。 break イベントはループ内で使用されるのは、オブジェクトのリストの反復を停止し、マイクロフロー内の残りのフローを継続するためだけです。 continue イベントは、現在の反復を停止し、次のオブジェクトの反復を開始するためにのみループで使用されます。

## 2 つのループプロパティ

Loop プロパティは **データ ソース** セクションで構成され、以下に説明します。

* **Loop Over** - ループするアイテムのリストである変数

*  **Loop Variable Name** - 現在作業中のリスト項目の名前を指します。

    {{% image_container width="350" %}}![ループのデータ ソースのプロパティ](attachments/microflows-loop/loop-properties.png)
    {{% /image_container %}}

## 3 ループの設定 {#loop-example}

簡単なユースケースは、データベースから注文リストを取得する場所です。 このリストをループし、結果として処理された注文をマークします。

![ループ例](attachments/microflows-loop/loop-example.png)

以下の前提条件があることを確認してください:

1. [ドメインモデルに](domain-models#adding-new-entities) エンティティを作成し、 *Order* という名前を付けます。
2. [このエンティティのブール型の属性](domain-models#adding-new-attributes) を作成して、この属性のステータスを示し、この属性に名前を付けます。 *処理済み*。
3. [マイクロフロー](microflows#create) を作成

ユースケースを開始するには、次の手順を実行します。

1. ループを追加するマイクロフローを開きます。

2. まず、ループオーバーする注文のリストを取得する必要があります。 次の操作を行います: <br />

    a **ツールバー**で **取得**を選択し、マイクロフローにドラッグ&ドロップします。 <br />

    B In **Properties** > the **Data Source** section, select **From Database**, and set *Order* as an entity for this activity. ( **Range** プロパティはデフォルトで **All** に設定されています): <br />

    {{% image_container width="350" %}}![オブジェクトのプロパティを取得](attachments/microflows-loop/retrieve-properties.png)
    {{% /image_container %}}

3. 作業できる注文のリストを取得したので、ループとロジックを作成する必要があります。 次の操作を行います: <br />

    a **Toolbox**で **Loop**を選択し、マイクロフローにドラッグ&ドロップします。 <br />

    ![ループが追加されました](attachments/microflows-loop/loop-added.png)<br />

    B **プロパティ**で、 **OrderList** を **Loop Over** に設定します(**Loop Variable Name** は自動的に設定されます)。 そのため、ループするオブジェクトのリストを選択していることになります。 <br />

    {{% image_container width="350" %}}![例のループプロパティ](attachments/microflows-loop/loop-properties-in-example.png)
     {{% /image_container %}}

4. これで、各注文のステータスを *処理済*に変更するアクティビティを追加できます。 つまり、ループ内で追加したアクティビティは、各オブジェクト(順序ごと)に対して実行されます。 次の操作を行います:<br />

    a **Toolbox**で **Change Object**を選択し、ループ内にドラッグ&ドロップします。<br />

    B In **Properties** > the **Data Source** section for the **Change Object** activity, set **Object** to **Order**.<br/>

    C **メンバーの変更** オプションが表示されたら、 **新しい値を追加** をクリックします。<br />

    ![ループの例でオブジェクトのプロパティを変更](attachments/microflows-loop/change-object-properties.png)

5. **値の変更** ダイアログで、次の操作を行います。<br />

    a **属性または関連付け** を **処理済み(ブール語)** に設定します。<br />

    B **式** タブで、 **true** と入力して、この属性の *新しい値* を設定します。 <br />

    ![値を変更するダイアログの例](attachments/microflows-loop/change-value-dialogue-example.png)

    C **追加** をクリックして変更を保存します。

このビデオは、上記の例を構成するプロセスを示しています。

<video width="768" height="432" controls src="attachments/microflows-loop/loop-example-video.mp4">ビデオ</video> 結果として、microflow に取得した注文のリストと、このリストを反復するループがあります。 ループ内のアクティビティでは、処理する各注文のステータスが設定されます。

## 4 続きを読む

* [マイクロフロー](マイクロフロー)
