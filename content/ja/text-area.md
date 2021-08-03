---
title: "テキストエリア"
parent: "input-widgets"
---


テキストエリアは、複数行に分割できる長いテキスト値を表示および/または編集するために使用できます。

{{% alert type="info" %}}

![](attachments/pages/text-area.png)

このテキストエリアでは、エンドユーザーが製品の説明を設定できます。

{{% /alert %}}

テキスト領域は、データビューまたはテンプレート グリッドに配置し、String 型の属性に接続する必要があります。 接続された属性は青色とテキスト領域内の括弧の間に表示されます。

## 一般プロパティ

### 自動的に拡大

このプロパティは、テキストの量に応じてテキスト領域が自動的に拡大するかどうかを定義します。

_デフォルト値:_ いいえ

### 行数

行数は、テキスト領域に同時に表示される行数を決定します。 テキストエリア内のテキストに複数の行が含まれている場合は、スクロールバーを使用してすべてを表示する必要があります。 このプロパティは、自動的に format@@0 が設定されている場合にのみ表示されます。

_デフォルト値:_ 5

### カウンターメッセージ

これは、テキストエリアに入力するときに表示されるテキストです。 このテキストには、2 つのプレースホルダがあります。 最初のプレースホルダにはすでに入力されている文字の数が表示され、2 番目のプレースホルダには文字の最大数が表示されます。

{{% alert type="info" %}}

許可されている {1} 文字の {2} 文字を使用しました。

{{% /alert %}}

### テキストが長すぎます

これは、入力された文字の数が最大文字数よりも大きい場合に表示されるテキストです。

### 最大長さ

このプロパティは、このテキストボックスに入力できる最大文字数を示します。

| 値     | 説明                       |
| ----- | ------------------------ |
| 属性の長さ | 最大文字数は、接続された属性の最大長と同じです。 |
| 無制限です | 最大文字数は無制限です。             |
| カスタム  | 最大文字数はユーザーによって設定されます。    |

_デフォルト値: 属性の長さ_

### プレースホルダーテキスト

テキストがまだ入力されていない場合、プレースホルダー テキストが表示されます。 ユーザーにどのようなテキストを入力すべきかのヒントを与えるために使用できます。

## バリデーションプロパティ

{{% snippet file="refguide7/Widget+Validation.md" %}}

## データソースのプロパティ

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguide7/Label+Property.md" %}}

## 編集可能なプロパティ

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## イベントのプロパティ

{{% snippet file="refguide7/On+Change+Event.md" %}}

{{% snippet file="refguide7/On+Enter+event.md" %}}

{{% snippet file="refguide7/On+Leave+Event.md" %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 続きを読む

*   [データビュー](data-view)
*   [属性](attributes)
