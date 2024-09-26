---
title: "プロジェクトエクスプローラー"
parent: 表示メニュー
menu_order: 40
tags:
  - "studio pro"
  - "プロジェクトエクスプローラー"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/project-explorer.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**プロジェクト エクスプローラ** は、モジュール内のすべてのドキュメントを含むプロジェクトの完全な構造を表示します。

{{% image_container width="250" %}}![](attachments/project-explorer/project-explorer.png)
{{% /image_container %}}

**プロジェクト エクスプローラ** は、以下で構成されます。

* **プロジェクト** フォルダ - プロジェクト全体として適用される設定とドキュメントが含まれています (詳細は、 [プロジェクト](project) を参照してください)
* **Modules**  – contain settings, a domain model, and *documents* that apply to this module (for more information, see [Modules](modules))
  * **ドメインモデル** - アプリケーションが使用する情報 (または *データ*) を抽象的な方法で記述するモデル 一つのモジュールは一つのドメインモデルのみを持つことができます
  * **ドキュメント** – 個々のファイル、例えば、 [ページ](pages)、 [microflow](microflows)、または [スケジュールされたイベント](scheduled-events)。

## 2 基本機能の実行

**プロジェクト エクスプローラー**では、次の操作ができます。

* **Filter** – enter the name of a module, folder, or document into the **Filter** field to filter documents of the project and highlight entered text within the **Project Explorer**. モジュールまたはフォルダ名でフィルタリングすると、一致するモジュールおよび/またはフォルダのすべてのコンテンツが表示されます。 さらに、 **フィルター** フィールドにフォーカスしている間、次のようにすることができます。
  * **プロジェクトエクスプローラー** を <kbd></kbd> キーと <kbd>伏線</kbd> キーでナビゲートします
  * フォルダを展開するか、 <kbd>Enter キーを押してドキュメントを開きます</kbd>
  * <kbd>Esc</kbd> を押してフィルタークエリをクリアします
* **ドキュメントを開く** – ドキュメントをダブルクリックして開きます
* **アクティブなドキュメントを選択** – **プロジェクトエクスプローラー** の右上隅にあるアイコンをクリックすると、 **プロジェクトエクスプローラー** ツリーでアクティブなドキュメントをすばやく表示できます。 デフォルトでは、アクティブなドキュメントは常に選択されているため、編集するドキュメントの場所をすばやく確認できます。 この動作は、 **編集** > **環境設定** ダイアログボックスで変更できます。
* **すべてのドキュメントを展開する** - **プロジェクトエクスプローラー** の左上隅にあるプラスのアイコンをクリックして、すべてのドキュメントを展開し、プロジェクトの構造全体を確認します。
* **すべてのドキュメントを折りたたむ** – **プロジェクトエクスプローラー** の左上隅にあるマイナスのアイコンをクリックして、すべてのドキュメントを折りたたみます。
* **個々のフォルダを展開または折りたたむ** – 個々のフォルダ内のドキュメントを展開/折りたたむには、プラス/マイナスアイコンをクリックするか、フォルダをダブルクリックします。
* **選択したフォルダに固有のアクションを実行する** – 選択したフォルダを右クリックして、どのような機能を実行できるかを確認します。 The list of functions depends on the folder, for example, when right-clicking the **System** module, you can only find usages of this module, while when right-clicking **MyFirstModule** you can add a page, add a microflow, rename the module, export the module package, copy/paste documents, and much more.

## 3 続きを読む

* [プロジェクト](プロジェクト)
* [モジュール](モジュール)
* [セキュリティ](セキュリティ)
