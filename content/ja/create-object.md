---
title: "オブジェクトを作成"
parent: "object-activity"
---

## 1つの紹介

オブジェクトの作成アクションは、オブジェクトの作成に使用できます。

{{% alert type="info" %}}

すべてのマイクロフローアクティビティが共有するプロパティ(図表など)については、 [Microflow Element Common Properties](microflow-element-common-properties) を参照してください。 このページでは、アクションに固有のプロパティのみを記述します。

{{% /alert %}}

## 2つのアクションプロパティ

### 2.1 エンティティ

オブジェクトを作成するエンティティ。

### 2.2 コミットの種類

**コミット タイプ** は、オブジェクトがコミットされる方法を定義します。

| Option        | 説明                                                            |
| ------------- | ------------------------------------------------------------- |
| イベントハンドラでははい  | オブジェクトがデータベースに保存され、 [イベントハンドラ](event-handlers) がトリガーされます。     |
| はい、イベントハンドラなし | オブジェクトはデータベースに保存されますが、 [イベントハンドラ](event-handlers) はトリガーされません。 |
| いいえ           | オブジェクトはデータベースに保存されずに変更されます。                                   |

{{% alert type="warning" %}}

Nanoflowはイベントなしでのコミット変更をサポートしていません。 オンラインアプリで実行中にコミットすると、Mendix Runtimeにコミットリクエストが送信され、イベントが実行されます。 オブジェクトの作成アクションがオフラインアプリで使用されている場合、変更はオフラインデータベースに反映されます。

{{% /alert %}}

_デフォルト値:_ いいえ

### 2.3 クライアントで更新

If the microflow is called from the client, [data sources](data-sources) do not reload, unless **Refresh in client** is set to *Yes*.

{{% alert type="warning" %}}

When inside a [nanoflow](nanoflows), the Create object action reloads [data sources](data-sources) as if Refresh in client was set to *Yes*.

{{% /alert %}}

_デフォルト値_: いいえ

### 2.3 メンバーを初期化する

新しく作成したオブジェクトのメンバーを初期化できます。 メンバーに対する値は [式](expressions) で指定され、メンバーと同じ型である必要があります。

## 3つの出力プロパティ

### 3.1 変数名

変数名は、生成されるオブジェクト変数の名前を定義します。 このアクティビティに続くすべてのアクティビティで使用できます。
