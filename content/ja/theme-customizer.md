---
title: "テーマのカスタマイズ"
description: "Mendix Studioでテーマカスタマイザについて説明します。"
menu_order: 80
tags:
  - "スタジオ"
  - "テーマのカスタマイズ"
  - "アトラスui"
---

## 1つの紹介

**テーマカスタマイズ** は、Mendix Studio でアプリをカスタマイズするのに役立つツールです。 たとえば、色を調整したり、ロゴをアップロードしたり、テキストのスタイルを変更したりすることができます。

![デフォルトスタイルとカスタマイズスタイル](attachments/theme-customizer/default-vs-customized.png)

**テーマカスタマイズ**を開くには、左側のメニューバーにあるペイントブラシアイコンをクリックします。

![テーマカスタマイザアイコン](attachments/theme-customizer/theme-customizer-icon.png)

**テーマカスタマイズ** は 2 つのペインに分かれています:

* [設定](#theme-customizer-settings)
* [プレビュー](#theme-customizer-preview)

**テーマカスタマイズ** の下部には、次の機能を持つ2つのボタンがあります。

* **Reset Style** - 変更をリセットするためにクリックし、 **Theme Customizer** を開いたときにそこにあった値を復元します (ただし、 **Apply Style** をクリックすると変更をリセットすることはできません)
* **スタイルの適用** – 変更を保存するにはクリックします

## 2 設定ペイン {#theme-customizer-settings}

**設定** でアプリの見た目を変更できます。 **設定** ペインを使用して変更することができる変更は以下の表に記載されています。

| セクション        | 説明                                                                                                                                                                                                                                                                                           |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ロゴをアップロード    | アプリでロゴとして使用する画像をアップロードできます。 拡張子png、jpg、jpeg、gif、svgで画像をアップロードできます。 <br />ロゴがアップロードされると、ボタンなどの要素の色を調整するためのドロップダウンウィンドウにその色が表示されます。 <br />テーマカスタマイザ **のテキスト、上部、サイドバー**。 したがって、 **Logo Colors** から色を選択して、アプリをロゴと同じスタイルにすることができます。 詳細については、 [**色の調整**](#adjusting-colors) を参照してください。 |
| ブランドカラー      | このセクションでは、アプリのメインカラーを選択できます(主にボタンに使用されます)。                                                                                                                                                                                                                                                   |
| UI のカスタマイズ   | このセクションでは、メイン UI 要素のスタイルと色を調整できます。 <ul><li>Topbar</li><li>Sidebar</li><li>背景</li></ul>                                                                                                                                                                                                                                  |
| タイポグラフィー（文法） | このセクションを使用すると、アプリのテキストスタイルとテキストの色を上書きできます。                                                                                                                                                                                                                                                   |

## 3 プレビューペイン {#theme-customizer-preview}

**プレビュー** では、アプリでの変更内容の印象を得ることができます。

## 4 テーマカスタマイザでの基本機能の実行

### 4.1 ロゴのアップロード {#uploading-logo}

ロゴをアップロードするには、次の操作を行います。

1. **テーマカスタマイザ**を開きます。
2.  **Upload Logo** セクションで、 **Select File** をクリックします。

    ![ロゴをアップロード中](attachments/theme-customizer/upload-logo.png)

3. ダイアログウィンドウで、ロゴとして使用する画像を選択します。
4.  選択した画像がアップロードされ、 **プレビュー** に表示されます。

    ![ロゴをプレビューする](attachments/theme-customizer/logo-preview.png)

5. **Apply Style** をクリックして変更を保存します。

### 4.2 色の調整 {#adjusting-colors}

アプリケーションのさまざまな要素のデフォルトの色を上書きできます。 ドロップダウンウィンドウでカラーパレットを持つ要素の色を変更できます。

色を変更するには、次の操作を行います。

1. **Brand Colors**, **UI Customization** or **Typography** セクションで、変更したい要素を選択します。
2.  Click this element and select color by clicking on the palette, filling out the code of the color, or selecting the color from **Brand Colors** and **Logo Colors** (only available when you upload a logo, for more information, see [Uploading a Logo](#uploading-logo)).

    ![ブランドカラーとロゴカラー](attachments/theme-customizer/adjusting-color.png)

3. **プレビュー** で結果を確認します。
4. **Apply Style** をクリックして変更を保存します。

## 5 続きを読む

* [アトラスUI](/howto/front-end/atlas-ui)
