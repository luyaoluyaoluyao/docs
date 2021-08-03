---
title: "アトラス2からアトラス3へ移行"
parent: "moving-from-8-to-9"
menu_order: 6
tags:
  - "Atlas"
  - "UI"
  - "UX"
  - "ユーザー経験"
  - "design"
---

## 1つの紹介

Atlas 3は、Mendixのスタイリングに新たな力と洗練をもたらします。 アトラス2からアトラス3へのアップグレードについては、以下の [アトラス2からアトラス3へのアップグレード](#upgrade) セクションをご覧ください。 Atlas 3がMendixにもたらす変更の高レベルのサマリーを表示するには、 [Atlas 3 Change Summary Reference Guide](/refguide/atlas3-change-summary) を参照してください。

アトラス2からアトラス3にアップグレードするには、以下の [アトラス2からアトラス3へのアップグレード](#upgrade) セクションを完了する必要があります。 **If you have not added custom styling into your Atlas**, completing these subsections of *Upgrading from Atlas 2 to Atlas 3* is all you need to do:

* [テーマディレクトリのアップグレード](#upgrade-theme-directory)
* [UIコンテンツの移行](#upgrade-ui-content)
* [Webスタイルの移行](#upgrade-web-styling)
* [ネイティブスタイルの移行](#upgrade-native-styling)
* [カスタム定義デザインプロパティの移行](#upgrade-design-properties)

アップグレード指示の後のセクションでは、既知の問題と、Atlas 3へのアップグレード時に発生する問題を参照しています。 **Atlasにカスタムスタイリングを導入した場合にのみ、ご相談ください**:

* [アトラス3へのアップグレード後の予想される問題](#expected-issues)
* [アトラス3にアップグレードした後のエッジケースの問題](#edge-cases)
* [一般的なアトラス問題のトラブルシューティング](#troubleshoot)

## 2 アトラス2からアトラス3へのアップグレード {#upgrade}

アップグレードする前に、Mendix 9でハイブリッドプロファイルが非推奨であるため、Atlas 3ではすべてのハイブリッドコンテンツが削除されていることに注意してください。 あなたのアプリがハイブリッドコンテンツを必要とする場合は、Atlasとは別に独自のハイブリッドコンテンツをすべて作成しない限り、Atlas 3にアップグレードしないことをお勧めします。

アップグレードプロセスを開始する前に。 Atlas 3で導入されたフォルダ構造の変更を調べるには、 [スタイルをカスタマイズする](/howto/front-end/customize-styling-new#file-and-folder) の *ファイルとフォルダ構造*セクションを参照してください。

### 2.1 テーマディレクトリのアップグレード {#upgrade-theme-directory}

テーマディレクトリをAtlas 3仕様にアップグレードするには、次のステップを完了してください:

1.  Atlas 2 **テーマ** ディレクトリの名前を変更します。 *theme_atlas2* に名前を付けることをお勧めします:

    ![アトラス2フォルダ](attachments/atlas-mig/atlas2-themefolder.png)

1.  Atlas 3 [**theme.zip**](https://www.dropbox.com/s/guffms4u5idx3us/theme.zip?dl=1) をダウンロードし、Mendix アプリフォルダのルートに展開します。 フォルダ構造は以下の例に似ています。 **Mendix app root**, then **theme**, then **web** and **native**:

    ![Atlas 3 folder](attachments/atlas-mig/atlas3-themefolder.png)

### 2.2 UI コンテンツの移行 {#upgrade-ui-content}

**Atlas 3** distributes the UI content previously found in the Atlas_UI_Resources, in 3 seperate modules: **Atlas Core**, **Atlas Web Content** and **Atlas Native Content**.

* [**Atlas Core**](https://marketplace.mendix.com/link/component/117187) - アトラスコアのスタイリングとレイアウトを含む
* [**Atlas Web Content**](https://marketplace.mendix.com/link/component/117183) - AtlasのウェブページテンプレートとBuilding Blockが含まれています
* [**Atlas Native Content**](https://marketplace.mendix.com/link/component/117175) - AtlasのネイティブページテンプレートとBuilding Blockを含む

#### 2.2.1 Atlas UI リソースをAtlas Core にアップグレードする

1. **アトラスUIリソース** で見つかったアトラスUIコンテンツを変更した場合、例: Building blocks, page templates or layouts, it is recommended to move the UI content you have modified to another user defined module within your app. **このステップ** をスキップしてください。
1.  Studio Proの **Atlas_UI_Resources** モジュールの名前を **Atlas_Core** に変更し、モジュールを右クリックして **名前の変更**をクリックします。

    ![](attachments/atlas-mig/2-rename.png)

1.  Download **[Atlas Core](https://marketplace.mendix.com/link/component/117187)** from the Marketplace and replace the existing ***Atlas_UI_Resources*** renamed to ***Atlas_Core***:

    ![](attachments/atlas-mig/3-import.png)

#### 2.2.2 アプリに Atlas の Web コンテンツを追加する

1.  マーケットプレイスから **[Atlas Web コンテンツ](https://marketplace.mendix.com/link/component/117183)** をダウンロード

    ![アトラスのウェブコンテンツ](attachments/atlas-mig/atlas-web-content-marketplace.png)

1.  **Atlas Web Content** は **マーケットプレイスモジュール** 内に新しいモジュールとして表示されます

    ![Atlas web content folder](attachments/atlas-mig/atlas-web-content-folder-structure.png)

#### 2.2.3 アプリにアトラスネイティブコンテンツを追加する

1.  Marketplaceから **[Atlas Native Content](https://marketplace.mendix.com/link/component/117175)** をダウンロード:

    ![アトラスのネイティブコンテンツ](attachments/atlas-mig/atlas-native-content-marketplace.png)

1.  **Atlas Native Content** は、 **Marketplace Modules** 内の新しいモジュールとして表示されます:

    ![アトラスネイティブコンテンツフォルダ](attachments/atlas-mig/atlas-native-content-folder.png)

### 2.3 ウェブスタイルの移行 {#upgrade-web-styling}

**Atlas 2 web theme** の修正には以下のものが含まれます:

* カスタム変数への変更
* 独自のスタイルを追加
* デザインプロパティの変更
* *Login.html* と *index.html* への変更

上記の変更を行った場合は、以下の手順に従ってください。 ステップは5つのセクションに分かれています:

* [Webカスタム変数](#web-custom-variables)
* [ウェブカスタムスタイル](#web-custom-styling)
* [ウェブ追加カスタムスタイル](#web-additional-custom-styling)
* [ウェブデザインのプロパティ](#web-design-properties)
* [Web リソース](#web-resources)

#### 2.3.1 ウェブカスタム変数 {#web-custom-variables}

このセクションでは、あなたが **Atlas 2 theme** の *custom-variables* **.scss** ファイルに加えた変更について説明します:

```
theme_atlas2/styles/web/ass/app/_custom-variables.scss
```

カスタム変数の変更を **Atlas 3**に移動するには、2つのオプションがあります:

**Option 1** — If the custom variables apply to the app level, then the modifications should be moved into the **custom-variables** SCSS file of the **Atlas 3 theme** directory:

```
theme/web/custom-variables.scss
```

**Option 2** — If you want to extract the variables into a reusable module, move them into the **custom-variables** SCSS file of a module you have created in the **themesource** directory:

```
themesource/your-module/web/custom-variables.scss
```

#### 2.3.2 ウェブカスタムスタイル {#web-custom-styling}

このセクションでは、 **Atlas 2 テーマ** の **カスタム** SCSS ファイルに対して行った変更について説明します。

```
theme_atlas2/styles/web/sass/app/_custom.scss
```

カスタムスタイルの変更を **Atlas 3**に移動するには、2つのオプションがあります:

**Option 1** — If the custom styling apply to the app level, then the modifications should be moved into the **main** SCSS file of the **Atlas 3 theme** directory:

```
theme/web/main.scss
```

**Option 2** — If you want to extract the custom styling into a reusable module, move them into the **main** SCSS file of a module you have created in the **themesource** directory:

```
themesource/your-module/web/main.scss
```

#### 2.3.3 ウェブ追加カスタムスタイル {#web-additional-custom-styling}

このセクションでは、 **Atlas 2 テーマの** アプリ **フォルダー** と、追加された可能性のある追加の SCSS スタイルシートに変更を加えました。

```
theme_atlas2/styles/web/ss/app/_
```

ここに追加した追加のスタイルシートを **Atlas 3**に移動するには、2つのオプションがあります:

**Option 1** — If the additional stylesheets apply to the app level, these changes should be moved into the **web** directory of the **Atlas 3 theme**:

```
theme/web/_
```

`@import <file name>` を ***theme/web/main.scss*** に含めることを忘れないでください。

**Option 2** — If you want to extract the additional stylesheets into a reusable module, move them to a module you have created in **themesource**:

```
themesource/your-module/web/_
```

`@import<file name>` を ***themesource/your-module/web/main.scss*** に含めることを忘れないでください。

#### 2.3.4 ウェブデザインプロパティ {#web-design-properties}

このセクションでは、 **Atlas 2 テーマ** の **settings.json ファイル** を変更したことについて説明します。

```
theme_atlas2/settings.json
```

Custom design properties that you have added to **settings.json** need to be moved into the web's **design-property** JSON file of a module you have created in the **themesource** directory:

```
themesource/your-module/web/design-properties.json*
```

モジュール **Atlas Core** または **Atlas Web Content** に追加しないでください。

プラットフォーム対応またはコミュニティ対応のウィジェットにユーザー定義のデザインプロパティがある場合は、以下の2つのシナリオに従ってください。

#### 2.3.5 ウェブリソース {#web-resources}

This section concerns modifications you have made to documents *login.html* and *index.html*, as well as additional static resources like font libraries, images, and more.

任意のカスタム *index.html* または *ログイン。 *アトラス2テーマ*で作成した*tml* ページを **アトラス2テーマ** の **ウェブ** ディレクトリに移動する必要があります。 **アトラス3テーマ**: </p>

```
theme/web/login.html
```

同じことは、あなたが作成したかもしれない追加の HTML ドキュメントにも適用されます。

画像やフォントライブラリなどの追加の静的リソースは、 **Atlas 3 テーマ** の **ウェブ** の **リソースディレクトリに移動する必要があります**:

```
テーマ/ウェブ/リソース
```

### 2.4 ネイティブのスタイルを移行 {#upgrade-native-styling}

**Atlas 2 テーマ** の **ネイティブ** セクションに変更を加えていない場合、このセクションはスキップできます。 **UI コンテンツの移行** {#upgrade-ui-content} のセクションに進むことができます。

**Atlas 2 テーマの変更** には以下のようなものがあります:

* カスタム変数への変更
* 追加のカスタムスタイルの追加
* デザインプロパティの変更

上記の変更を行った場合は、以下の手順に従ってください。 ステップは4つのセクションに分かれています:

* [ネイティブカスタム変数](#native-custom-variables)
* [ネイティブカスタムスタイル](#native-custom-styling)
* [ネイティブ追加カスタムスタイル](#native-additional-custom-styling)
* [ネイティブデザインのプロパティ](#native-design-properties)

#### 2.4.1 ネイティブカスタム変数 {#native-custom-variables}

このセクションでは、 **Atlas 2 theme** の **custom-variables** js ファイルに対して行った変更について説明します。

```
theme_atlas2/styles/native/sass/app/custom-variables.js
```

カスタム変数の変更を **Atlas 3**に移動するには、2つのオプションがあります:

**Option 1** - If the custom variables apply to the app level, then the modifications should be moved into the **custom-variables** scss file of the **Atlas 3 theme** directory.

```
theme/native/custom-variables.js
```

**Option 2** - If you want to extract the variables into a reusable module, move them into the **custom-variables** scss file of a module you have created in the **themesource** directory.

```
themesource/your-module/native/custom-variables.js
```

#### 2.4.2 ネイティブカスタムスタイル {#native-custom-styling}

このセクションでは、 **Atlas 2 theme** の **カスタム** js ファイルに対して行った変更について説明します。

```
theme_atlas2/styles/native/sass/app/_custom.js
```

カスタムスタイルの変更を **Atlas 3**に移動するには、2つのオプションがあります:

**Option 1** - If the custom styling apply to the app level, then the modifications should be moved into the **main** js file of the **Atlas 3 theme** directory.

```
theme/native/main.js
```

**Option 2** - If you want to extract the custom styling into a reusable module, move them into the **main** js file of a module you have created in the **themesource** directory.

```
themesource/your-module/native/main.js
```

#### 2.4.3 ネイティブ追加のカスタムスタイル {#native-additional-custom-styling}

このセクションでは、 **Atlas 2 theme** の **app** フォルダーと、追加された可能性のある追加の js スタイルシートに行った変更について説明します。

```
theme_atlas2/styles/native/sass/app/_
```

ここに追加した追加のスタイルシートを **Atlas 3**に移動するには、2つのオプションがあります:

**Option 1** - If the additional stylesheets apply to the app level, these changes should be moved into the **web** directory of the **Atlas 3 theme**.

```
theme/native/_
```

JavaScript の `import` 構文を *theme/native/main.js* でインポートし、インポートされたファイルによって公開される変数をエクスポートすることを忘れないでください。

**Option 2** - If you want to extract the additional stylesheets into a reusable module, move them to a module you have created in **themesource**.

```
themesource/your-module/native/_
```

JavaScript の `インポート` 構文を *themesource/your-module/native/main.js* でインポートし、インポートされたファイルで公開される変数をエクスポートしてください。

#### 2.4.4 ネイティブデザインプロパティ {#native-design-properties}

このセクションでは、 **Atlas 2 theme** の **settings-native.json ファイル** に対して行った変更について説明します。

```
theme_atlas2/settings-native.json
```

Custom **design properties** that you have added to **settings-native.json**, need to be moved into the native's **design-property** json file of a module you have created in the **themesource** directory.

```
themesource/your-module/web/design-properties.json*
```

モジュール **Atlas Core** または **Atlas Native Content** に追加しないでください。

プラットフォームサポートまたはコミュニティサポートのウィジェットにカスタム定義されたデザインプロパティがある場合は、以下の [カスタム定義デザインプロパティの移行](#upgrade-design-properties) セクションを参照してください。

### 2.5 カスタム定義デザインプロパティの移行 {#upgrade-design-properties}

#### 2.5.1 プラットフォームでサポートされているウィジェットのデザインプロパティの追加

次の例と同様に、独自のデザインプロパティを使用して、1つ以上のプラットフォームがサポートするウィジェットを拡張している場合。

**コンテナ ウィジェット** を design プロパティ **border** で拡張して、コンテナーのインスタンスにボーダーを追加していること。 デザインのプロパティでは、 `要素` の名前は `DivContainer` と呼ばれます。

```
{
 "pageTemplates": "WebModeler",
 "cssFiles": ["styles/web/css/main.css"],
 "designProperties": {
  "DivContainer": [
    {
        "name": "Align content",
        "type": "Dropdown",
        "description": "Align content of this element left, right or center it. Align elements                  inside the container as a row or as a column.",
        "options": [
                {
                    "name": "Left align as a row",
                    "oldNames": ["Left align as row"],
                    "class": "row-left"
                },
                {
                    "name": "Center align as a row",
                    "oldNames": ["Center align as row"],
                    "class": "row-center"
                },
                {
                    "name": "Right align as a row",
                    "oldNames": ["Right align as row"],
                    "class": "row-right"
                }
        ]
   },
   {
    "name": "Border", // custom design property targeting the platform's DivContainer
    "type": "Toggle",
    "description": "Add a border.",
    "class": "div-container-border"
   }
  ]
 }
}
```

上の例では、2つのデザインプロパティがあります: **コンテンツの配置** と **枠線**。 コンテンツの配置は Atlas 3 で定義されたデザインプロパティで、境界はカスタム定義されたデザインプロパティです。 Atlas 3 定義された設計プロパティとの競合を避けるために。 **themessource** ディレクトリで作成したモジュールの **design-property** json ファイルに、カスタム定義されたデザインプロパティのみをエクスポートすることをお勧めします。 以下の例と似たような結果が得られます。

```
{
 "DivContainer": [
  {
   "name": "Border",
   "type": "Toggle",
   "description": "Add a border.",
   "class": "div-container-border"
  }
 ]
}
```

#### 2.5.2 コミュニティ対応ウィジェットのデザインプロパティの追加

次の例と同様に、アプリでコミュニティサポートされているウィジェットに独自のデザインプロパティを定義している場合は、以下の手順に従ってください。

MyCustomWidgetのデザインプロパティ `"Opacity"` を **Atlas 2** に追加しました。 以下のように **settings.json** ファイルに表示されます。

```
{
 "pageTemplates": "WebModeler",
 "cssFiles": ["styles/web/css/main.css"],
 "designProperties": {
  "MyCustomWidget": [
   {
    "name": "Opacity",
    "type": "Dropdown",
    "description": "Emphasize the visual-importance via opacity.",
    "options": [
     {
      "name": "Light",
      "class": "opacity-light"
     },
     {
      "name": "Normal",
      "class": "opacity-normal"
     }
    ]
   }
  ]
 }
}
```

As this is a custom-defined design property, this needs to be added to the web's **design-property** json file of a module you have created in the **themesource** directory. 以下の例と似たような結果が得られます。

```
{
 "MyCustomWidget": [
  {
   "name": "Opacity",
   "type": "Dropdown",
   "description": "Emphasize the visual-importance via opacity.",
   "options": [
    {
     "name": "Light",
     "class": "opacity-light"
    },
    {
     "name": "Normal",
     "class": "opacity-normal"
    }
   ]
  }
 ]
}
```

#### 2.5.3 デザインプロパティのマージオプション

デザインプロパティオプションは、テーマソースモジュール間でマージすることもできます。 詳細については、 [デザインプロパティ API ドキュメント](/apidocs-mxsdk/apidocs/design-properties#extend-existing-design-properties) の **他のモジュールのデザインプロパティの拡張またはオーバーライド** セクションを参照してください。

## アトラス3にアップグレードすると予想される3つの問題 {#expected-issues}

上記のセクションを完了すると、エラーリストにエラーが発生する可能性があります。

*  名前の変更されたデザインプロパティに関連するエラーについては、関連するエラーを右クリックし、 **プロジェクト内のすべての名前の変更されたデザインプロパティを更新** をクリックします。

    ![エラー](attachments/atlas-mig/4-errors.png)

* For errors about the **Phone** or **Tablet** navigation profile no longer existing, right-click the error and select **Go to** which will navigate you to the widget that points to a missing Phone or Tablet profile — use one of these methods to solve the error:
    * レイアウトを削除
    * レイアウトのウィジェットを削除
    * **Phone web** または **Tablet web** ナビゲーションプロファイルを Mendix アプリケーションに追加します
    * ウィジェットのプロパティ ペインで、 **プロファイル** を既に存在するプロファイルに変更します。たとえば、 **レスポンシブウェブ**

    Mendix 9でナビゲーションプロファイルが変更されたことに注意してください。 詳細は [Mendix 9 Release Notes](/releasenotes/studio-pro/9.0) を参照してください。

    ![](attachments/atlas-mig/5-nav.png)

*  ハイブリッド電話プロファイルを使用している場合。 ナビゲーションプロファイルの **プロフィールの種類を変更** をクリックして、同等のWebプロファイルに変更してください:
    * ハイブリッドタブレットアプリをオフライン → タブレットウェブをオフライン
    * ハイブリッドタブレットアプリ オンライン → タブレットウェブ
    * ハイブリッド電話アプリをオフライン → 電話ウェブをオフライン
    * ハイブリッド電話アプリをオンライン → 携帯電話のウェブ

    ![](attachments/atlas-mig/6-hybrid-phone.png)

*  バッジ、プログレスバー、進捗バー、地図ウィジェットを使用している場合 各ウィジェットに追加された新しいプロパティに従って、ウィジェットの定義を更新し、再設定してください:

    ![](attachments/atlas-mig/7-errors.png)

*  If you have **Design property X is not supported by your theme** errors, it either means a design property has been removed in Atlas 3 or you need to add your own design properties to the new file structure as instructed in the [migrating custom defined design properties](#upgrade-design-properties) section above. エラーを抑制するには、エラーを右クリックし、 **プロパティを削除** を選択します。 デザインプロパティを拡張する方法を確認するには、 [デザインプロパティを拡張する方法](/howto/front-end/extend-design-properties) に従ってください。

    ![](attachments/atlas-mig/8-errors-background.png)

* **Unknown option X for design property**というエラーがある場合 これは、Atlas 3でdesign property オプションが削除されたことを意味します。 次のいずれかの方法を使用して、エラーを解決します。
    * design プロパティをデフォルトのオプションに設定します: エラーを右クリックし、 **Set property X to default**
    * Search for the design property option's CSS class in *theme_atlas2/settings.json* for web and *theme_atlas2/settings-native.json* for native, then add it to the applicable [widget's style property](common-widget-properties#style)

    ![](attachments/atlas-mig/9-set-prop.png)

* **Nanoflow commons/Native モバイル・リソースが互換性がない場合、** **Marketplace** から新しいメジャーバージョンを取得します。

## アトラス3にアップグレードした後の4つのエッジケースの問題 {#edge-cases}

Mendix 9ではハイブリッドプロファイルは非推奨です。 アトラス3では、すべてのハイブリッドコンテンツが削除されます。 アトラス2からアトラス3にアップグレードするとき ハイブリッドプロファイルのデフォルトのホームページとして使用されているページに関するエラーが発生する可能性があります。

![](attachments/atlas-mig/10-edge.png)

これを修正するには、エラーを右クリックし、 **を選択します。ナビゲーションプロファイル ‘HybridPhone’** に移動し、デフォルトのホームページを変更します。

![](attachments/atlas-mig/set-hybrid-nav.png)

## 5 一般的なアトラスの問題のトラブルシューティング {#troubleshoot}

一般的なアトラスの問題をトラブルシューティングするには、次の手順を実行します。

* **レイアウト X が存在しない** エラーがある場合は、エラーを右クリックし、エラーが発生するページに移動します。 ページのプロパティで、新しい適切なレイアウトを選択します。
* **選択したイメージ X が存在しない** エラーがあります。 エラーを右クリックして、発生するページに移動し、新しい画像を選択します。 アプリによっては、 **Atlas_NativeMobile_Content** モジュールをダウンロードし、モジュールから画像を使用することもできます。
* **選択したプレースホルダー X が存在しない場合** エラーが発生しました。 エラーを右クリックし、発生したページに移動し、その後、エラーを修正するための代替オプションがあります。
    * ページに一致する名前を持つプレースホルダを含めるために使用するレイアウトを調整します。
    * ページで、コンテンツをプレースホルダから移動します。

## 6もっと読む

* [Atlas 3 ウェブサイト](https://www.mendix.com/atlas/)
* [アトラス設計システムアプリ](https://atlasdesignsystem.mendixcloud.com/)
* [Atlas 3 変更概要](/refguide/atlas3-change-summary)
* [Studio Pro 9 リリースノート](/releasenotes/studio-pro/9.0)
