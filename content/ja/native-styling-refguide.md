---
title: "ネイティブ モバイル スタイル"
parent: "native-Mobile"
menu_order: 20
description: "このリファレンスガイドでは、ネイティブモバイルアプリでMendixが使用するスタイル要素をコンテキスト化します。 Mendixのウィジェットのクラスとスタイルプロパティについて説明します。"
tags:
  - "ネイティブ"
  - "クラス"
  - "デザイン"
  - "属性"
  - "スタイル"
  - "ウィジェット"
  - "studio pro"
---

## 1つの紹介

このリファレンスガイドでは、ネイティブモバイルアプリでMendixが使用するスタイル要素をコンテキスト化します。 Mendixのウィジェットのクラスとスタイルプロパティについて説明します。 ネイティブスタイリングの基本を学ぶには [Native Mobile Styling](/howto/mobile/native-styling) の実装方法と、 [Mendix Native Mobile App のスタイル設定方法](/howto/mobile/how-to-use-native-styling) を参照してください。

Mendix アプリは、ページがどのように見えるかを決定するためにレイアウトを使用します。 ネイティブモバイルアプリの場合は、ネイティブレイアウトを使用してナビゲーションや設定をネイティブ機能に最適化したものに簡単に統合できます。 レイアウトの詳細については、 [レイアウト](layout) を参照してください。

ウィジェットの応答を維持するために、Mendix アプリは Flexbox を使用します。 Flexbox を使用すると、コンポーネントはその子コンポーネントのレイアウトを設定できます。 これにより、アプリは複数のフォーム要素にわたって一貫したレイアウトを維持できます。 レイアウトの詳細については、React Nativeの [Flexbox documentation](https://reactnative.dev/docs/flexbox) を参照してください。

`高さ` と `幅` プロパティを使用して、ウィジェットコンポーネントの寸法を設定できます。 サイズの詳細については、React Nativeの [Height and Width documentation](https://reactnative.dev/docs/height-and-width) を参照してください。

## 2 つのスタイルオブジェクト {#style-objects}

ウィジェットは様々な要素で構成されており、それぞれのスタイルを個別に設定できます。 スタイルオブジェクトを使用してウィジェットをカスタマイズできます。 style オブジェクトは、各ウィジェットに固有の属性のセットを持つ JavaScript オブジェクトです。 いくつかの属性は、React NativeのViewStyle、TextStyle、ImageStyle、Colors要素など、他の要素のプロパティを再利用します。 アプリをカスタマイズする際に、スタイリングの詳細については、次のプロパティセットを参照してください。

* **ViewStyle** – React Nativeの [View Style](https://reactnative.dev/docs/view-style-props) プロパティセットは、境界、不透明度を変更するのに役立ちます。 とアプリのその他の一般的な側面（ビュースタイルプロパティセットには、レイアウト、シャドウ、変換プロパティも含まれています）
* **TextStyle** – React Nativeの [Text](https://reactnative.dev/docs/text-style-props) プロパティセットはテキストのスタイル設定を可能にします。これらのプロパティを使用すると、テキストのフォントを制御できます。 選択状況など(テキストプロパティセットにはレイアウトプロパティも含まれています)
* **ImageStyle** – React Native’s [Image](https://reactnative.dev/docs/image-style-props) property set will allow you to style images from network sources, a local library, and temporary local images – using these properties you can alter an image’s size, border, and more, while the image property set also contains layout properties (the `resizeMode` value `repeat` is not supported)
* **Colors** – React Nativeの [Color Reference](https://reactnative.dev/docs/colors) プロパティセットで色を変更することができます – 赤緑色の表記を使用して色をカスタマイズできます。 色相や彩度などを変えると

### 2.1 クラス名

各スタイルオブジェクトには、オブジェクトのクラス名と呼ばれる名前があります。 新しいカスタムクラスを作成し、ウィジェット クラス プロパティにクラス名を設定することで、単一のウィジェットにスタイルを適用できます。 ここでは、 `customClassName` を作成するコードを見ることができます。

```javascript
// A custom styling class
export const customClassName = {
    container: {
        // ViewStyle properties
        paddingTop: 5
    },
    text: {
        // TextStyle properties
        fontWeight: "bold"
    }
}
```

そのカスタムクラスはMendix Studio Proで簡単にアクセスできます。

{{% image_container width="400" %}}![custom class](attachments/native-styling-refguide/custom-class.png){{% /image_container %}}

ウィジェットのインスタンスにスタイリングを適用したい場合は、ウィジェットのデフォルトクラスを拡張できます。 各ウィジェットのデフォルトクラスは、以下の [データウィジェット](#understanding-data-widgets) セクションに名前が付けられています。 以下の例は、デフォルトのクラスを拡張する方法を示しています。

```javascript
export const ActionButton = {
    container: {
        // ViewStyle properties
        borderWidth: 3
    },
    caption: {
        // TextStyle properties
        fontSize: 20
    },
};
```

Add-on widgets each have their own default styling classes based on their full widget IDs (found in *{widget name}.xml*), and can be created by replacing the dots with underscores. 以下の例は、プラグ可能なウィジェットのデフォルトスタイリングクラスを示しています。

```javascript
export const com_mendix_widget_native_badge_Badge = (Badge = {
    text: {
        // TextStyle properties
        color: "#00FF00",
    }
});
```

自分のクラスを作成するための詳細情報 [独自のクラスの作成](/howto/mobile/how-to-use-native-styling#creating-your-own-classes) セクションの *Style Your Mendix Native Mobile App* を参照してください。 このドキュメントでは、カスタムクラスをデザインプロパティとして使用する方法も説明しています。

## 3つのデータウィジェット {#understanding-data-widgets}

データウィジェットは、多くのMendixアプリにとって不可欠です。 これらのウィジェットは、ユーザーがデータオブジェクトを作成して処理することを可能にし、アプリのニーズに合わせてカスタマイズすることができます。

### 3.1 データ表示ウィジェット

データ ビュー ウィジェットには、1 つのデータ オブジェクトの内容が表示されます。 このウィジェットの詳細については、 [Data View](data-view)を参照してください。このウィジェットにはユーザーインターフェイスがないため、スタイルをサポートしていません。

### 3.2 リスト表示ウィジェット {#list-view}

リストビューには、縦または横に配置されたオブジェクトのリストが表示されます。 このウィジェットの詳細については、 [リストビュー](list-view) を参照してください。 これはデフォルトのリスト表示ではありませんが、リスト表示ウィジェットがアプリでどのように見えるかを示します:

{{% image_container width="350" %}}![list view](attachments/native-styling-refguide/list-view.png){{% /image_container %}}

ウィジェットのコードは次のように構成されています。

```xml
<container>
    <listItem>コンテンツ</listItem>
    <listItem>コンテンツ</listItem>
</container>
```

ウィジェットのスタイルプロパティは以下の通りです:

| 要素                 | スタイルのプロパティ          | 説明                                                                                                                                                                              |
| ------------------ | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `コンテナ`             | すべてのViewStyle プロパティ |                                                                                                                                                                                 |
| `コンテナ`             | `numColumns`        | これは、リストがレンダリングする列の数です(デフォルトは 1 です)。                                                                                                                                             |
| `listItem`         | すべてのViewStyle プロパティ |                                                                                                                                                                                 |
| `listItem`         | `rippleColor`       | This is the color of the ripple on Android, and will be applied only when the item has an on click action set, otherwise it will be ignored (defaults to `rgba(0, 0, 0, 0.2)`). |
| `listItem`         | `underlayColor`     | iOS上でアイテムを押す際の色です。クリック操作が設定されている場合にのみ適用されます。 それ以外の場合は無視され、不透明度のみに設定されます。                                                                                                        |
| `listItemDisabled` | `listItem` と同じプロパティ | `listItem` スタイルを上書きします。 アイテムにクリックアクションがあり、アクションが実行できない、またはアクション中に無効になっている場合。                                                                                                    |

すべてのリストビューにスタイルを適用するデフォルトのクラスは `ListView` という名前です。

## 一般的なウィジェット4個

一般的なウィジェットは、ほぼすべてのアプリページで使用されます。 ユビキタスのため、一般的なウィジェットのスタイルを学ぶことはアプリにとって大きな違いをもたらします。

### 4.1 テキスト

テキストウィジェットには、オプションとしてパラメータを含めることができるテキストが表示されます。 これらのウィジェットの詳細については、 [テキストウィジェット](text) を参照してください。 ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <text>コンテンツ</text>
</container>
```

| 要素     | スタイルのプロパティ                     | 説明 |
| ------ | ------------------------------ | -- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |    |
| `テキスト` | これにはすべての TextStyle プロパティがあります。 |    |

すべてのテキストにスタイルを適用するデフォルトのクラスは、 `Text` という名前です。

### 4.2 画像 {#image}

イメージ ウィジェットを使用して、定義済みのイメージをページ、レイアウト、またはスニペットに表示できます。 これらのウィジェットの詳細については、 [Image Widgets](image) を参照してください。 ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <image/>
</container>
```

| 要素                  | スタイルのプロパティ                      | 説明                                                                                                                                                                                   |
| ------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。  |                                                                                                                                                                                      |
| `コンテナ`              | `rippleColor`                   | This is the color of the ripple on Android, and will be applied only when the container has an on click action set, otherwise it will be ignored (defaults to `rgba(0, 0, 0, 0.2)`). |
| `コンテナ`              | `underlayColor`                 | これは、iOS でコンテナを押したまま色であり、コンテナがクリックアクションセットを持っている場合にのみ適用されます。 それ以外の場合は無視され、不透明度のみに設定されます。                                                                                              |
| `containerDisabled` | `コンテナ` と同じプロパティ                 | イメージにクリックアクションがあり、アクションが実行できない、またはアクション中に無効になっている場合、 `コンテナ` スタイルを上書きします。                                                                                                             |
| `画像`                | これにはすべての ImageStyle プロパティがあります。 |                                                                                                                                                                                      |
| `imageDisabled`     | `イメージ` と同じプロパティ                 | 画像にクリックアクションがあり、アクションが実行できない、またはアクション中に無効になっている場合、 `イメージ` スタイルを上書きします。                                                                                                               |

すべての静的なイメージスタイルをスタイル化するためのデフォルトのクラスは、 `Image` という名前です。 モデルから読み込まれた画像は、以下の `Image Viewer` セクションで説明されているように、 [NativeDynamicImage](#image-viewer) でスタイル付けされていることに注意してください。

### 4.3 ページタイトル

ページ タイトル ウィジェットには、使用されているページのタイトルが表示されます。 これは、ページ自体で定義されたタイトル、またはページを表示するときに定義されたオーバーライドタイトルになります。 このウィジェットの詳細については、 [ページタイトル](page-title) を参照してください。 ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <text>ページタイトル</text>
</container>
```

| 要素     | スタイルのプロパティ                     | 説明 |
| ------ | ------------------------------ | -- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |    |
| `テキスト` | これにはすべての TextStyle プロパティがあります。 |    |

すべてのページタイトルにスタイルを適用するデフォルトのクラスは `PageTitle` に名前が付けられます。

### 4.4 レイアウトグリッド

レイアウト グリッド ウィジェットを使用して、ページのコンテンツを構成できます。 固定または動的なサイズを設定できる行と列を作成できます。

The widget’s style properties are divided over several objects: `LayoutGrid`, `row`, `noGuttersRow`, `col`, `colFitToContent`, `col1`, `col2`, `col3`, `col4`, `col5`, `col6`,  `col7`, `col8`, `col9`, `col10`, `col11`, `col12`, and `noGutters`.

`列` の Width プロパティが "自動入力" の場合、列format@@2 が適用されます。

`colFitToContent` は、列の Width プロパティが "Auto-fit content" の場合に適用されます。

`col1`, `col2`, `col3`, `col4`, `col5`, `col6`,  `col7`, `col8`, `col9`, `col10`, `col11`, `col12` are applied when the Width on a column property is "Manual". 関連する Size プロパティに基づいて適用されるクラスは 1 つだけです。

`noGuttersRow` (Row) と `noGutters` (Column) は、行の columns プロパティが "No" に設定されている場合に適用されます。

メイン `のレイアウトグリッド`:

```xml
<container></container>
```

`行`, `noGuttersRow`:

```xml
<container></container>
```

The `col`, `colFitToContent`, `col1`, `col2`, `col3`, `col4`, `col5`, `col6`,  `col7`, `col8`, `col9`, `col10`, `col11`, `col12`, `noGutters`:

```xml
<container></container>
```

結果の DOM は以下のようになります:

```xml
<container>
    <row>
        <col></col>
    </row>
</container>
```

## 5つのコンテナウィジェット

コンテナーウィジェットは、ページのコンテンツの構造を提供するツールのセットです。 以下に詳細なコンテナウィジェットと呼ばれる特定のウィジェットもあります。 これらのウィジェットの詳細については、 [コンテナウィジェット](container-widgets) を参照してください。

### 5.1 コンテナ

コンテナウィジェットを使用して、ウィジェットのスタイルを設定したり、グループを非表示にしたりできます。 このウィジェットにはデフォルトで視覚的な表示はありませんが、スタイルを使用してスペースを追加することはできます。 ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    コンテンツ
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                                                                                                                                                                                   |
| ------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                                                                                                                                                                                      |
| `コンテナ`              | `rippleColor`                  | This is the color of the ripple on Android, and will be applied only when the container has an on click action set, otherwise it will be ignored (defaults to `rgba(0, 0, 0, 0.2)`). |
| `コンテナ`              | `underlayColor`                | これは、iOS でコンテナを押したまま色であり、コンテナがクリックアクションセットを持っている場合にのみ適用されます。 それ以外の場合は無視され、不透明度のみに設定されます。                                                                                              |
| `containerDisabled` | `コンテナ` と同じプロパティ                | これは `コンテナ` スタイルを上書きします。クリック操作セットが存在し、アクションが実行できない場合、またはアクション中に無効になっている場合。                                                                                                            |

すべてのページタイトルにスタイルを適用するデフォルトのクラスは、 `Container` と命名されます。

### 5.2 タブコンテナ

タブコンテナは、複数のタブページに分類された情報を表示するために使用されます。 タブコンテナは、デバイスのスクリーンスペースを超える情報を表示するのに役立ちます。 これは、デフォルトのタブコンテナウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="350" %}}![tab container](attachments/native-styling-refguide/tab-container.png){{% /image_container %}}

ウィジェットのコードは次のように構成されています。

```xml
<container>
    <tabBar>
        <tab>
            <activeLabel>PAGE 1</activeLabel>
            <badgeContainer><badgeCaption /></badgeContainer>
        </tab>
        <tab>
            <label>PAGE 2</label>
        </tab>
        <indicator>
    <tabBar>
    content
</container>
```

ウィジェットのスタイルプロパティは以下の通りです:

| 要素               | スタイルのプロパティ                     | 説明                                                              |
| ---------------- | ------------------------------ | --------------------------------------------------------------- |
| `コンテナ`           | これにはすべての ViewStyle プロパティがあります。 |                                                                 |
| `tabBar`         | これにはすべての ViewStyle プロパティがあります。 |                                                                 |
| `tabBar`         | `バウンス`                         | これは、スクロール時にタブバーがバウンドするかどうかを示すブール値です。                            |
| `tabBar`         | `pressColor`                   | これはマテリアルリップルの色です(Androidのみ)。                                    |
| `tabBar`         | `pressOpacity`                 | これは、押されたタブの不透明度です。                                              |
| `tabBar`         | `scrollEnabled`                | これはブール値でスクロール可能なタブを有効にします。                                      |
| `tabBar`         | `tabBarPosition`               | これは、タブビューのタブバーの位置です。 可能な値は `top` と `bottom` (デフォルトは `top` ) です。 |
| `インジケーター：`       | これにはすべての ViewStyle プロパティがあります。 |                                                                 |
| `tab`            | これにはすべての ViewStyle プロパティがあります。 |                                                                 |
| `ラベル`            | これにはすべての TextStyle プロパティがあります。 |                                                                 |
| `activeLabel`    | これにはすべての TextStyle プロパティがあります。 |                                                                 |
| `badgeContainer` | これにはすべての ViewStyle プロパティがあります。 |                                                                 |
| `badgeCaption`   | これにはすべての TextStyle プロパティがあります。 |                                                                 |

すべてのタブコンテナをスタイル化するデフォルトのクラスは `TabContainer` という名前です。

### 5.3 スクロールコンテナ

スクロールコンテナを使用して、ページの一部のスクロールを有効にします。 このウィジェットにはデフォルトで視覚的な表示はありませんが、スタイルを使用してスペースを追加することはできます。  ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    スクロール可能なコンテンツ
</container>
```

| 要素     | スタイルのプロパティ                     | 説明 |
| ------ | ------------------------------ | -- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |    |

すべてのスクロールコンテナをスタイル化するデフォルトのクラスは、 `ScrollContainer` という名前です。

## 6 入力ウィジェット

入力ウィジェットは通常、ユーザーにデータを表示し、データを編集できるようにするために使用されます。 これらのウィジェットの詳細については、 [入力ウィジェット](input-widgets) を参照してください。

### 6.1 テキスト ボックス {#text-box}

テキストボックスはテキストの値を表示または編集するために使用できます。 これは、検証フィードバックを含むテキスト ボックス ウィジェットとプレーンテキスト ボックス ウィジェットがアプリ内で見ることができる方法です。

{{% image_container width="350" %}}![text box](attachments/native-styling-refguide/text-box.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下のように構成されています:

```xml
<container>
    <label>Text box</label>
    <inputError>Content invalid</inputError>
    <validationMessage>Input validation feedback message</validationMessage>
</container>
<container>
    <label>Text box</label>
    <input>Valid text</input>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                                                                                                                                                                                                                                                                                                                        |
| ------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                                                                                                                                                                                                                                                                                                                           |
| `containerDisabled` | `コンテナ` と同じプロパティ                | テキストボックスが編集不可の場合、 `コンテナ` スタイルを上書きします。                                                                                                                                                                                                                                                                                     |
| `input`             | これにはすべての TextStyle プロパティがあります。 |                                                                                                                                                                                                                                                                                                                           |
| `input`             | `autoCapitalize`               | This automatically capitalizes certain characters when the user types:<br><br>* `characters`: capitalizes all characters<br>* `words`: capitalizes the first letter of each word<br>* `sentences`: capitalizes the first letter of each sentence (default)<br>* `none`: capitalizes nothing |
| `input`             | `placeholderTextColor`         | これはプレースホルダ文字列のテキスト色です。                                                                                                                                                                                                                                                                                                    |
| `input`             | `selectionColor`               | これはテキスト入力のハイライトとカーソルの色です。                                                                                                                                                                                                                                                                                                 |
| `input`             | `underlineColorAndroid`        | これは `入力` 下線の色です。                                                                                                                                                                                                                                                                                                          |
| `inputFocused`      | `入力と同じプロパティ`                   | テキストボックスがフォーカスされている場合、 `入力` スタイルを上書きします (Studio Pro v8.15 付き)。                                                                                                                                                                                                                                                            |
| `inputError`        | これは `入力` と同じプロパティを持ちます         | バリデーションエラーがある場合は、 `入力` スタイルを上書きします。                                                                                                                                                                                                                                                                                       |
| `inputDisabled`     | `入力と同じプロパティ`                   | テキストボックスが編集不可の場合、 `入力` スタイルを上書きします。                                                                                                                                                                                                                                                                                       |
| `ラベル`               | すべての TextStyle プロパティがあります      |                                                                                                                                                                                                                                                                                                                           |
| `ラベル`               | `numberOfLines`                | ラベルテキストをラップする行の最大数です。 テキストがそれ以上長くなっている場合は、省略記号で切り取られます (デフォルトは 1)。                                                                                                                                                                                                                                                        |
| `labelDisabled`     | `label` と同じプロパティ               | テキストボックスが編集不可の場合、 `ラベル` スタイルを上書きします。                                                                                                                                                                                                                                                                                      |
| `validationMessage` | これにはすべての TextStyle プロパティがあります。 |                                                                                                                                                                                                                                                                                                                           |

すべてのテキストボックスをスタイル付けするデフォルトのクラスは、 `TextBox` という名前です。

### 6.2 テキストエリア

テキストボックスを使用して、複数行のテキスト値を表示または編集できます。 このウィジェットは上記の [テキスト ボックス](#text-box) ウィジェットと同じスタイルプロパティと構造をサポートしています。 これは、検証フィードバックを伴うテキストエリアウィジェットとプレーンテキストエリアウィジェットがアプリ内で見ることができる方法です。

{{% image_container width="350" %}}![text area](attachments/native-styling-refguide/text-area.png){{% /image_container %}}

すべてのテキストエリアをスタイル化するデフォルトのクラスは、 `TextArea` という名前です。

### 6.3 ドロップ ダウン {#drop-down}

ドロップダウンは、列挙属性の表示と編集に使用できる入力ウィジェットです。

Studio Pro v8.11 以降、ドロップダウン ウィジェットには、 `useUniformDesign: boolean` と呼ばれる新しいスタイル プロパティがあり、両方のプラットフォームで均一なデザインを可能にします。

ウィジェットのレンダリング階層は、非均一では以下のとおりです:

```xml
<container>
    <label>Drop down enumeration</label>
    <value>Content invalid</value>
    <validationMessage>Validation feedback enumeration</validationMessage>
</container>
<picker>
    <pickerBackdropIOS/>
    <pickerTopIOS><button>close</button></pickerTopIOS>
    <pickerIOS>
        <pickerItemIOS>First</pickerItemIOS>
        <pickerItemIOS>Second</pickerItemIOS>
        <pickerItemIOS>Third</pickerItemIOS>
    </pickerIOS>
</picker>
```

ウィジェットのレンダリング階層は、ユニフォームの次のとおりです:

```xml
<container>
    <label>Drop down enumeration</label>
    <valueContainer>
        <value>First</value>
    <icon/>
    </valueContainer>
    <validationMessage>Validation feedback enumeration</validationMessage>
</container>
<menuWrapper>
    <selectedItemContainer>
        <selectedItem>First</selectedItem>    <= Selected
    </selectedItemContainer>
    <itemContainer>
        <item>Second</item>
    </itemContainer>
    <itemContainer>
        <item>Third</item>
    </itemContainer>
</menuWrapper>
```

| 要素                      | スタイルのプロパティ                                   | 説明                                                                                         |
| ----------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------ |
| `コンテナ`                  | これにはすべての ViewStyle プロパティがあります。               |                                                                                            |
| `containerDisabled`     | `コンテナ` と同じプロパティ                              | ドロップダウンが編集不可の場合、 `コンテナ` スタイルを上書きします。                                                       |
| `ラベル`                   | これにはすべての TextStyle プロパティがあります。               |                                                                                            |
| `ラベル`                   | `numberOfLines`                              | ラベルテキストをラップする行の最大数。 テキストがそれ以上であれば、楕円で切り取られます。 デフォルトは `1` です。                               |
| `labelDisabled`         | `label` と同じプロパティ                             | ドロップダウンが編集できない場合は、 `ラベル` スタイルを上書きします。                                                      |
| `pickerIOS`             | これにはすべての ViewStyle プロパティがあります。               |                                                                                            |
| `pickerBackdropIOS`     | これにはすべての ViewStyle プロパティがあります。               |                                                                                            |
| `pickerTopIOS`          | これにはすべての ViewStyle プロパティがあります。               |                                                                                            |
| `validationMessage`     | これにはすべての TextStyle プロパティがあります。               | 検証メッセージをスタイル化します(Studio Pro v8.11)。                                                        |
| `値`                     | すべての TextStyle プロパティがあります                    | ドロップダウンと PickerIOS アイテムを切り替える値ボタンをスタイル化します。 プレースホルダが選択されている場合、placeholderTextColor が適用されます |
| `useUniformDesign`      | `boolean`                                    | 新しいユニフォームデザインを有効にします(Studio Pro v8.11)。                                                    |
| `iconStyle`             | すべての TextStyle プロパティがあります                    | 値 (Studio Pro v8.15) の横にある矢印アイコンをスタイル化します。                                                 |
| `値`                     | `placeholderTextColor: string`               | プレースホルダが選択されている場合、placeholderTextColor が適用されます (Studio Pro v8.11)。                         |
| `valueFocused`          | `値` と同じプロパティ                                 | ドロップダウンボックスがフォーカスされている場合、 `値` スタイルを上書きします。 (Studio Pro v8.15 を使用)。                         |
| `valueContainer`        | これはすべてのViewStyle プロパティ & rippleColor を持っています | 値ボタンのコンテナをスタイル化します(Studio Pro v8.11)。                                                      |
| `valueContainerFocused` | `valueContainer` と同じプロパティ                    | ドロップダウンボックスがフォーカスされている場合、 `valueContainer` スタイルを上書きします (Studio Pro v8.15 を使用)。             |
| `menuWrapper`           | これはすべてのViewStyleプロパティを持っています                 | すべてのメニュー アイテムを囲むラッパービューをスタイル化します(Studio Pro v8.11)。                                        |
| `itemContainer`         | これはすべてのViewStyleプロパティを持っています                 | 選択したアイテムコンテナ(Studio Pro v8.11を使用)を含むドロップダウンメニュー内のすべてのアイテムコンテナをスタイル化します。                    |
| `項目`                    | これにはすべてのTextStlyeプロパティがあります                  | 選択した項目(Studio Pro v8.11)を含むドロップダウンメニュー内のすべての項目にスタイルを設定します。                                 |
| `selectedItem`          | すべての TextStyle プロパティがあります                    | ドロップダウンメニューで選択した項目をスタイル化します(Studio Pro v8.11)。                                             |
| `selectedItemContainer` | これはすべてのViewStyleプロパティを持っています                 | (Studio Pro v8.11で) ドロップダウンメニューで選択した項目のコンテナにスタイルを設定します。                                    |

### 6.4 チェック ボックス

チェック ボックスの入力ウィジェットを使用して、ブール値の属性を表示および編集でき、スイッチとしてレンダリングされます。 これは、チェック ボックス ウィジェットがアプリ内でどのように見えるかです:

{{% image_container width="350" %}}![check box](attachments/native-styling-refguide/check-box.png){{% /image_container %}}

ウィジェットのスタイルプロパティ構造は以下のとおりです:

```xml
<container>
    <label>Boolean switch</label>
    <inputError>
        <trackColorOff/>
        <thumbColorOff/>
    </inputError>
    <validationMessage>Feedback switch input</validationMessage>
</container>
<container>
    <label>Valid boolean</label>
    <input>
        <trackColorOn/>
        <thumbColorOn/>
    </input>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                                                               |
| ------------------- | ------------------------------ | ---------------------------------------------------------------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `containerDisabled` | `コンテナ` と同じプロパティ                | テキストボックスが編集不可の場合、 `コンテナ` スタイルを上書きします。                            |
| `input`             | これにはすべての TextStyle プロパティがあります。 |                                                                  |
| `input`             | `trackColorOn`                 | オンにすると、スイッチトラックのカスタムカラーが変わります。                                   |
| `input`             | `trackColorOff`                | オフにすると、スイッチトラックのカスタムカラーが変わります。                                   |
| `input`             | `thumbColorOn`                 | 電源を入れると前面スイッチのグリップの色が変わります。 iOS で設定した場合、スイッチのグリップはドロップシャドウを失います。 |
| `input`             | `thumbColorOff`                | 電源を切ったときの前面スイッチのグリップの色。 iOS で設定した場合、スイッチのグリップはドロップシャドウを失います。     |
| `inputError`        | これは `入力` と同じプロパティを持ちます         | バリデーションエラーがある場合は、 `入力` スタイルを上書きします。                              |
| `inputDisabled`     | これは `入力` と同じプロパティを持ちます         | このチェック ボックスが編集不可の場合、 `入力` スタイルを上書きします。                           |
| `ラベル`               | すべての TextStyle プロパティがあります      |                                                                  |
| `ラベル`               | `numberOfLines`                | ラベルテキストをラップする行の最大数。 テキストがそれ以上であれば、楕円で切り取られます。 デフォルトは `1` です。     |
| `labelDisabled`     | `label` と同じプロパティ               | このチェック ボックスが編集不可の場合、 `ラベル` スタイルを上書きします。                          |
| `validationMessage` | これにはすべての TextStyle プロパティがあります。 |                                                                  |

すべてのチェックボックスの入力スタイルを設定するデフォルトのクラスは `Checkbox` という名前です。

### 6.5 日付の選択

日付ピッカーとは、日付や時刻の属性を表示および編集するために使用できる入力ウィジェットです。 これは、日付ピッカーウィジェットがアプリ内でどのように見えるかです:

{{% image_container width="300" %}}![date picker](attachments/native-styling-refguide/date-picker.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <label>Drop down enumeration</label>
    <value>Content invalid</value>
    <validationMessage>Validation feedback enumeration</validationMessage>
    <pickerBackdropIOS>iOS picker modal shadow container
        <pickerIOS>iOS picker
            <pickerTopIOS>iOS picker modal header</pickerTopIOS>
        </pickerIOS>
    </pickerBackdropIOS>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                                                                                                                                       |
| ------------------- | ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                                                                                                                                          |
| `containerDisabled` | `コンテナ` と同じプロパティ                | 日付ピッカーが編集不可の場合、 `コンテナ` スタイルを上書きします。                                                                                                      |
| `ラベル`               | これにはすべての TextStyle プロパティがあります。 |                                                                                                                                          |
| `ラベル`               | `numberOfLines`                | ラベルテキストをラップする行の最大数です。 テキストがそれ以上長くなっている場合は、省略記号で切り取られます (デフォルトは `1`)。                                                                     |
| `labelDisabled`     | `label` と同じプロパティ               | 日付ピッカーが編集不可の場合、 `ラベル` スタイルを上書きします。                                                                                                       |
| `値`                 | すべての TextStyle プロパティがあります      |                                                                                                                                          |
| `値`                 | `rippleColor`                  | This is the color of the ripple on Android, and will be applied only when the date picker is pressed (defaults to `rgba(0, 0, 0, 0.2)`). |
| `値`                 | `underlayColor`                | iOSで日付ピッカーを押しながら色を指定します。設定されていない場合は不透明度のみがデフォルトになります。                                                                                    |
| `valueDisabled`     | すべての TextStyle プロパティがあります      | 日付ピッカーが編集不可の場合、 `値` のスタイルを上書きします。                                                                                                        |
| `プレースホルダー`          | すべての TextStyle プロパティがあります      |                                                                                                                                          |
| `プレースホルダー無効`        | すべての TextStyle プロパティがあります      | 日付ピッカーが編集不可の場合、 `プレースホルダー` スタイルを上書きします。                                                                                                  |
| `validationMessage` | すべての TextStyle プロパティがあります      |                                                                                                                                          |
| `pickerBackdropIOS` | これはすべてのViewStyleプロパティを持っています   |                                                                                                                                          |
| `pickerIOS`         | これはすべてのViewStyleプロパティを持っています   |                                                                                                                                          |
| `pickerIOS`         | `色`                            |                                                                                                                                          |
| `pickerTopIOS`      | これはすべてのViewStyleプロパティを持っています   |                                                                                                                                          |

すべての日付ピッカー入力をスタイル化するデフォルトのクラスは `DatePicker` という名前です。

### 6.6 リファレンスセレクター

参照セレクタは、関連付けを表示および編集するために使用できる入力ウィジェットです。 このウィジェットの詳細については、 [リファレンスセレクター](reference-selector) を参照してください。 このウィジェットは上記の [ドロップダウン](#drop-down) ウィジェットと同じスタイルプロパティと構造をサポートしています。

すべての参照セレクタ入力スタイルのデフォルトクラスは、 `ReferenceSelector` という名前です。

## 7件のファイルウィジェット

ファイルウィジェットは、ユーザーアプリが画像やその他のファイルを管理するのに役立ちます。 これらのウィジェットの詳細については、 [ファイルウィジェット](file-widgets) を参照してください。

### 7.1 画像ビューアー {#image-viewer}

画像ビューアは、画像を表示するために使用することができます。 このウィジェットは上記の [イメージ](#image) ウィジェットと同じスタイルプロパティと構造をサポートしています。

すべての画像視聴者にスタイルを適用するデフォルトのクラスは、  `NativeDynamicImage` という名前です。

## 8ボタンウィジェット

ボタンウィジェットは、ユーザーがアクションを実行するのに役立ちます。 これらのウィジェットの詳細については、 [ボタンウィジェット](button-widgets) を参照してください。

### 8.1 アクションボタン

アクションボタンは、ナノフローの呼び出し、ページを開くなど、さまざまなアクションを実行できます。

{{% image_container width="350" %}}![action button](attachments/native-styling-refguide/action-button.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <icon/><caption>primary</caption>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                                                                           |
| ------------------- | ------------------------------ | ---------------------------------------------------------------------------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                                                                              |
| `コンテナ`              | `rippleColor`                  | これは、Android のリップルの色です (デフォルトでは `rgba(0, 0, 0, 0.2)`)。                        |
| `コンテナ`              | `underlayColor`                | これは、iOSのボタンを押している間の色です。設定されていない場合は、不透明度のみに設定されます。                            |
| `containerDisabled` | `コンテナ` と同じプロパティ                | `コンテナ` スタイルを上書きします。ボタンにクリックアクションセットがあり、実行できない場合や、 `アクション中は無効にする` が設定されている場合。 |
| `図表番号`              | これにはすべての TextStyle プロパティがあります。 |                                                                              |
| `キャプション無効`          | 図表番号 `と同じプロパティ`                | ボタンにクリックアクションセットがあり、実行できない、または `アクション中に` 無効に設定されている場合、 `キャプション`スタイルを上書きします。  |
| `アイコン`              | これにはすべての ViewStyle プロパティがあります。 |                                                                              |
| `アイコン`              | `サイズ`                          | これはボタンアイコンのサイズです (デフォルトは `12`)。                                              |
| `アイコン`              | `色`                            | これはボタンアイコンの色です。                                                              |
| `アイコンが無効です`         | `アイコン` と同じプロパティ                | `アイコン` は、ボタンにクリックアクションセットがあり、実行できないか、 `アクション中は無効` で設定されている場合に上書きします。         |

すべてのアクションボタンをスタイル化するためのデフォルトクラスは、 `ActionButton` という名前です。 ただし、ヘッダー内のアクションボタンには、デフォルトのクラス `ActionButtonHeader` があります。

## 9 ページ {#pages}

スタイルページには、クラスをページまたはそのレイアウトに追加できます。 ステータスバーとヘッダーはページの一部であり、このようにスタイル設定することもできます。

```xml
<page>
    <statusBar/>
    <header/>
    <container>
        application content
    </container>
</page>
```

| 要素         | スタイルのプロパティ                     | 説明                                                                |
| ---------- | ------------------------------ | ----------------------------------------------------------------- |
| `ステータス バー` | `barStyle`                     | ステータスバーのスタイル。 `ダークコンテンツ` (黒文字) または `ライトコンテンツ` (白文字) のいずれかを指定できます。 |
| `ステータス バー` | `backgroundColor`              | ステータスバーの背景色 (Androidのみ)                                           |
| `ヘッダー`     | `コンテナ`                         | これにはすべての ViewStyle プロパティがあります。                                    |
| `ヘッダー`     | `タイトル`                         | これにはすべての TextStyle プロパティがあります。                                    |
| `ヘッダー`     | `バックボタンのテキスト`                  | これにはすべての TextStyle プロパティがあります。                                    |
| `ヘッダー`     | `バックボタンアイコン`                   | これにはすべての ImageStyle プロパティがあります。                                   |
| `コンテナ`     | これにはすべての ViewStyle プロパティがあります。 |                                                                   |

レイアウトとページのデフォルトのクラスは、 `レイアウト` と `ページ` です。

## 10 Navigation {#navigation-widget}

ナビゲーションは下部のバー(ユーザーがアプリ内でナビゲートすることができます)と進捗オーバーレイ(何かのロードを待機中にロードインジケーターを表示するために使用できます)で構成されています。 アプリ内のナビゲーションは以下のようになります。

{{% image_container width="300" %}}![navigation widget](attachments/native-styling-refguide/nav-widget.png){{% /image_container %}}

ナビゲーション スタイルのプロパティは次のとおりです。

```xml
<app>
    <page/>
    <bottomBar/>
<app>
<progressOverlay>
    <background>
        <container>
            <activityIndicator/>
            <text/>
        </container>
    </background>
</progressOverlay>
```

| 要素                | スタイルのプロパティ          | 説明                                                      |
| ----------------- | ------------------- | ------------------------------------------------------- |
| `bottomBar`       | `コンテナ`              | これにはすべての ViewStyle プロパティがあります。                          |
| `bottomBar`       | `ラベル`               | これにはすべての TextStyle プロパティがあります。                          |
| `bottomBar`       | `selectedLabel`     | これにはすべての TextStyle プロパティがあります。                          |
| `bottomBar`       | `アイコン`              | これにはすべての ViewStyle プロパティがあります。                          |
| `bottomBar`       | `アイコンを選択`           | これにはすべての ViewStyle プロパティがあります。                          |
| `progressOverlay` | `背景`                | これにはすべての ViewStyle プロパティがあります。                          |
| `progressOverlay` | `コンテナ`              | これにはすべての ViewStyle プロパティがあります。                          |
| `progressOverlay` | `activityIndicator` | これは、 [アクティビティ インジケータ](#activity-indicator) ウィジェットと同じです。 |
| `progressOverlay` | `テキスト`              | これにはすべての TextStyle プロパティがあります。                          |

ナビゲーションスタイルのデフォルトクラスは、  `navigationStyle` という名前です。 ナビゲーションにカスタムクラススタイルのサポートはありません。

## アドオンウィジェット11個

アドオンウィジェットは [Native Mobile Resources](/appstore/modules/native-mobile-resources) モジュールを介して配布され、Mendix Studio Proには同梱されません。 他のアドオンウィジェットは、他のアプリからページをインポートするモジュールだけでなく、アプリテンプレートを介して配布されることもあります。

### 11.1 Activity Indicator {#activity-indicator}

アクティビティ インジケータウィジェットには、円形のローディングインジケータが表示されます。 アクティビティインジケータウィジェットがアプリ内でどのように見えるかを示します。

{{% image_container width="350" %}}![activity indicator](attachments/native-styling-refguide/activity-indicator.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```javascript
<container>
    <indicator/>
</container>
```

| 要素         | スタイルのプロパティ                     | 説明                               |
| ---------- | ------------------------------ | -------------------------------- |
| `コンテナ`     | これにはすべての ViewStyle プロパティがあります。 |                                  |
| `インジケーター：` | `色`                            | これはインジケーターの色です (デフォルトは `グレー`)。   |
| `インジケーター：` | `サイズ`                          | 指標の値は `大` と `小` (デフォルトは `大`) です。 |

The default class to style all activity indicators is named `com_mendix_widget_native_activityindicator_ActivityIndicator`.

### 11.2 アプリイベント

アプリイベントウィジェットでは、アプリのネットワーク状態が変更されたときにアクションを設定することができ、アクションコールの制限を設定することができます。 このウィジェットにはユーザーインターフェイスがないため、スタイルをサポートしていません。

### 11.3 背景画像

format@@0 ウィジェットでは、画像の上に 1 つまたは複数のウィジェットをレイヤリングできます。

ウィジェットのスタイルプロパティは以下の通りです:

```javascript
<container>
    <image />
</container>
```

| 要素     | スタイルのプロパティ                      | 説明                                |
| ------ | ------------------------------- | --------------------------------- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。  |                                   |
| `画像`   | これにはすべての ImageStyle プロパティがあります。 |                                   |
| `画像`   | `svgColor`                      | SVG 画像の色を設定するプロパティです(デフォルトは `黒`)。 |

すべての背景画像をスタイル化するデフォルトのクラスは `com_mendix_widget_native_backgroundimage_BackgroundImage` と命名されます。

### 11.4 バッジ

バッジウィジェットには、テキストまたは値がバッジとして表示されます。 アプリ内でバッジウィジェットがどのように見えるかを示します。

{{% image_container width="350" %}}![badge](attachments/native-styling-refguide/badge.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <text>新しい</text>
</container>
```

| 要素     | スタイルのプロパティ                     | 説明 |
| ------ | ------------------------------ | -- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |    |
| `テキスト` | これにはすべての TextStyle プロパティがあります。 |    |

全てのバッジをスタイル付けするデフォルトのクラスは `com_mendix_widget_native_badge_Badge` という名前です。

### 11.5 バーコードスキャナ

バーコードスキャナウィジェットを使用すると、アプリはバーコードとQRコードをスキャンできます。 このウィジェットは、スタイルのあるコンテナでカメラビューをレンダリングします。

ウィジェットのスタイルプロパティは以下のとおりです。

```javascript
<container>
        <mask />
<container />
```

| 要素     | スタイルのプロパティ                     | 説明                                                 |
| ------ | ------------------------------ | -------------------------------------------------- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |                                                    |
| `マスク`  | これにより、以下のプロパティのみが許可されます。       |                                                    |
| `マスク`  | `色`                            | マスク境界インジケータの色を設定するプロパティです(デフォルトは `#62B1F6`)。       |
| `マスク`  | `width`                        | バーコードリーダの幅を設定するプロパティです。                            |
| `マスク`  | `高さ`                           | バーコードリーダの高さを設定します。                                 |
| `マスク`  | `backgroundColor`              | マスクの背景色を設定するプロパティです(デフォルトでは `rgba(0, 0, 0, 0.6)`)。 |

すべてのバーコードスキャナウィジェットをスタイル化するためのデフォルトのクラスは、 `com_mendix_widget_native_barcodescanner_BarcodeScanner` という名前です。

### 11.6 フィードバック

format@@0ウィジェットでは、ユーザーが直接フィードバックを行うことができます。 これは、フィードバックウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="350" %}}![feedback](attachments/native-styling-refguide/feedback-two.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

| 要素                  | スタイルのプロパティ                     | 説明                                                                   |
| ------------------- | ------------------------------ | -------------------------------------------------------------------- |
| `floatingButton`    | これにはすべての ViewStyle プロパティがあります。 |                                                                      |
| `ダイアログ`             | これにはすべての ViewStyle プロパティがあります。 |                                                                      |
| `タイトル`              | これにはすべての TextStyle プロパティがあります。 |                                                                      |
| `textAreaInput`     | これにはすべての TextStyle プロパティがあります。 |                                                                      |
| `textAreaInput`     | `placeholderTextColor`         | これはプレースホルダ文字列のテキスト色です。                                               |
| `textAreaInput`     | `selectionColor`               | これはテキスト入力のハイライトとカーソルの色です。                                            |
| `textAreaInput`     | `underlineColorAndroid`        | これは、Androidデバイス用の下線色です。                                              |
| `textAreaInput`     | `numberOfLines`                | これは、テキスト領域の高さであり、この数のテキスト行に基づいています。                                  |
| `switchLabel`       | これにはすべての TextStyle プロパティがあります。 |                                                                      |
| `switchInput`       | これにはすべての TextStyle プロパティがあります。 |                                                                      |
| `switchInput`       | `trackColorOn`                 | オンにすると、スイッチトラックのカスタムカラーになります。                                        |
| `switchInput`       | `trackColorOff`                | オフにすると、スイッチトラックのカスタムカラーになります。                                        |
| `switchInput`       | `thumbColorOn`                 | 電源を入れると、前面スイッチのグリップの色になります。 iOS で設定した場合、スイッチのグリップはドロップシャドウを失います。     |
| `switchInput`       | `thumbColorOff`                | 電源を切ったときのフォアグラウンドスイッチのグリップの色です。 iOS で設定した場合、スイッチのグリップはドロップシャドウを失います。 |
| `ボタン`               | `borderColor`                  | これはダイアログボタンの枠線の色です。                                                  |
| `ボタン`               | `borderWidth`                  | これはダイアログボタンの枠線の幅です。                                                  |
| `ボタン`               | `色`                            | これはダイアログボタンテキストの色です。                                                 |
| `無効なボタン`            | `色`                            | 無効にすると、ダイアログボタンのテキストの色になります。                                         |
| `activityIndicator` | `色`                            | これはフィードバックが送信されている間に表示されるアクティビティインジケーターの色です。                         |

すべてのフィードバックウィジェットをスタイル化するデフォルトのクラスは、 `com_mendix_widget_native_feedback_Feedback` という名前です。

### 11.7 フローティングアクションボタン

フローティング アクション ボタン ウィジェットを使用すると、フローティング アクション ボタンの外観と機能をカスタマイズできます。 ウィジェットのスタイルプロパティは以下の通りです:

| 要素                                | スタイルのプロパティ                      | 説明                    |
| --------------------------------- | ------------------------------- | --------------------- |
| `コンテナ`                            | これにはすべての ViewStyle プロパティがあります。  |                       |
| `ボタン`                             | これにはすべての ViewStyle プロパティがあります。  |                       |
| `ボタン`                             | `サイズ`                           | これはボタンの半径です。          |
| `ボタン`                             | `rippleColor`                   | これは、Androidのリップルの色です。 |
| `ボタンアイコン`                         | これにはすべての ImageStyle プロパティがあります。 |                       |
| `secondaryButton`                 | これにはすべての ViewStyle プロパティがあります。  |                       |
| `secondaryButton`                 | `サイズ`                           | これは、2番目のボタンの半径です。     |
| `secondaryButtonアイコン`             | これにはすべての ImageStyle プロパティがあります。 |                       |
| `secondaryButtonCaption`          | これにはすべての TextStyle プロパティがあります。  |                       |
| `secondaryButtonCaptionContainer` | これにはすべての ViewStyle プロパティがあります。  |                       |

すべてのフローティングアクションボタンをスタイル化するデフォルトクラスは、 `com_mendix_widget_native_floatingactionbutton_FloatingActionButton` という名前です。

### 11.8 マップ

マップウィジェットは、さまざまなデジタルマッププロバイダをサポートしています。 これは、地図ウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="350" %}}![maps](attachments/native-styling-refguide/maps.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

| 要素                 | スタイルのプロパティ                     | 説明                    |
| ------------------ | ------------------------------ | --------------------- |
| `コンテナ`             | これにはすべての ViewStyle プロパティがあります。 |                       |
| `loadingOverlay`   | これにはすべての ViewStyle プロパティがあります。 |                       |
| `loadingIndicator` | `色`                            | これは、ローディングインジケータの色です。 |
| `マーカー`             | `色`                            | これはロケーションマーカーの色です。    |
| `マーカー`             | `透明度`                          | これは位置マーカーの不透明度です。     |

すべてのマップウィジェットをスタイル化するデフォルトのクラスは `com_mendix_widget_native_maps_Maps` と命名されます。

### 11.9 通知

通知ウィジェットでは、カスタム メッセージをアプリに表示できます。 このウィジェットにはユーザーインターフェイスがないため、スタイルをサポートしていません。

### 11.10 プログレスバー

プログレスバーウィジェットに進捗率が表示されます。 これは、プログレスバーウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="300" %}}![progress bar](attachments/native-styling-refguide/progress-bar.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <bar><fill/></bar>
    <validationMessage/>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                          |
| ------------------- | ------------------------------ | --------------------------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                             |
| `バー`                | これにはすべての ViewStyle プロパティがあります。 |                             |
| `塗りつぶし`             | `backgroundColor`              | これは、塗りつぶされたプログレスバー部分の背景色です。 |
| `validationMessage` | これにはすべての TextStyle プロパティがあります。 |                             |

すべてのプログレスバーをスタイル化するデフォルトのクラスは、 `com_mendix_widget_native_progressbar_ProgressBar` という名前です。

### 11.11 進行サークル

進行状況サークルウィジェットには、正または負の値を使用して円内の進行状況が表示されます。 これは、進捗サークルウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="300" %}}![progress circle](attachments/native-styling-refguide/progress-circle.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <circle><fill/></circle>
    <validationMessage/>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明                                |
| ------------------- | ------------------------------ | --------------------------------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |                                   |
| `円`                 | `サイズ`                          | これは進行円の半径です。                      |
| `円`                 | `borderWidth`                  | これは進行中円の境界線の幅です。                  |
| `円`                 | `borderColor`                  | これは進行状況サークルの境界線の色です。              |
| `塗りつぶし`             | `backgroundColor`              | これは円の塗りつぶされた部分の色です。               |
| `塗りつぶし`             | `width`                        | これはプログレスサークルの幅です。                 |
| `塗りつぶし`             | `lineCapRound`                 | これは、回転する線の先端が四捨五入されているかどうかを決定します。 |
| `テキスト`              | これにはすべての TextStyle プロパティがあります。 |                                   |
| `validationMessage` | これにはすべての TextStyle プロパティがあります。 |                                   |

すべての進捗サークルをスタイル化するデフォルトのクラスは `com_mendix_widget_native_progressCircle` と命名されます。

### 11.12 QR Code

QRコードウィジェットは、ユーザーがスキャンできる値に基づいてQRコードを生成します。 これはQRコードウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="350" %}}![qr code](attachments/native-styling-refguide/qr-code.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <qrcode/>
</container>
```

| 要素       | スタイルのプロパティ                     | 説明         |
| -------- | ------------------------------ | ---------- |
| `コンテナ`   | これにはすべての ViewStyle プロパティがあります。 |            |
| `qrcode` | `サイズ`                          | QRコードのサイズ。 |
| `qrcode` | `色`                            | QRコードの色。   |
| `qrcode` | `backgroundColor`              | QRコードの背景色。 |

すべての QR コードをスタイル化するデフォルトのクラスは `com_mendix_widget_native_qrcode_QRCode` という名前です。

### 11.13 Range Slider {#range-slider}

範囲スライダーウィジェットでは、最大値と最小値のスライダーを使用して値の範囲を変更できます。 これは、範囲スライダーウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="300" %}}![range slider](attachments/native-styling-refguide/range-slider.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <track><highlight/><marker/></track>
    <validationMessage/>
</container>

<container>
    <trackDisabled><highlightDisabled/><markerDisabled/></trackDisabled>
    <validationMessage/>
</container>
```

| 要素                  | スタイルのプロパティ                     | 説明 |
| ------------------- | ------------------------------ | -- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |    |
| `トラック`              | これにはすべての ViewStyle プロパティがあります。 |    |
| `trackDisabled`     | これにはすべての ViewStyle プロパティがあります。 |    |
| `強調表示`              | これにはすべての ViewStyle プロパティがあります。 |    |
| `highlightDisabled` | これにはすべての ViewStyle プロパティがあります。 |    |
| `マーカー`              | これにはすべての ViewStyle プロパティがあります。 |    |
| `markerActive`      | これにはすべての ViewStyle プロパティがあります。 |    |
| `markerDisabled`    | これにはすべての ViewStyle プロパティがあります。 |    |
| `validationMessage` | これにはすべての TextStyle プロパティがあります。 |    |

すべての範囲スライダーの入力スタイルを設定するデフォルトのクラスは `com_mendix_widget_native_rangeslider_RangeSlider` という名前です。

### 11.14 セーフエリアビュー

安全な領域表示ウィジェットは、丸みを帯びた画面のコーナーやノッチの後ろなど、不要な領域でコンテンツがレンダリングされることを防ぎます。 このウィジェットはiOSアプリでのみサポートされています。 `コンテナ` のスタイリングは、安全なエリアにのみ適用されることに注意してください。

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>コンテンツ</container>
```

| 要素     | スタイルのプロパティ                     | 説明 |
| ------ | ------------------------------ | -- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |    |

The default class to style all safe area views is named `com_mendix_widget_native_safeareaview_SafeAreaView`.

### 11.15 スライダー

スライダーウィジェットでは、スライダーを使って数値を変更できます。 これは、スライダーウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="300" %}}![slider](attachments/native-styling-refguide/slider.png){{% /image_container %}}

このウィジェットは上記の \[range-slider\] (#range-slider) ウィジェットと同じスタイルプロパティをサポートしています。

すべてのスライダー入力をスタイル付けするデフォルトのクラスは、 `com_mendix_widget_native_slider_Slider` という名前です。

### 11.16 評価

レーティングウィジェットでは、0 から 5 までのオブジェクトを評価できます。 これはアプリで評価ウィジェットがどのように見えるかです。

{{% image_container width="350" %}}![ratings](attachments/native-styling-refguide/ratings.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <icon/><icon/><icon/><icon/><icon/>
</container>

<containerDisabled>
    <icon/><icon/><icon/><icon/><icon/>
</containerDisabled>
```

| 要素                  | スタイルのプロパティ                     | 説明          |
| ------------------- | ------------------------------ | ----------- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |             |
| `containerDisabled` | これにはすべての ViewStyle プロパティがあります。 |             |
| `アイコン`              | これにはすべての ViewStyle プロパティがあります。 |             |
| `アイコン`              | `サイズ`                          | アイコンのサイズ。   |
| `アイコン`              | `色`                            | アイコンの色。     |
| `アイコン`              | `selectedColor`                | 選択時のアイコンの色。 |

すべてのレーティング入力をスタイル付けするデフォルトのクラスは `com_mendix_widget_native_rating_Rating_Rating` という名前です。

### 11.17 ボタンの切り替え

トグルボタンウィジェットでは、列挙属性を設定できます。 これは、トグルボタンウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="350" %}}![toggle buttons](attachments/native-styling-refguide/toggle-buttons.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <button><text>Standard</text></button>
    <activeButton><activeButtonText>Sattelite</activeButtonText></activeButton>
    <button><text>Hybrid</text></button>
    <validationMessage/>
</container>

<containerDisabled>
    <button><text>Standard</text></button>
    <activeButton><activeButtonText>Sattelite</activeButtonText></activeButton>
    <button><text>Hybrid</text></button>
    <validationMessage/>
</containerDisabled>
```

| 要素                  | スタイルのプロパティ                     | 説明 |
| ------------------- | ------------------------------ | -- |
| `コンテナ`              | これにはすべての ViewStyle プロパティがあります。 |    |
| `containerDisabled` | これにはすべての ViewStyle プロパティがあります。 |    |
| `ボタン`               | これにはすべての ViewStyle プロパティがあります。 |    |
| `テキスト`              | これにはすべての TextStyle プロパティがあります。 |    |
| `アクティブボタン`          | これにはすべての ViewStyle プロパティがあります。 |    |
| `activeButtonText`  | これにはすべての TextStyle プロパティがあります。 |    |
| `validationMessage` | これにはすべての TextStyle プロパティがあります。 |    |

The default class to style all toggle buttons is named `com_mendix_widget_native_togglebuttons_ToggleButtons`.

### 11.18 ビデオプレーヤー

ビデオプレーヤーウィジェットを使用すると、URLに基づいてビデオを再生でき、MP4のみに制限されます。 これは、ビデオプレーヤーウィジェットがアプリ内でどのように見えるかです。

{{% image_container width="300" %}}![video player](attachments/native-styling-refguide/video-player.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

| 要素             | スタイルのプロパティ                     | 説明             |
| -------------- | ------------------------------ | -------------- |
| `コンテナ`         | これにはすべての ViewStyle プロパティがあります。 |                |
| `インジケーター：`     | `色`                            | 読み込みインジケーターの色。 |
| `ビデオ`          | これにはすべての ViewStyle プロパティがあります。 |                |
| `errorMessage` | これにはすべての TextStyle プロパティがあります。 |                |

すべてのビデオプレーヤーをスタイル付けするデフォルトのクラスは `com_mendix_widget_native_videoplayer_VideoPlayer` という名前です。

### 11.19 ウェブビュー

Web ビューウィジェットを使用すると、静的または動的な Web サイトをアプリケーションに埋め込むことができます。 ウィジェットのスタイルプロパティは以下の通りです:

| 要素               | スタイルのプロパティ                     | 説明 |
| ---------------- | ------------------------------ | -- |
| `コンテナ`           | これにはすべての ViewStyle プロパティがあります。 |    |
| `errorContainer` | これにはすべての ViewStyle プロパティがあります。 |    |
| `errorText`      | これにはすべての TextStyle プロパティがあります。 |    |

すべての Web ビューをスタイル化するデフォルトのクラスは `com_mendix_widget_native_webview_WebView` という名前です。

### 11.20 アニメーション

アニメーションウィジェットを使用すると、コンテナをアニメーション化できます。 コンテンツを揺らしたり、移動したり、サイズを変更したりすることができます。

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    {content}
</container>
```

| 要素     | スタイルのプロパティ                     | 説明 |
| ------ | ------------------------------ | -- |
| `コンテナ` | これにはすべての ViewStyle プロパティがあります。 |    |

The default class to style all animation widgets is named `com_mendix_widget_native_animation_Animation`.

### 11.21 紹介画面

この導入画面ウィジェットには、スワイプできるページ付けされたコンテンツが表示され、続行または戻る各ページのボタンが表示されます。

{{% image_container width="350" %}}![intro screen](attachments/native-styling-refguide/intro-screen.gif){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<fullscreenContainer>
    content
    <paginationContainer>
        <dotStyle/><activeDotStyle/><dotStyle/>
    </paginationContainer>
    <paginationAbove.buttonsContainer>
        <buttonSkip.container>
            <icon/><caption>Skip</caption>
        </buttonSkip.container>
        <buttonPrevious.container>
            <icon/><caption>Back</caption>
        </buttonPrevious.container>
        <buttonNext.container>
            <icon/><caption>Next</caption>
        </buttonNext.container>
        <buttonDone.container>
            <icon/><caption>Done</caption>
        </buttonDone.container>
    </paginationAbove.buttonsContainer>
</fullscreenContainer>

<popupContainer>
    content
    <paginationBetween>
        <buttonSkip.container>
            <icon/><caption>Skip</caption>
        </buttonSkip.container>
        <buttonPrevious.container>
            <icon/><caption>Back</caption>
        </buttonPrevious.container>
        <paginationContainer>
            <paginationText>4 / 5</paginationText>
        </paginationContainer>
        <buttonNext.container>
            <icon/><caption>Next</caption>
        </buttonNext.container>
        <buttonDone.container>
            <icon/><caption>Done</caption>
        </buttonDone.container>
    </paginationBetween>
</popupContainer>
```

| 要素                    | スタイルのプロパティ                     | 説明                                                               |
| --------------------- | ------------------------------ | ---------------------------------------------------------------- |
| `fullscreenContainer` | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `popupContainer`      | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `paginationContainer` | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `paginationText`      | これにはすべての TextStyle プロパティがあります。 |                                                                  |
| `dotStyle`            | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `activeDotStyle`      | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `buttonsContainer`    | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `コンテナ`                | これにはすべての ViewStyle プロパティがあります。 | Meant for buttonSkip, buttonDone, buttonPrevious and buttonNext. |
| `図表番号`                | これにはすべての ViewStyle プロパティがあります。 |                                                                  |
| `アイコン`                | `サイズ`                          | アイコンのサイズ。                                                        |
| `アイコン`                | `色`                            | アイコンの色。                                                          |

全てをスクリーンウィジェットにスタイル付けするデフォルトクラスは、 `com_mendix_widget_native_animation_Animation` という名前です。

### 11.22 リスト表示スワイプ

リストビューのスワイプウィジェットは、リストアイテムの背景にスワイプジェスチャーと追加ボタンを追加することで、リストビューをインタラクティブにすることができます:

{{% image_container width="350" %}}![list view swipe](attachments/native-styling-refguide/list-view-swipe-buttons.gif){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container>
    <leftAction>
        {Left background}
    </leftAction>
    {Foreground}
    <rightAction>
        {Right background}
    </rightAction>
</container>
```

| 要素            | スタイルのプロパティ                     | 説明                           |
| ------------- | ------------------------------ | ---------------------------- |
| `コンテナ`        | これにはすべての ViewStyle プロパティがあります。 |                              |
| `leftAction`  | これにはすべての ViewStyle プロパティがあります。 |                              |
| `leftAction`  | `panelSize`                    | バックグラウンドボタンのピクセル数とサイズの組み合わせ。 |
| `leftAction`  | `しきい値`                         | スワイプアクションを許可するピクセル数。         |
| `rightAction` | これにはすべての ViewStyle プロパティがあります。 |                              |
| `rightAction` | `panelSize`                    | バックグラウンドボタンのピクセル数とサイズの組み合わせ。 |
| `rightAction` | `しきい値`                         | スワイプアクションを許可するピクセル数。         |

全てのアニメーションウィジェットをスタイル付けするデフォルトのクラスは `com_mendix_widget_native_listviewswipe_ListViewSwipe` という名前です。

### 11.23 下シート

下部のシートウィジェットは、画面の残りの部分または画面の下部に固定されているドラッグ可能なサーフェスとの相互作用をブロックしながら、オプションのセットを作成します。 カスタマイズ可能なバリエーションが2つあります。

* モーダルボトムシート:

    {{% image_container width="350" %}}![modal bottom sheet](attachments/native-styling-refguide/modal-bottom-sheet.gif){{% /image_container %}}

* 下部シートを拡大中:

    {{% image_container width="350" %}}![expanding bottom sheet](attachments/native-styling-refguide/expanding-bottom-sheet.gif){{% /image_container %}}

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container />
<containerWhenExpandedFullscreen />
<modal />
<modalItems>
    <defaultStyle />
    <primaryStyle />
    <dangerStyle />
    <customStyle />
</modalItems>
```

| 要素                                | スタイルのプロパティ                     | 説明                                              |
| --------------------------------- | ------------------------------ | ----------------------------------------------- |
| `コンテナ`                            | これにはすべての ViewStyle プロパティがあります。 |                                                 |
| `containerWhenExpandedFullscreen` | これにはすべての ViewStyle プロパティがあります。 | `Expading` と `Enable full screen` が有効な場合のみ有効です。 |
| `モーダル（モーダル）`                      | これにはすべての ViewStyle プロパティがあります。 |                                                 |
| `defaultStyle`                    | これにはすべての TextStyle プロパティがあります。 | 基本アイテムのスタイルとして `デフォルト` が選択されている場合に利用できます。       |
| `primaryStyle`                    | これにはすべての TextStyle プロパティがあります。 | 基本アイテムのスタイルとして `Primary` が選択されている場合に利用できます。     |
| `dangStyle`                       | これにはすべての TextStyle プロパティがあります。 | 基本アイテムのスタイルとして `危険` が選択された場合に利用できます。            |
| `customStyle`                     | これにはすべての TextStyle プロパティがあります。 | 基本アイテムのスタイルとして `カスタム` が選択されている場合に利用できます。        |

下部のすべてのウィジェットをスタイル化するデフォルトのクラスは、 `com_mendix_widget_native_bottomsheet_Bottomsheet` という名前です。

### 11.24 Popup Menu

ポップアップ メニュー ウィジェットでは、ユーザーがタップした場所にコンテキスト メニューを表示できます。

ウィジェットのスタイルプロパティは以下の通りです:

```xml
<container/>
<buttonContainer/>
<custom>
    <containerStyle/>
    <itemStyle>
        </rippleColor>
    </itemStyle>
</custom>
<basic>
    <containerStyle/>
    <dividerColor/>
    <itemStyle>
        <ellipsizeMode/>
    </rippleColor>
        <defaultStyle/>
        <primaryStyle/>
        <dangerStyle/>
        <customStyle/>
    </itemStyle>
<basic/>
```

メインオブジェクトには4つのオブジェクトがあります。

| 要素              | スタイルのプロパティ                     | 説明                                                        |
| --------------- | ------------------------------ | --------------------------------------------------------- |
| 基本              | BasicItemStyle                 | 基本アイテムをスタイル化します。                                          |
| カスタム            | CustomItemStyle                | スタイルカスタムアイテム。                                             |
| buttonContainer | これにはすべての ViewStyle プロパティがあります。 | 複数の要素が存在する可能性があるため、トリガーのラッパービューをスタイルします。ビューにラップする必要があります。 |
| コンテナ            | これにはすべての ViewStyle プロパティがあります。 | メニュー全体のラッパービューをスタイル化します。                                  |

#### BasicItemStyle

| 要素             | スタイルのプロパティ                     | 説明                          |
| -------------- | ------------------------------ | --------------------------- |
| containerStyle | これにはすべての ViewStyle プロパティがあります。 | 基本アイテムを囲むラッパーコンテナをスタイル化します。 |
| アイテムスタイル       | アイテムスタイル                       | 基本アイテムをスタイル化します。            |
| DividerColor   | `文字列`                          | 区切り線の色をスタイル化します。            |

#### アイテムスタイル

| 要素            | スタイルのプロパティ                     | 説明                                                                  |
| ------------- | ------------------------------ | ------------------------------------------------------------------- |
| ellipsizeMode | `ヘッド`, `中央`, `テール`, または `クリップ` | テキストが長すぎるとクリップされるスタイルを設定します。                                        |
| rippleColor   | `文字列`                          | アイテムがタップされたときのタッチフィードバックの色をスタイル化します。 iOSとAndroidの両方のプラットフォームで動作します。 |
| defaultStyle  | これにはすべての TextStyle プロパティがあります。 | `デフォルト` スタイルが選択されているすべての基本メニューアイテムをスタイル化します。                        |
| primaryStyle  | これにはすべての TextStyle プロパティがあります。 | `primary` スタイルが選択されているすべての基本メニューアイテムをスタイル化します。                      |
| dangStyle     | これにはすべての TextStyle プロパティがあります。 | `危険` スタイルが選択されているすべての基本メニューアイテムをスタイル化します。                           |
| customStyle   | これにはすべての TextStyle プロパティがあります。 | `カスタム` スタイルが選択されているすべての基本メニューアイテムをスタイル化します。                         |


#### CustomItemStyle

| 要素             | スタイルのプロパティ                     | 説明                                                                  |
| -------------- | ------------------------------ | ------------------------------------------------------------------- |
| containerStyle | これにはすべての ViewStyle プロパティがあります。 | カスタム項目を囲むラッパーコンテナをスタイルします。                                          |
| アイテムスタイル       | `rippleColor: string`          | アイテムがタップされたときのタッチフィードバックの色をスタイル化します。 iOSとAndroidの両方のプラットフォームで動作します。 |
| DividerColor   | `文字列`                          | 区切り線の色をスタイル化します。                                                    |

全てのポップアップメニューをスタイル化するためのデフォルトのクラスは、 `com_mendix_widget_native_popupmenu_PopupMenu` という名前です。

### 11.25 Carousel

カルーセルウィジェットでは、カルーセルにスワイプ可能なアイテムを表示できます。

ウィジェットのスタイルプロパティは以下の通りです:

```xml
</container>
<cardLayout>
    </slideItem>
    </inactiveSlideItem>
    </indicator>
    <pagination>
        </container>
        </dotStyle>
        </inactiveDotStyle>
        </dotContainerStyle>
        </text>
    </pagination>
</cardLayout>
<fullWidthLayout>
    </slideItem>
    </inactiveSlideItem>
    </indicator>
    <pagination>
        </container>
        </dotStyle>
        </inactiveDotStyle>
        </dotContainerStyle>
        </text>
    </pagination>
</fullWidthLayout>
```

メインオブジェクトには、 `コンテナ`、 `cardLayout`、および `fullWidthLayout` という3つのオブジェクトが必要です。 `cardLayout` と `fullWidthLayout` は、ウィジェットのプロパティで選択されたレイアウトに応じて自動的に適用されます。

```
export myCarouselStyle = {
    container: ViewStyle //
    cardLayout: ...LayoutStyle,
    fullWidthLayout: ...LayoutStyle
}
```

| 要素              | スタイルのプロパティ                     | 説明                                                      |
| --------------- | ------------------------------ | ------------------------------------------------------- |
| コンテナ            | これにはすべての ViewStyle プロパティがあります。 | カルーセルウィジェットを囲むビューをスタイル化します。 最良の結果を得るには、 `高さ` を固定してください。 |
| cardLayout      | レイアウトスタイル                      | レイアウトがカードに設定されている場合のカルーセルのスタイル                          |
| fullWidthLayout | レイアウトスタイル                      | レイアウトが最大幅に設定されている場合にカルーセルをスタイルします。                      |

#### レイアウトスタイル

| 要素                | スタイルのプロパティ                     | 説明                                                                             |
| ----------------- | ------------------------------ | ------------------------------------------------------------------------------ |
| slideItem         | これにはすべての ViewStyle プロパティがあります。 | 非アクティブなスライドを含む各スライドを囲むビューをスタイル化します。                                            |
| inactiveSlideItem | `不透明度: 数, スケール: 数値`            | `inactiveSlideOpacity` と `inactiveSlideScale`は、非アクティブなスライドを小さくしてフェードできるようにします。 |
| インジケーター：          | `color: string`                | カルーセルの読み込み中に表示される読み込みインジケータをスタイル化します。                                          |
| pagination        | 改ページ                           | スタイルページネーションコンテナ、ドット、アクティブなドット、テキスト。                                           |

#### 改ページ

| 要素                | スタイルのプロパティ                                        | 説明                                                                 |
| ----------------- | ------------------------------------------------- | ------------------------------------------------------------------ |
| コンテナ              | これにはすべての ViewStyle プロパティがあります。                    | テキストやドットに関係なく、ページネーションを中心としたメインビューをスタイル化します。                       |
| dotStyle          | すべての ViewStyle プロパティ + `color: string`            | すべてのページネーションドットをスタイル化します。                                          |
| inactiveDotStyle  | すべての ViewStyle プロパティ + `不透明度: 数; スケール: 数; 色: 文字列` | 無効なドットの追加スタイルです。 `dotStyle` とマージされます。                              |
| dotContainerStyle | これにはすべての ViewStyle プロパティがあります。                    | ページネーションドットの周りのビューをスタイル化します。                                       |
| テキスト              | これにはすべての TextStyle プロパティがあります。                    | カルーセルに5つ以上の要素がある場合に適用されます。その場合、ページネーションボタンは **1/5** のようなテキストになります。 |

全てのポップアップメニューをスタイル付けするデフォルトのクラスは、 `com_mendix_widget_native_caroussel_カルーセル` という名前です。

### 11.26 署名 {#signature}

format@@0 ウィジェットでは、署名を描画して保存できます。 署名ウィジェットは以下のようになります:

{{% image_container width="350" %}}![signature](attachments/native-styling-refguide/signature.png){{% /image_container %}}

ウィジェットのスタイルプロパティは以下のように構成されています:

```xml
<container>
    <signature/>
    <buttonWrapper>
        <Button>
            <Caption>Clear</Caption>
        </Button>
        <Button>
            <Caption>Save</Caption>
        </Button>
    </buttonWrapper>
</container>
```

| 要素                     | スタイルのプロパティ                     | 説明                                      |
| ---------------------- | ------------------------------ | --------------------------------------- |
| `コンテナ`                 | これにはすべての ViewStyle プロパティがあります。 |                                         |
| `コンテナ`                 | `penColor`                     | これはストロークの色を変更します。                       |
| `buttonWrapper`        | これにはすべての ViewStyle プロパティがあります。 |                                         |
| `buttonClearContainer` | これにはすべての ViewStyle プロパティがあります。 |                                         |
| `buttonClearContainer` | `rippleColor`                  | これは、Androidのリップルの色を変更します。               |
| `buttonClearContainer` | `activeOpacity`                | iOS でタッチが有効な場合、不透明度が変更されます。             |
| `buttonClearContainer` | `underlayColor`                | タッチが iOS でアクティブになっている場合、アンダーレイの色が変わります。 |
| `ボタンClearCaption`      | これにはすべての TextStyle プロパティがあります。 |                                         |
| `SaveContainer`        | これにはすべての ViewStyle プロパティがあります。 |                                         |
| `SaveContainer`        | `rippleColor`                  | これは、Androidのリップルの色を変更します。               |
| `SaveContainer`        | `activeOpacity`                | iOS でタッチが有効な場合、不透明度が変更されます。             |
| `SaveContainer`        | `underlayColor`                | タッチが iOS でアクティブになっている場合、アンダーレイの色が変わります。 |
| `buttonSaveCaption`    | これにはすべての TextStyle プロパティがあります。 |                                         |

すべてのテキストボックスにスタイルを設定するデフォルトのクラスは、 `com_mendix_widget_native_signature_Signature_Signature` という名前です。

### 11.27 折れ線

[ライン チャート](https://github.com/mendix/widgets-resources/blob/master/packages/pluggableWidgets/line-chart-native) ウィジェットは、静的および動的なデータセットに基づいてスケーラブルなライン グラフをレンダリングします。

ウィジェットは次の要素で構成されています。

```xml
<container/>
<errorMessage/>
<chart/>
<grid/>
<xAxis>
    <label/>
</xAxis>
<yAxis>
    <label/>
</yAxis>
<legend>
    <container/>
    <item/>
    <indicator/>
    <label/>
</legend>
<lines>
    <customLineStyles>
        <any_custom_line_style_name>
            <line/>
            <markers/>
        </any_custom_line_style_name>
    </customLineStyles>
</lines>
<lineColorPalette/>
```

| 要素                                                                  | スタイルのプロパティ                                                             | 説明                                                                                                                                      |
| ------------------------------------------------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `コンテナ`                                                              | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `errorMessage`                                                      | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `グラフ`                                                               | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `グリッド`                                                              | `backgroundColor`                                                      | グリッドの背景 (文字列) に色を適用します。                                                                                                                 |
| `グリッド`                                                              | `dashArray`                                                            | グリッド線( [ダッシュパターン](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) を含む文字列)にダッシュとギャップのパターンを適用します。                      |
| `グリッド`                                                              | `lineColor`                                                            | グリッド ライン (文字列) に色を適用します。                                                                                                                |
| `グリッド`                                                              | `lineWidth`                                                            | グリッド線 (数値) に幅を適用します。                                                                                                                    |
| `グリッド`                                                              | `padding`                                                              | グリッドのすべての辺(数)にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                         |
| `グリッド`                                                              | `paddingBottom`                                                        | グリッドの下側(数値)にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                           |
| `グリッド`                                                              | `水平方向にpaddingHorizontal`                                               | グリッドの水平方向(数値)にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                         |
| `グリッド`                                                              | `paddingLeft`                                                          | グリッドの左側(数値)にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                           |
| `グリッド`                                                              | `paddingRight`                                                         | グリッド(数値)の右側にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                           |
| `グリッド`                                                              | `paddingTop`                                                           | グリッド(数値)の上側にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                           |
| `グリッド`                                                              | `paddingVertical`                                                      | グリッドの垂直辺(数字)にパディングを適用します。 軸の値ラベルを表示するために使用します。                                                                                          |
| `xAxis`                                                             | `色`                                                                    | 軸の値 ラベル (文字列) に色を適用します。                                                                                                                 |
| `xAxis`                                                             | `dashArray`                                                            | 軸線にダッシュとギャップのパターンを適用します( [ダッシュパターン](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) を含む文字列)。                         |
| `xAxis`                                                             | `fontFamily`                                                           | 軸値ラベル (文字列) にフォントを適用します。                                                                                                                |
| `xAxis`                                                             | `fontSize`                                                             | 軸の値ラベル (数値) にサイズを適用します。                                                                                                                 |
| `xAxis`                                                             | `fontStyle`                                                            | 軸の値ラベル ("normal" または "italic") にフォントスタイルを適用します。                                                                                         |
| `xAxis`                                                             | `fontWeight`                                                           | 軸の値のラベル ("normal" または "bold" または "100" または "200" または "300" または "400" または "500" または "600" または "700" または "800" または "900") にフォントの重みを適用します。 |
| `xAxis`                                                             | `lineColor`                                                            | 軸線 (文字列) に色を適用します。                                                                                                                      |
| `xAxis`                                                             | `lineWidth`                                                            | 軸線 (数値) に幅を適用します。                                                                                                                       |
| `xAxis` > `label`                                                   | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `xAxis` > `label`                                                   | `relativePositionGrid`                                                 | 軸ラベルをグリッドの一番下または右側に配置します(「下」または「右」)。                                                                                                    |
| `yAxis`                                                             | すべての `xAxis` 要素スタイル。                                                   |                                                                                                                                         |
| `yAxis` > `label`                                                   | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `yAxis` > `label`                                                   | `relativePositionGrid`                                                 | 軸ラベルをグリッドの上部または左側に配置します(「上」または「左」)。                                                                                                     |
| `legend` > `container`                                              | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `legend` > `item`                                                   | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `legend` > `indicator`                                              | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `legend` > `label`                                                  | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `行`                                                                 | `lineColorPalette`                                                     | 線の色が設定されていない行に色を提供します (文字列の色のリストは ';' で区切られた文字列)。                                                                                       |
| `line` > `customLineStyles` > `any_custom_line_style_name` > `line` | `dashArray`                                                            | ダッシュとギャップのパターンをグラフ線に適用します( [ダッシュパターン](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) を含む文字列)。                       |
| `line` > `customLineStyles` > `any_custom_line_style_name` > `line` | `終了`                                                                   | グラフ線(「フラット」または「ラウンド」)にフラットまたは丸められた線の端を適用します。                                                                                            |
| `line` > `customLineStyles` > `any_custom_line_style_name` > `line` | `lineColor`                                                            | グラフの線 (文字列) に色を適用します。                                                                                                                   |
| `line` > `customLineStyles` > `any_custom_line_style_name` > `line` | `lineWidth`                                                            | グラフの線(数値)に幅を適用します。                                                                                                                      |
| `行` > `customLineStyles` > `any_custom_line_style_name` > `マーカー`    | `backgroundColor`                                                      | グラフ線(文字列)のマーカーに背景色を適用します。                                                                                                               |
| `行` > `customLineStyles` > `any_custom_line_style_name` > `マーカー`    | `borderColor`                                                          | グラフ線(文字列)のマーカーに境界線の色を適用します。                                                                                                             |
| `行` > `customLineStyles` > `any_custom_line_style_name` > `マーカー`    | `borderWidth`                                                          | グラフ線(文字列)のマーカーに外枠の幅を適用します。                                                                                                              |
| `行` > `customLineStyles` > `any_custom_line_style_name` > `マーカー`    | `display`                                                              | マーカーが表示されるかどうかに影響します。 表示されると、グラフの線のマーカーを行の上下に配置します(「false」または「下」または「onTop」)。                                                            |
| `行` > `customLineStyles` > `any_custom_line_style_name` > `マーカー`    | `サイズ`                                                                  | グラフ線(数字)のマーカーにサイズを適用します。                                                                                                                |
| `行` > `customLineStyles` > `any_custom_line_style_name` > `マーカー`    | `シンボル`                                                                 | グラフ線のマーカーにシンボルを適用します(「円」または「ダイヤモンド」または「プラス」または「マイナス」または「正方形」または「星」または「三角形」または「三角形」)。                                                    |

すべての折れ線グラフウィジェットをスタイル化するデフォルトのクラスは、 `com_mendix_widget_native_linechart_LineChart` という名前です。

### 11.28 棒グラフ

棒グラフウィジェットは、静的および動的なデータセットに基づいて水平方向の棒グラフをレンダリングします。

ウィジェットは次の要素で構成されています。

```xml
<container/>
<errorMessage/>
<chart/>
<grid/>
<xAxis>
    <label/>
</xAxis>
<yAxis>
    <label/>
</yAxis>
<legend>
    <container/>
    <item/>
    <indicator/>
    <label/>
</legend>
<domain>
    </padding>
</domain>
<bars>
    </barsOffset>
    </barColorPalette>
    <customBarStyles>
        <any_custom_bar_style_name>
            </bar>
            </label>
        </any_custom_bar_style_name>
    </customBarStyles>
</bars>
```

| 要素                                                                 | スタイルのプロパティ                                                             | 説明                                                                                                                                      |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `コンテナ`                                                             | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `errorMessage`                                                     | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `グラフ`                                                              | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `グリッド`                                                             | `backgroundColor`                                                      | グリッドの背景 (文字列) に色を適用します。                                                                                                                 |
| `グリッド`                                                             | `dashArray`                                                            | グリッド線( [ダッシュパターン](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) を含む文字列)にダッシュとギャップのパターンを適用します。                      |
| `グリッド`                                                             | `lineColor`                                                            | グリッド ライン (文字列) に色を適用します。                                                                                                                |
| `グリッド`                                                             | `width`                                                                | グリッド線 (数値) に幅を適用します。                                                                                                                    |
| `グリッド`                                                             | `padding`                                                              | グリッドのすべての辺(数)にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                          |
| `グリッド`                                                             | `paddingBottom`                                                        | グリッドの下側(数値)にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                            |
| `グリッド`                                                             | `水平方向にpaddingHorizontal`                                               | グリッドの水平方向(数値)にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                          |
| `グリッド`                                                             | `paddingLeft`                                                          | グリッドの左側(数値)にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                            |
| `グリッド`                                                             | `paddingRight`                                                         | グリッド(数値)の右側にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                            |
| `グリッド`                                                             | `paddingTop`                                                           | グリッド(数値)の上側にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                            |
| `グリッド`                                                             | `paddingVertical`                                                      | グリッドの垂直辺(数字)にパディングを適用します。 これにより軸の値ラベルが表示されます。                                                                                           |
| `xAxis`                                                            | `色`                                                                    | 軸の値 ラベル (文字列) に色を適用します。                                                                                                                 |
| `xAxis`                                                            | `dashArray`                                                            | 軸線にダッシュとギャップのパターンを適用します( [ダッシュパターン](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) を含む文字列)。                         |
| `xAxis`                                                            | `fontFamily`                                                           | 軸値ラベル (文字列) にフォントタイプを適用します。                                                                                                             |
| `xAxis`                                                            | `fontSize`                                                             | 軸の値ラベル (数値) にサイズを適用します。                                                                                                                 |
| `xAxis`                                                            | `fontStyle`                                                            | 軸の値ラベル ("normal" または "italic") にフォントスタイルを適用します。                                                                                         |
| `xAxis`                                                            | `fontWeight`                                                           | 軸の値のラベル ("normal" または "bold" または "100" または "200" または "300" または "400" または "500" または "600" または "700" または "800" または "900") にフォントの重みを適用します。 |
| `xAxis`                                                            | `lineColor`                                                            | 軸線 (文字列) に色を適用します。                                                                                                                      |
| `xAxis`                                                            | `lineWidth`                                                            | 軸線 (数値) に幅を適用します。                                                                                                                       |
| `xAxis` > `label`                                                  | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `xAxis` > `label`                                                  | `relativePositionGrid`                                                 | グリッドの **下部** または **右側** に軸ラベルを配置します。                                                                                                    |
| `yAxis`                                                            | すべての `xAxis` 要素スタイル。                                                   |                                                                                                                                         |
| `yAxis` > `label`                                                  | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `yAxis` > `label`                                                  | `relativePositionGrid`                                                 | グリッドの **上部** または **左側** に軸ラベルを配置します。                                                                                                    |
| `legend` > `container`                                             | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `legend` > `item`                                                  | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `legend` > `indicator`                                             | すべての [ViewStyle](https://reactnative.dev/docs/view-style-props) プロパティ。 |                                                                                                                                         |
| `legend` > `label`                                                 | すべての [TextStyle](https://reactnative.dev/docs/text-style-props) プロパティ。 |                                                                                                                                         |
| `domain` > `padding`                                               | `x`                                                                    | X 軸ドメイン (数値) の始まりと終わりを追加するために、パディングの数のピクセルを適用します。                                                                                       |
| `domain` > `padding`                                               | `y`                                                                    | Y 軸ドメイン (数値) の始まりと終わりを追加するために、パディングのピクセル数を適用します。                                                                                        |
| `バー`                                                               | `barColorPalette`                                                      | バーの色が設定されていないバーに色を提供します(文字列の色のリストは ';' で区切られています)。                                                                                      |
| `バー`                                                               | `barsOffset`                                                           | グループ内の各バーのピクセル数を、Y軸上の元の位置(数値)からオフセットするよう指定します。 これはプレゼンテーションモードが **グループ** の場合にのみ適用できます。                                                  |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `bar`   | `終了`                                                                   | 各バーに適用する半径を指定します。                                                                                                                       |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `bar`   | `色`                                                                    | バー (文字列) に色を適用します。 バーにラベルが設定されている場合、ラベルはバーと同じ色になります。                                                                                    |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `bar`   | `width`                                                                | 小節(数字)に幅を適用します。                                                                                                                         |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `fontFamily`                                                           | バーラベル (文字列) にフォントの種類を適用します。                                                                                                             |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `fontSize`                                                             | 小節ラベル (数値) にサイズを適用します。                                                                                                                  |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `fontStyle`                                                            | バーラベル (**標準** または **イタリック** ) にフォントスタイルを適用します。                                                                                          |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `fontWeight`                                                           | フォントの重みを小節ラベル ("normal" または "bold" または "100" または "200" または "300" または "400" または "500" または "600" または "700" または "800" または "900") に適用します。   |

すべての棒グラフウィジェットをスタイル化するデフォルトのクラスは、 `com_mendix_widget_native_barchart_BarChart` という名前です。

## 12 続きを読む

* [Mendixネイティブモバイルアプリのスタイル設定](/howto/mobile/how-to-use-native-styling)
* [ネイティブモバイルスタイルの実装方法](/howto/mobile/native-styling)
* [デザインプロパティドキュメント](/apidocs-mxsdk/apidocs/design-properties)
