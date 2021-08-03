---
title: "テキストボックス"
parent: "input-widgets"
---


テキストボックスは、テキストの値を表示および/または編集するために使用できます。

{{% alert type="info" %}}

![](attachments/pages/text-box.png) このテキストボックスは、エンドユーザーが顧客の名前を設定できるようにします。

{{% /alert %}}

テキスト ボックスは、データ ビューまたはテンプレート グリッドに配置し、String 型の属性に接続する必要があります。 接続された属性は青色とテキストボックス内の括弧の間に表示されます。

## 一般プロパティ

{{% snippet file="refguide7/Numeric+Formatting+Properties.md" %}}

### パスワードとして表示 (文字列またはハッシュ文字列タイプの属性のみ)

| 値     | 説明                                                        |
| ----- | --------------------------------------------------------- |
| False | 標準テキスト ボックス                                               |
| True  | 型付けされた文字はエンドユーザーには表示されません。 代わりに、型付けされた文字ごとにアスタリスクが表示されます。 |

_デフォルト値:_ False

### 入力マスク (Webフォームのみ)

入力マスクは、ユーザーがテキストボックスに入力できるものを制限します。 「9」は任意の数字、「Z」は任意の文字、「U」は大文字、「L」は小文字、「*」は文字または数字を意味します。 他の文字は文字通り取られます。 たとえば、入力マスク99-LLL-9999は24-apr-2008に一致します。

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
