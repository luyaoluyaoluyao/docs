---
title: "テキスト"
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

テキストは、 [テキスト、段落、見出し(H1-H6)](page-editor-widgets) 、 [ページタイトル](#text-widget)で構成される [ウィジェット](#page-title-widget)のグループです。 これらはエンドユーザーにテキスト情報を表示するために使用されます。 たとえば、テキスト段落を表示できます。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-text/paragraph-example.png)
{{% /image_container %}}

## 2 テキスト、段落、見出し一般プロパティ {#text-widget}

You can use **Text**, **Paragraph**, or **Heading** widgets to display a text to the end-user. In **Properties** > **General**, you can type the text that will be displayed, define if it contains attribute values, and set the [render mode](#render-mode).

### 2.1 コンテンツ {#content}

**コンテンツ**では、エンドユーザーに表示されるテキストを定義します。 ここで動的データを表示することもできます: 属性値と式の結果。

属性を追加すると、ユーザに属性値が表示されます。 **追加** > **属性** を選択するか、 <kbd>Ctrl</kbd> + <kbd>スペース</kbd> を押して属性を選択します。  たとえば、ユーザーがアカウントにログインすると、グリーティングメッセージを表示できます。 where *Name* and *NumberOfMessages* is attribute value:

![](attachments/page-editor-widgets-text/content-example.png)

式を設定し、式の結果を表示することもできます (式の詳細については、 [式](expressions) を参照してください)。 式を書くには、 **追加** > **式結果** を選択してください。 たとえば、付加価値税(VAT)を除く価格を表示できます。

![コンテンツ例式](attachments/page-editor-widgets-text/content-example-expression.png)

**コンテンツ**を編集するには、ページのウィジェットをダブルクリックします。


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

## 4 条件付き表示セクション

{{% snippet file="studio/visibility-section-link.md" %}}

## 5デザインセクション {#input-elements-design}

**デザイン** セクションとそのプロパティについては、 [デザイン セクション](page-editor-widgets-design-section) を参照してください。

## 6もっと読む

* [ページ](page-editor)
* [ウィジェット](page-editor-widgets)
