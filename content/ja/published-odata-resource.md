---
title: "公開されたOData リソース"
parent: "published-odata-services"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-odata-resource.pdf) をクリックしてください。
{{% /alert %}}

{{% alert type="warning" %}}

このドキュメントでは、公開された OData リソースのプロパティについて説明します。 OData サービスの概要については、 [Publiced OData Services](published-odata-services) を参照してください。

{{% /alert %}}

## 1 リソースの追加または編集

### 1.1 リソースを追加

**公開済みOData Service** ウィンドウの **リソース** ペインの **** をクリックして、 **エンティティを選択** ウィンドウを開きます。 公開するエンティティを選択し、 **Select** をクリックします。

![OData サービスページ](attachments/published-odata-resource/published-odata-service.png)

リソースを追加する別の方法は、 **Domain Model**にあります: エンティティを右クリックし、 **Expose as OData resource** を選択します。

![ドメインモデルのドロップダウンメニュー](attachments/published-odata-resource/create-odata-resource-from-domain-model.png)

リソースを追加するには、 **公開データサービスを選択** ウィンドウでODataサービス名をクリックし、 **選択**をクリックします。

新しいODataサービスを作成し、それにエンティティを追加するには **New**  をクリックし、 **Add Published OData Service** ダイアログボックスに作成するサービスの名前を入力します。

### 1.2 リソースを編集

In the **Resources** pane of the **Published OData Service** window, select a resource and click **Edit** to display the **Edit published resource** window.

![公開済みの OData ダイアログボックスを編集](attachments/published-odata-resource/published-resource-dialog-box.png)

別の **エンティティ** を選択するか、 ****をクリックしてドメインモデル内のエンティティを表示することができます。 選択した図形の [属性と関連性](#exatass) をこのウィンドウで設定できます。

リソースが公開される場所を **場所の例** で指定します。

**公開ドキュメント** タブでは、公開されたエンティティの概要と説明を提供できます。

{{% alert type="info" %}}

[IBM DB2](db2) は、マルチユーザー環境でノンブロッキングの読み取り絶縁データ検索操作をサポートしていません。 したがって、ODataによって取得されたデータは、同じデータ行が他のユーザーによって同時に変更された場合、100%一致しない可能性があります。

{{% /alert %}}

## 露出された属性と関連付けの選択 {#exatass}

In the **Edit published resource** window, select **Exposed attributes and associations** to display the list of attributes and associations for the entity.

{{% alert type="info" %}}

**System.ID** 属性は、OData サービスのキーとして使用され、常にチェックする必要があります。

{{% /alert %}}

公開されたエンティティの属性は、デフォルトで **Nillable** です。 つまり、値が空の場合、OData コンテンツ内の明示的な null としてエンコードされます。 **Nillable** が属性のチェックを外した場合、属性は空にできません(これはランタイムエラーになります)。

{{% alert type="info" %}}

Attributes of the type **Binary** cannot be exported through OData services except for the **Contents** field of the **System.FileDocument** attribute.

{{% /alert %}}

## 内部名から公開名へのマッピング3

**公開されたリソースの編集** ウィンドウで **公開されたエンティティ名** を使用して、外部に公開されたリソースの名前をカスタマイズします。 デフォルトは、ドメインモデルで公開されているエンティティの名前です。 **Exposed entity name** は文字で始まり、続く文字または数字が480文字以内でなければなりません。

{{% alert type="info" %}}

位置情報URIは一意でなければなりません。 同じ場所に2つの異なるリソースを公開すると、一貫性エラーになります。

{{% /alert %}}

属性と関連付けは、 **公開された属性と関連** リストウィンドウの **公開された名前** 列で同じ方法でカスタマイズできます。

関連付けの場合、公開されている名前は navigation プロパティ(関連するオブジェクトを参照するプロパティ)に与えられる名前です。 デフォルトは、ドメインモデルの関連付け名と同じです。

{{% alert type="info" %}}

この方法で名前がカスタマイズされている場合、エンティティの名前、属性、。 ドメインモデルで定義された関連付けは外部には公開されません すべての OData 通信では、公開された名前が使用されます。

{{% /alert %}}

これらの機能により、外部 API に影響を与えることなくドメインモデルをリファクタリングしやすくなります。

## 公開セット4名

**公開リソースの編集** ウィンドウの **公開セット名** フィールドに表示されるエンティティセットの名前をカスタマイズすることができます。 これは、 **場所の例** で指定されているリソースの URL の最後の部分を形成します。

デフォルト: *{Entity name}s*

## 5ページングを使用

**ページングの使用** オプションは、レスポンスあたりの最大オブジェクト数を設定し、次のオブジェクトセットへのリンクを含めるために使用されます。 [Tableau](https://www.tableau.com) のようなクライアントは、これを使用して進行状況を表示し、すべてのデータが取得されるまで自動的にリンクに従います。 ページングが適切なページサイズに設定されている場合、クライアントのメモリ使用量を改善することができます。

デフォルト: *いいえ*

設定 **ページング** を **はい** に使用すると、取得したデータが単一のトランザクションで取得されないため、データに矛盾が生じる可能性があります。 一例として **顧客** と呼ばれるエンティティの **年齢** 属性をソートし、顧客を取得するためにページあたり1000個のオブジェクトに設定されています。 2つの通話の間に顧客が削除された場合、1001のポジションにある **年齢** 23の顧客は1000に移動します。 これは、2 ページ目の最初のアイテムになるオブジェクトが最初のページに移動され、もはや取得されないことを意味します。 同様に、コール間に挿入されたデータは、データの重複を引き起こす可能性があります。 このオプションは、この種の矛盾が許容される場合にのみ使用する必要があります。

## 6 ページサイズ

When **Use paging** is set to **Yes**, the number of objects per page can be set in **Page size**.

デフォルト: *10000*
