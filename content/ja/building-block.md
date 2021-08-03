---
title: "Building Block"
parent: "page-resources"
menu_order: 40
tags:
  - "studio pro"
  - "Building block"
  - "ページリソース"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/building-block.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

Building Blocksはページ作成プロセスを合理化するために再利用できるコンポーネントです。 構築ブロックの事前設定とスタイル設定により、ユーザーは、スタイリングガイドラインやユーザーエクスペリエンスの詳細を気にすることなく、インターフェイスを簡単にクリックできます。

Building Blocksはプロジェクトの [UIリソースパッケージ](ui-resources-package)に格納されます。 これにより、プロジェクトテーマと同期させることができ、デザイン関連のすべてのデータを統合するのに便利な場所が提供されます。

Building Blockを作成するには、Studio Proでプロジェクト内の任意の場所でウィジェットを右クリックし、 **Building Blockを作成** を選択します。 ウィジェットの内容とともに、新しいBuilding Blockとして追加されます。 Building Blockは **Toolbox** の **Building Blocks**タブに自動的に表示されます。

Building Blockの目的は、機能ではなく設計を容易にすることであるため、Building Blockは他の文書への参照を欠いている必要があります。 これは、ユーザーが自分のページにBuilding Blockを使用しているときに混乱してエラーに直面することを防ぐためです。 また、別のプロジェクトからBuilding Blockをインポートする際のエラーの可能性も軽減します。

## 2つの一般的なプロパティ

{{% snippet file="refguide8/comon-section-link.md" %}}

## デザイナープロパティ

{{% snippet file="refguide8/designer-properties.md" %}}

## 4つの一般プロパティ

### 4.1 表示名

表示名は、ツールボックスに表示されるBuilding Blockの名前を決定します。

### 4.2 画像

選択された画像は、Studio の **Toolbox** の **Building Blocks** タブに表示されます。 代表的な画像を選択すると、ユーザーはビルディングブロックを簡単に区別できます。 空白の場合、Studio は一般的なデフォルト画像を表示します。 選択された画像は200x200ピクセルに縮小されます。

### 4.3 ドキュメントURL

ドキュメント URL は、ビルド ブロックのドキュメント ページにリンクするために使用できます。 これらのリンクはStudioの **ツールボックス** の **Building Blocks**タブに表示されます。
