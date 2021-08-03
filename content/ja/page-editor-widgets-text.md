---
title: "テキストウィジェット"
parent: "page-editor-widgets"
description: "Mendix Studioでタイポグラフィウィジェットを説明します。"
menu_order: 40
tags:
  - "スタジオ"
  - "ページエディタ"
  - "タイポグラフィー(文章)"
  - "テキストウィジェット"
  - "ウィジェット"
---

## 1つの紹介

Text is a group of [widgets](page-editor-widgets) that consists of **[Text, Paragraph, Headings (H1-H6)](#text-widget)**, and the [**Page Title**](#page-title-widget). これらはエンドユーザーにテキスト情報を表示するために使用されます。

## 2 テキスト、段落、見出し一般プロパティ {#text-widget}

You can use **Text**, **Paragraph**, or **Heading** widgets to display a text to the end-user. In **Properties** > **General**, you can type the text that will be displayed, define if it contains attribute values, and set the [render mode](#render-mode).

### 2.1 コンテンツ

**コンテンツ**では、表示されるテキストを定義します。 属性を追加することもでき、属性値がユーザーに表示されます。 たとえば、ユーザーがアカウントにログインすると、グリーティングメッセージを表示できます。 where *Name* and *NumberOfMessages* is attribute value:

![](attachments/page-editor-widgets-text/content-example.png)

#### 2.1.1 属性を追加しないコンテンツの設定

属性を追加せずに **コンテンツ** を設定するには、次のいずれかを実行できます。

* ページのウィジェットをダブルクリックし、エンドユーザーに表示したいテキストを入力し始めます。変更を保存するには、 <kbd>Enter</kbd> を押します。
* Open **Properties** of the widget, delete the default text in the **General** section > **Content**, and type the message you want to show to the end-user

#### 2.1.2 コンテンツの設定と属性の追加

**コンテンツ** を構成し、属性を追加するには、次の操作を行います:

1. Place the widget (**Text**, **Paragraph**, or **Heading**) inside a data container (a list view or a data view) and set an entity for the list view/data view. 詳細については、 [Data View & List View Properties](page-editor-data-view-list-view) を参照してください。 これは、選択した図形の属性をテキストに挿入できるようにするために必要です。

2.  Open **Properties** of the **Text**, **Paragraph**, or **Heading**, delete the default text in the **General** section > **Content** and start typing the message you want to show to the end-user.

    {{% image_container width="350" %}}![](attachments/page-editor-widgets-text/content.png)
    {{% /image_container %}}

3. メッセージに属性値を挿入するには、 **属性の追加** をクリックするか、 <kbd>Ctrl</kbd> + <kbd>スペース</kbd> を押します。  挿入できる属性のリストが表示されます。

4.  Scroll through the list of attributes (you can also use <kbd>Up</kbd> and <kbd>Down</kbd> arrows for that) and select the attribute you want to add to the **Text**.

    {{% image_container width="350" %}}![](attachments/page-editor-widgets-text/list-of-attributes.png)
    {{% /image_container %}}

5. 残りのテキストを入力し、必要に応じて属性を追加してメッセージを終了します。

ウィジェットの **コンテンツ** を設定しました。 編集する場合は、ページ内のウィジェットをダブルクリックします。 **テキストの編集** ポップアップダイアログが表示され、ウィジェットの内容に属性が表示されます。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-text/edit-text.png)
{{% /image_container %}}

### 2.2 レンダリングモード {#render-mode}

レンダリングモードでは、テキストをエンドユーザーに表示する方法を定義します。 Basically, **Text**, **Paragraph**, and **Heading** widgets are different render modes of the same widget. レンダリングモードの可能な値は以下の表に記載されています。

| 値     | 説明                                                |
| ----- | ------------------------------------------------- |
| テキスト  | テキストはページ上の前/次のウィジェットとともにインラインでレンダリングされます          |
| 段落    | テキストは別の段落としてレンダリングされます                            |
| H1-H6 | テキストは見出しとしてレンダリングされます。 H1は見出しの最大のタイプで、H6は最小のものです。 |

## 3 ページタイトル一般プロパティ {#page-title-widget}

ページタイトルウィジェットは現在のページのタイトルを設定し、表示します。 このタイトルは、ブラウザタブにページタイトルとしても表示されます。  タイトルは **テーマカスタマイザ** の **H1**スタイルで表示されます。 詳細は [テーマカスタマイズ](theme-customizer) を参照してください。

ページ名を変更する場合は、次の操作を行います。

1. Open **Properties** of the widget > the **General** section.
2. **タイトル** フィールドの名前を変更します。

ページタイトルが変更されました。

ページプロパティとウィジェットに表示される **タイトル** は同じです。 つまり、ページ プロパティのタイトルに変更を加えると、この変更はウィジェットに表示され、その逆も同様です。

![](attachments/page-editor-widgets-text/page-title-interrelation.png)



{{% alert type="info" %}}

**タイトル** ウィジェットを複数ページに配置できますが、それらはすべて同じテキストを表示し、個別に編集することはできません。

{{% /alert %}}

## 4デザインセクション {#input-elements-design}

**デザイン** セクションとそのプロパティについては、ウィジェットの [デザインセクション](page-editor-widgets-design-section) を参照してください。

## 5 続きを読む

* [ページ](page-editor)
* [ウィジェット](page-editor-widgets)
