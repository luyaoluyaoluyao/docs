---
title: "クライアントの状態の監視"
category: "Mendix Runtime"
tags:
  - "studio pro"
---

## 1つの紹介

状態はクライアント(ウェブブラウザ)にあります。 これにより、サーバーを複数のインスタンスにスケーリングすることができます。 状態がクライアントに存在するため、状態内のものと、特定の時点でなぜかを監視するのに役立ちます。

これを行うには <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> キーの組み合わせを使用して、ブラウザーコンソールに状態をダンプします。 状態は JSON オブジェクトで表示され、エンティティタイプごとにグループ化されます。 エンティティが持続可能でない場合、これはサフィックス `[NPE]` で示されます。

{{% alert type="info" %}}
 <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> キーの組み合わせは、 [Parallels](/howto8/mobile/using-mendix-studio-pro-on-a-mac) 内の Mozilla Firefox を除くすべてのブラウザーで動作します。
{{% /alert %}}

## 2つの詳細

エンティティタイプごとに、状態にあるオブジェクトインスタンスの ID が表示されます。 各オブジェクトインスタンスには以下の情報が表示されます:

* オブジェクト ID の後のサフィックス `(新しい)` - オブジェクトが新しいか (オブジェクトがまだコミットされていない)
* オブジェクト ID の後のサフィックス `(変更された)` - オブジェクトが反映されていない変更があるかどうか (オブジェクトが以前に反映されているかどうか)
* プロパティ `の変更` – オブジェクトに存在する変更
* プロパティ `subscribedWidgets` – オブジェクトを使用しているウィジェット
    * The widget name is in the form of `Module.PageName.widgetName` (for example, `MyFirstModule.Entity_NewEdit.dataView1`), which allows you to quickly find the referenced widget in Studio Pro
* プロパティ `referencedBy` – このオブジェクトを参照するオブジェクト

`subscribedWidgets` と `referencedby` プロパティの両方が、オブジェクトがまだ状態にある理由を説明しています。 それらが両方とも空の場合は、「ガベージコレクションにする」というテキストが表示されます。
