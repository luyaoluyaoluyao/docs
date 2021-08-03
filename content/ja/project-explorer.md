---
title: "アプリエクスプローラー"
parent: 表示メニュー
menu_order: 40
tags:
  - "studio pro"
  - "アプリエクスプローラー"
---

## 1つの紹介

**App Explorer** は、モジュール内のすべてのドキュメントを含むアプリケーションの完全な構造を表示します。

![](attachments/app-explorer/app-explorer.png)

**App Explorer** は以下で構成されています。

* **App** フォルダ – アプリ全体に適用される設定とドキュメントが含まれています (詳細は [アプリ](project) を参照してください)
* **Modules**  – contain settings, a domain model, and *documents* that apply to this module (for more information, see [Modules](modules))
  * **ドメインモデル** - アプリケーションが使用する情報 (または *データ*) を抽象的な方法で記述するモデル 一つのモジュールは一つのドメインモデルのみを持つことができます
  * **ドキュメント** – 個々のファイル、例えば、 [ページ](pages)、 [microflow](microflows)、または [スケジュールされたイベント](scheduled-events)。

## 2 基本機能の実行

**App Explorer**では、以下の操作ができます。

* **Filter** – enter the name of a module, folder, or document into the **Filter** field to filter documents of the app and highlight entered text within the **App Explorer**. モジュールまたはフォルダ名でフィルタリングすると、一致するモジュールおよび/またはフォルダのすべてのコンテンツが表示されます。 さらに、 **フィルター** フィールドにフォーカスしている間、次のようにすることができます。
  * **アプリエクスプローラ** を <kbd></kbd> と <kbd>伏線</kbd> キーで移動します
  * フォルダを展開するか、 <kbd>Enter キーを押してドキュメントを開きます</kbd>
  * <kbd>Esc</kbd> を押してフィルタークエリをクリアします
* **ドキュメントを開く** – ドキュメントをダブルクリックして開きます
* **アクティブなドキュメントを選択** – **App Explorer** の右上隅にあるアイコンをクリックして、 **App Explorer** ツリーでアクティブなドキュメントをすばやく表示します。 デフォルトでは、アクティブなドキュメントは常に選択されているため、編集するドキュメントの場所をすばやく確認できます。 この動作は、 **編集** > **環境設定** ダイアログボックスで変更できます。
* **すべてのドキュメントを展開する** - **App Explorer** の左上隅にあるプラスアイコンをクリックして、すべてのドキュメントを展開し、アプリの構造全体を確認します。
* **すべてのドキュメントを折りたたむ** – **App Explorer** の左上隅にあるマイナスのアイコンをクリックして、すべてのドキュメントを折りたたみます。
* **個々のフォルダを展開または折りたたむ** – 個々のフォルダ内のドキュメントを展開/折りたたむには、プラス/マイナスアイコンをクリックするか、フォルダをダブルクリックします。
* **選択したフォルダに固有のアクションを実行する** – 選択したフォルダを右クリックして、どのような機能を実行できるかを確認します。 The list of functions depends on the folder, for example, when right-clicking the **System** module, you can only find usages of this module, while when right-clicking **MyFirstModule** you can add a page, add a microflow, rename the module, export the module package, copy/paste documents, and much more.

## 3 続きを読む

* [アプリ](プロジェクト)
* [モジュール](モジュール)
* [セキュリティ](セキュリティ)
