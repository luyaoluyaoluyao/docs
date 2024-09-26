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

**テーマカスタマイズ** は、Mendix Studio でアプリをカスタマイズするのに役立つツールです。 たとえば、色を調整したり、ロゴをアップロードしたり、テキストスタイルを変更したりすることで、アプリの一貫性とユニーク性を高めることができます。

![デフォルトスタイルとカスタマイズスタイル](attachments/theme-customizer/default-vs-customized.png)

**テーマカスタマイザ**を開くには、左メニューバーのペイントブラシアイコンをクリックします。

![テーマカスタマイザアイコン](attachments/theme-customizer/theme-customizer-icon.png)

左側のテーマカスタマイザには、アプリのさまざまな要素をカスタマイズするための設定が含まれています。 変更内容は右側にプレビューされます。 2つのプレビューモードがあります:

* [ウィジェットビュー](#widget-view) – 個々のウィジェットのスタイルをプレビュー

*  [ページビュー](#page-view) – ページのスタイルをプレビューします

    {{% alert type="info" %}} **ページビュー** 機能はベータ版です。 つまり、この機能に変更がある可能性があります。 ベータ版の機能の詳細については、 [Mendix Beta Features](/releasenotes/beta-features/) を参照してください。
    {{% /alert %}}

上部バーのボタンをクリックすると、モードを切り替えることができます。

![プレビューモード](attachments/theme-customizer/preview-modes.png)

## 2の設定

**テーマカスタマイザ**の左側にある異なる設定を使用して、アプリの見た目を変更できます。 次のセクションに分かれています

### 2.1 ロゴをアップロード

**ロゴのアップロード** セクションでは、アプリのロゴとして使用する画像をアップロードできます。 拡張子png、jpg、jpeg、gif、svgで画像をアップロードできます。 ロゴのアップロード方法については、 [ロゴのアップロード](#uploading-logo) セクションを参照してください。

ロゴがアップロードされると、ロゴの色に基づいてカラーパレットが生成されます。 その後、異なる設定のカラーピッカーで **ロゴカラー** を選択し、アプリのスタイルをロゴのスタイルに合わせることができます:

{{% image_container width="250" %}}![ロゴ色](attachments/theme-customizer/logo-colors.png)
{{% /image_container %}}

設定で新しい色を選択する方法については、 [色の調整](#adjusting-colors) を参照してください。

### 2.2 ブランドカラー

In the **Brand Colors** section, you can define colors of different styles: **Default**, **Primary**, **Inverse**, **Info**, etc. これらのスタイルは、例えば **スタイル** プロパティを持つウィジェットに適用されます。 That means, if you selected a green color for the **Success** style, buttons that have *Success* selected in the **Style** property will be green:

![](attachments/theme-customizer/brand-colors-style-dependency.png)

### 2.3 UI のカスタマイズ

**UI カスタマイズ** セクションでは、メイン UI 要素のスタイルと色を調整できます。

### 2.4 タイポグラフィー（組版）

**タイポグラフィ** セクションでは、アプリのテキストスタイルとテキストカラーを上書きできます。 アプリ内の色や見出しのサイズやハイパーリンクなど:

{{% image_container width="250" %}}![ウィジェットビュー](attachments/theme-customizer/widget-view.png)
{{% /image_container %}}

## 3つのウィジェットビュー {#widget-view}

**ウィジェット ビュー** は、たとえば個々のウィジェットや UI 要素のスタイルをプレビューします。 例えば、 **組版**を変更すると、その変更は個々の見出しと段落に対してプレビューされます。

## 4ページ表示 {#page-view}

{{% alert type="info" %}} **ページビュー** 機能はベータ版です。 つまり、この機能に変更がある可能性があります。 ベータ版の機能の詳細については、 [Mendix Beta Features](/releasenotes/beta-features/) を参照してください。
{{% /alert %}}

**ページビュー**では、アプリから任意のページを選択して変更をプレビューできます。 トップバーのドロップダウンメニューからページを選択できます。 You can also switch the Device modes to see how your style looks on the **Phone**, **Tablet**, or **Responsive view**.

![トップ バー](attachments/theme-customizer/top-bar.png)

## 5 Basic アクションの実行

### 5.1 ロゴのアップロード {#uploading-logo}

ロゴをアップロードするには、次の操作を行います。

1. **テーマカスタマイザ**を開きます。

2.  **Upload Logo** セクションで、 **Select File** をクリックします。

    ![ロゴをアップロード中](attachments/theme-customizer/upload-logo.png)

3. ダイアログボックスで、ロゴとして使用する画像を選択します。

4.  選択した画像がアップロードされ、プレビューに表示されます。

5. **保存** をクリックして変更を保存します。

アプリのロゴが変更されました。

### 5.2 色の調整 {#adjusting-colors}

アプリケーションのさまざまな要素のデフォルトの色を上書きできます。 ドロップダウン ウィンドウでカラーピッカーを持つ要素の色を変更できます。

色を変更するには、次の操作を行います。

1. **Brand Colors**, **UI Customization** or **Typography** セクションで、変更したい設定を選択します。

2.  この設定をクリックし、次のいずれかを実行して色を選択します:

    1. パレットで色を選択します。
    2. 色のコードで塗りつぶす。
    3. Selecting the color from **Brand Colors** and **Logo Colors** (**Logo Colors** are only available when you [upload a logo](#uploading-logo)).<br/>
{{% image_container width="200" %}}![ブランドカラーとロゴカラー](attachments/theme-customizer/adjusting-color.png)
    {{% /image_container %}}

3. プレビューの結果を参照してください。

4. **保存** をクリックして変更を保存します。

アプリに色が適用されました。

## 6もっと読む

* [アトラスUI](/howto/front-end/atlas-ui)
