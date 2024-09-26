---
title: "言語メニュー"
parent: "menus"
menu_order: 50
tags:
  - "studio pro"
  - "翻訳"
  - "言語"
  - "翻訳可能なテキスト"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/translatable-texts.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

Mendixは、異なる言語要件を持つユーザーに同じ情報を簡単に提示できるように設計されています。 これをサポートするために、エンドユーザーに表示されるすべてのテキストを異なる言語に翻訳することができます。

これらの *翻訳可能なテキスト* には、以下のものが含まれます。

* [ボタン](button-widgets) の字幕
* [データ グリッド](data-grid) 列
* [ラベル](ラベル)
* [メニュー項目](menu#menu-item)
* [メッセージ](show-message) は [マイクロフロー](microflows) から送信されます
* [テキスト](テキスト)

## 現在選択されている言語で作業している2つ{#selected-language}

現在作業中の言語は、画面の右下に表示されます。

![言語の状態](attachments/language/language-status.png)

アプリに複数の言語が設定されている場合は、次のいずれかを実行することで、使用する言語を選択できます。

* **言語 > 現在の言語** メニューから選択してください
* Studio Proのメインウィンドウの右下隅にあるドロップダウンを使用してください
* <kbd>Ctrl</kbd>+<kbd>L</kbd> または <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>L</kbd> キーボードショートカットの組み合わせを使用します。 設定された言語を循環させます

デフォルトではない言語で作業する場合、まだ翻訳されていないテキストを識別できます。 これらは、角括弧間のデフォルト言語でテキストを表示します。 例えば、 `<Name>`. 適切な翻訳でテキストを置き換えることができ、現在選択されている言語に置き換えられます。

デフォルトの言語ではない間に新しいウィジェットを追加するためにアプリを編集する場合 ウィジェットの新しい翻訳可能なテキストは現在の言語に追加されます デフォルト言語のテキストは空白のままにするか、ウィジェットのプレースホルダー テキストが表示されます。

アプリケーションを実行すると、翻訳されていないすべてのテキストがデフォルトの言語で表示されます。

{{% alert type="info" %}}
デフォルト言語にテキストがない場合、エンドユーザーは `[no translation]` を参照します。 テキストを空白にしたい場合は、デフォルトの言語テキストを空白ではなくスペースに設定します。
{{% /alert %}}

## 3言語メニュー

**言語** メニューでは、アプリの追加言語と翻訳を管理できます。 これには、個別に各発生を変更するのではなく、単一の変更で表示されるすべての場所でテキストを翻訳するのに役立つ機能が含まれています:

{{% image_container width="300" %}}![言語メニュー](attachments/language/language-menu.png)
{{% /image_container %}}

### 3.1 メニューアイテムの概要

**言語** のメニュー項目は以下の表に記載されています。

| メニュー項目                       | 説明                                         | ショートカットキー                                         |
| ---------------------------- | ------------------------------------------ | ------------------------------------------------- |
| **現在の言語**                    | **言語設定…** で設定されている言語のいずれかから現在の言語を選択してください。 | *なし*                                              |
| **前の言語を選択**                  | **言語設定…** で選択された言語のリストから以前の言語を選択してください。    | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>L</kbd> |
| **次の言語を選択**                  | **言語設定…** で選択された言語のリストから次の言語を選択してください。     | <kbd>Ctrl</kbd> + <kbd>L</kbd>                    |
| [言語設定…](language-settings)   | アプリでサポートされている言語を選択し、日付と時刻の設定を行います。         | *なし*                                              |
| [一括置換…](batch-replace)       | 現在の言語で選択された翻訳可能なテキストのすべての出現箇所を変更します。       | *なし*                                              |
| [一括翻訳…](batch-translate)     | 選択した翻訳元の言語から選択した翻訳先の言語に翻訳を追加および編集          | *なし*                                              |
| [言語操作…](language-operations) | 言語間で翻訳を操作 (例えば、コピー) します。                   | *なし*                                              |

## 4 エンドユーザーの言語の設定

エンドユーザーに表示される言語は、関連 **User_Language** を介して、現在のエンドユーザーの **ユーザー** オブジェクトに関連付けられている **Language** オブジェクトによって決定されます。

関連付けられた言語がアプリで設定されていない場合、エンドユーザーはデフォルト言語でページを表示します。

エンドユーザーが言語に関連付けられていない場合、たとえばそれらは匿名ユーザーです。 使用言語は、ユーザーのブラウザやオペレーティングシステムの設定によって異なります。 要求された言語がアプリに存在しない場合は、アプリのデフォルト言語が使用されます。 要求された言語は以下のとおりです:

* ウェブアプリ - ブラウザの言語の優先順位に基づいてアプリで設定された言語に一致する最初の言語
* モバイルアプリ向け – オペレーティングシステムの言語

![ユーザーと言語のシステムドメインモデル](attachments/language/user-language-domain-model.png)

エンドユーザーがアプリ内で表示言語を変更できるようにすると、変更はすぐには適用されません。 これは、アプリの翻訳可能なテキストがすでにエンドユーザーのオリジナル言語に設定されているためです。

言語が変更されていることを確認するには2つのオプションがあります:

1. エンドユーザーに手動で何かを行うように依頼する
    * サインアウトして再度サインインする
    * ブラウザのrefresh コマンドを使用する
2. Mendixを強制的にページを再読み込みさせるには、次の手順を実行します。
    1. アプリにサポートされるプラットフォームウィジェット [HTML / JavaScript Snippet](https://marketplace.mendix.com/link/component/56/) を追加します。
    2. ポップアップページを作成します。
    3. ポップアップページに HTMLSnippet ウィジェットを配置します。
    4. **JavaScript** のコンテンツ `mx.reloadWithState();` をウィジェットに追加します。
    5. ユーザーの言語を切り替えるときに、マイクロフローから新しいポップアップページを開きます。

    ![ユーザーと言語のシステムドメインモデル](attachments/language/reload-with-state.png)

{{% alert type="info" %}}
The above only applies to pages *within* your Mendix application (meaning, pages that are created in Studio Pro). The labels for static pages (such as the *index.html* and *login.html* pages in the **theme** folder of your app) are generated when you create a deployment package using the default language of your project. これらのページのラベルは、異なるユーザーのために変更されることはありません、彼らは常に同じになります。
{{% /alert %}}

## 5 続きを読む

* [アプリのコンテンツを翻訳する方法](/howto8/collaboration-requirements-management/translate-your-app-content) - 翻訳を追加する作業例
* [翻訳可能な検証メッセージの使い方](/howto8/logic-business-rules/translatable-validation-messages)
* [リンクをクリックして言語を変更する](https://forum.mendixcloud.com/link/questions/91821) - 言語が変更されたときにページを更新するためのMendixフォーラムの説明とアイデア
* [Anonymous User Journey](https://forum.mendixcloud.com/link/questions/91676) - 匿名エンドユーザー向けの言語切り替えに関するMendixフォーラムに関するディスカッション
