---
title: "自己参照についてのクエリ"
parent: "関連"
menu_order: 20
tags:
  - "クエリ"
  - "自己参照"
  - "関連"
  - "ドメインモデル"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/query-over.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

場合によっては、データの型と構造により柔軟性を高めるために、より一般的なドメインモデルを作成したい場合があります。 この場合、継承または自己参照を使用して、シンプルでありながら効率的に設計されたモデルを可能にすることがよくあります。 これにより、マイクロフローとアプリケーションロジックの構築がはるかに簡単になります。 しかし、正しいオブジェクトをクエリすることは難しくなります:特に自己参照を使用している場合。

## 2例

この例は、1つのフォルダに複数のサブフォルダを含めることができるコンピュータ上のフォルダの実装です。

![](attachments/associations/query-over-example-structure.png)

これを実装するには、 **フォルダ** への自己参照が使用されます。 自己参照は **Folder_SubFolder** と呼ばれる関連です。 これにより、無制限の数とレベルのフォルダ構造を構築できます。

{{% alert type="info" %}}
この場合の協会は一対一の協会ですが、同じ技術が多対多または一対一の協会に適用されます。
{{% /alert %}}

![](attachments/associations/self-reference-domain-model.png)

If we create our folder functionality in a module called **QueryOver**, the association **Folder_SubFolder** is described in two ways in the domain model:

| 名前               | タイプ | 所有者   | 親             | 子要素           |
| ---------------- | --- | ----- | ------------- | ------------- |
| Folder_Subfolder | 参照  | デフォルト | クエリオーバーの倍率を変更 | クエリオーバーの倍率を変更 |

* 乗算: 1 つの 'フォルダ' オブジェクトは、複数の 'フォルダ' オブジェクトに関連付けられています

**Child** は 関連付けの **オーナー** です。言い換えれば、関連付けは子プロセスを通じて常に更新されます。

![](attachments/associations/query-over-association.png)

上記の例には6つのフォルダがあり、データベースは構造化されており、以下に示すように属性が入力されています。 **Folder_SubFolder** テーブルでは、 **ChildFolderID** が関連付けの所有者であるため、左側に表示されます。

![](attachments/associations/query-over-example-database.png)

ドメインモデルがデータベースにどのように実装されるかについての詳細は、 [Domain Model](domain-model#implementation) の *実装* セクションを参照してください。

### 2.1 サブフォルダ(子)をフォルダ(親)から取得する

microflow で $ChosenFolder オブジェクトを使用している場合は、サブフォルダを簡単に取得できます。 各協会には右側(協会内の親)と左側(協会内の子または所有者)があります。  プラットフォームは各関連付けを読み込み、親が $ChosenFolder と等しいかどうかを決定します。

これは以下の XPath 制約を使用して実装されます: `[QueryOver.Forder_SubFolder=$ChosenFolder]`. XPath 制約は右から左へ読み込まれ、結果のフォルダが結果となります。 これは、あなたがどの方向に関連付けられているかを解釈するための鍵です。

{{% image_container width="400" %}}
![](attachments/associations/query-over-retrieve-normal.png)
{{% /image_container %}}

If the $ChosenFolder object has **Code** `202002141322015` and **Name** `SubFolder2` we have chosen the folder with **ID** `3`. オレンジ色で強調表示されている左側のテーブルの2つのフォルダが返されます。 プラットフォームは、関連するChildFolder(s)を返すため、デフォルトでは制約を関連付けることができます。

![](attachments/associations/query-over-retrieve-normal-tables.png)

### 2.2 フォルダから親フォルダを取得

使用可能な $ChosenFolder オブジェクトを持っていて、ParentFolder を取得したい場合 (階層内の次の上のフォルダー) 例えば、format@@0 **SubFolder2** データベースから **MainFolder**を取得すると、より複雑になります。

[reversed ()] `[reversed ()]` を使用して、Mendix が通常使用する逆方向の制約を読み取るように指示します。

{{% alert type="info" %}}
`[reversed()]` は 1 つの関連付けにのみ適用されます。 複数の関連付けがある場合、彼らは通常の方法で解釈され続けます。 下記の [より複雑なクエリの作成](#more-complex)を参照してください。

`[reversed()]` 式は自己参照にのみ適用できます。 2 つの異なるオブジェクトタイプ間の関連付けがある場合、プラットフォームは自動的に結合の方向を決定することができます。
{{% /alert %}}

 例では、 $ChosenFolder の親フォルダを探します。 クエリは `[QueryOver.Forder_SubFolder [reversed ()]=$ChosenFolder]` になります。 関連付けを右から左へ(親から子へ)読むのではなく、関連付けは左から右へ読み取られます。

{{% image_container width="400" %}}
![](attachments/associations/query-over-retrieve-reversed.png)
{{% /image_container %}}

If the $ChosenFolder object has **Code** `202002141322015` and **Name** `SubFolder2` we have chosen the folder with **ID** `3`. オレンジ色でハイライトされた右側のテーブルのフォルダが返されます。 プラットフォームは、制約を逆方向に適用し、関連するParentFolderを返します。

![](attachments/associations/query-over-retrieve-reversed-tables.png)

### 2.3 より複雑なクエリの作成 {#more-complex}

前の例は単純な例でした。 しかし、 `[reversed()]` 式はより複雑なクエリで使用できます。

たとえば、各フォルダが複数のファイルを含めることができるとします。関連付け **File_Folder** 上のフォルダに関連付けられています。

![](attachments/associations/query-over-extended-domain-model.png)

フォルダオブジェクト $ChosenFolder の親フォルダ内のすべてのファイルを取得します。

Use the constraint `[QueryOver.File_Folder/QueryOver.Folder/QueryOver.Folder_SubFolder [reversed ()]=$ChosenFolder]` to return all the **File** objects associated with the **Folder** which is associated (as parent) with the **Folder** which is the same as **$ChosenFolder**.

![](attachments/associations/query-over-retrieve-complex.png)

If the $ChosenFolder object is `SubFolder2`, you will retrieve all the **File** objects associated with `MainFolder` over the association **File_Folder**.

## 専門分野に関連する3つの関連

自己参照の特殊なケースでは、1対多の関連付けがそれ自体の専門化である場合、アソシエーション [によって](retrieve#source)を取得することはできません。

ここに継承例があります。

![](attachments/associations/limitation.png)

この例では、 **Specializations** のリストは、入力が専門分野である場合、マイクロフロー内の標準的なバイアソシエーション取得を使用している場合には取得できません。

ただし、この制限に対する回避策があります。Java API を使用する Java アクションで専門性のリストを取得できます。 このJavaアクションには、次の2つのパラメータが必要です: **専門化** と **リバース** このコードスニペットを介して:

```
public class RetrieveAsAssociatedWithB extends CustomJavaAction<java.util.List<IMendixObject>>
{
    private IMendixObject __B;
    private main.proxies.Specialization B;
    private java.lang.Boolean Reverse;

    public RetrieveAsAssociatedWithB(IContext context, IMendixObject B, java.lang.Boolean Reverse)
    {
        super(context);
        this.__B = B;
        this.Reverse = Reverse;
    }

    @java.lang.Override
    public java.util.List<IMendixObject> executeAction() throws Exception
    {
        this.B = __B == null ? null : main.proxies.Specialization.initialize(getContext(), __B);

        // BEGIN USER CODE
        return Core.retrieveByPath(getContext(), __B, "Main.Generalization_Specialization", Reverse);
        // END USER CODE
    }
}
```

{{% alert type="info" %}}
必ず `com.mendix.core.Core` をインポートして、このコードスニペットで `Core.retrievByPath(..)` を実行できるようにしてください。
{{% /alert %}}

`Reverse` Boolean を true に設定し、 `Specialization` オブジェクトを入力として使用する場合。 返されたリストには専門化に関連するすべての一般化が含まれています。
