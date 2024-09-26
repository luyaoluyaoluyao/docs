---
title: "作成ボタン"
parent: "ボタン-ウィジェット"
---

{{% alert type="info" %}}

このボタンは Mendix 7.17 で削除されました。 [オブジェクトの作成](action-button) アクションを代わりに通常の **アクションボタン** を使用します。

{{% /alert %}}

ユーザーが **** ボタンを押した時。 Mendixアプリケーションは新しいオブジェクトを作成し、新しいオブジェクトを編集するページを開きます。

## ボタンのプロパティ

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguide7/Render+Mode+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

## 共通のプロパティ

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 一般プロパティ

### ページ

このプロパティは、エンドユーザーがこのボタンを押した時に開かれるページを指定します。 エンドユーザーは、このページを使用して、新しく作成されたオブジェクトを保存する前に編集できます。 このページには、このボタンと同じエンティティに接続されたデータビューが含まれている必要があります。

[ページを開く](opening-pages) を参照してください。

### エンティティ (パス)

ボタンをクリックしたときに作成するオブジェクトの種類を指定します。 データビュー内のオブジェクトへの関連付けを持つオブジェクト、または page パラメータとして渡されるオブジェクトを作成することができます。 関連付けは、新しいオブジェクトが作成されると自動的に設定されます。 1対1または1の多くの関連付けがサポートされています。

## 表示プロパティ

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Extended.md" %}}
