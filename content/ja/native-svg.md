---
title: "ベクターグラフィックスの操作"
parent: "native-Mobile"
menu_order: 80
description: "SVGsをネイティブモバイルアプリに統合する方法をご覧ください。"
tags:
  - "ネイティブ"
  - "svg"
  - "画像"
  - "モバイル"
  - "ベクトル"
  - "ベクトルグラフィックス"
---

## 1つの紹介

ネイティブのモバイルアプリケーションを構築する場合は、アイコンやその他のイラストにベクター画像を使用することができます。 この目的のために、Scalable Vector Graphics (SVGs) を使用できます。 このリファレンスガイドでは、ネイティブ モバイル アプリにおける SVG を扱うためのガイダンスを提供します。

## 2SVGの最適化 {#optimizing}

SVG をエディタからエクスポートする場合、いくつかの不要な要素を持つ SVG が生成されることがよくあります。 これらの要素はファイルサイズを増やし、パフォーマンスを低下させ、望ましくない副作用を引き起こす可能性があります。 したがって、SVG 最適化ツールを介して SVG を実行することをお勧めします。

SVGを最適化するには [SVGOMG](https://jakearchibald.github.io/svgomg/) などのオンラインツールを使用するか、 [SVGO](https://github.com/svg/svgo) などのローカルツールを使用することができます。

## 3 サポートされていない要素

SVGはいくつかの種類の要素を含むことができます。 ただし、すべてがネイティブモバイルアプリでサポートされているわけではありません。 サポートされていない要素には効果はなく、削除する必要があります。 The following SVG elements are *not* supported for native mobile apps:

* 複雑なグラデーション数
* アニメーション
* ビデオ
* JavaScript コード
* CDATA 要素
* `<style />` タグと `スタイル` 属性 (代わりに通常のプロパティを使用してください)

これらの要素を SVG から手動で削除するか、上記の [SVGの最適化](#optimizing) に記載されているツールを使用して互換性を確保することをお勧めします。

## 4 Styling SVGs

画像を追加する場合など、SVG 内で特定の色を変更することができます。 Mendix では、画像のスタイルで `fill` と `ストローク` プロパティを設定することでこれを行うことができます。 These properties will then be applied to *all* the elements inside the SVG that do not have these properties.

次の SVG を例として取ります。

```svg
<svg viewBox="0 0 100 100">
    <rect x="10" y="10" width="80" height="80" stroke="blue"/>
</svg>
```

この画像のスタイルに `fill` プロパティを設定すると、与えられた色に長方形(`direct` 要素)が変わります。 `ストローク` プロパティを設定すると、 `ストローク` が既に設定されているため、変更はありません。

次のように、 `プロパティを` に埋めないSVGがどのように見えるかを示します。

![前](attachments/native-svg/before.png)

次のように、SVG が `fill` プロパティでどのように見えるかを示します。

![後](attachments/native-svg/after.png)

許可されているスタイルのプロパティのリストは、 [react-native-svg](https://github.com/react-native-community/react-native-svg#common-props) リポジトリで確認できます。

### 4.1 SVGアイコンの色付け

アイコンは、ボタンと下部のバーアイテムにのみ設定できます。 SVGアイコンをボタンまたは下部のバーアイテムに統合する場合は、SVGの色を自分で設定する必要があります。 Atlas UIを採用しているアプリを使用する場合、デフォルトではすべて白色になります。 スタイリングの詳細については、 [Native Mobile Styling Reference Guide](/refguide/native-styling-refguide) を参照してください。

例えば、以下のコードです。

```jsx
export const DemoButton = {
    container: {
        backgroundColor: 'green'
    },
    caption: {
        color: 'orange'
    },
    icon: {
        color: 'blue'
    }
}
```

次のボタンとSVGを生成します:

![blue svg](attachments/native-svg/blue-svg.png)

## 5 Pluggable Native WidgetsでSVGを使用する

プラグイン可能なネイティブウィジェットの image プロパティで SVG を使用するには、指定された `Image` または `Icon` コンポーネントを使用することをお勧めします。 これにより、サポートされている任意のフォーマットの静的な画像を、SVGを含むpluggableウィジェットで使用することができます。

次に、 `イメージ` コンポーネントを使用した例を示します。

```jsx
import { createElement } from "react";
import { Image } from "mendix/components/native/Image";

export const PluggableWidget = () => (
    <Image source="PUT_SOURCE_HERE" style={{ fill: 'blue' }} />
);
```

以下は、 `アイコン` コンポーネントを使用した例です。

```jsx
import { createElement } from "react";
import { Icon } from "mendix/components/native/Icon";

export const PluggableWidget = () => (
    <Icon 
        icon={{
            type: "image",
            iconUrl: "PUT_SOURCE_HERE"
        }}
        size={20}
        color="blue"
    />
);
```

プラグイン可能なウィジェットで SVG 要素を直接使用したい場合は、 [react-native-svg](https://github.com/react-native-community/react-native-svg) ライブラリを参照してください。

## 5 続きを読む

* [Pluggable Native Widgetを作成する](/howto/extensibility/build-native-widget)
* [アトラスUI](/howto/front-end/atlas-ui)
* [Pluggable Widgets API](/apidocs-mxsdk/apidocs/pluggable-widgets)
