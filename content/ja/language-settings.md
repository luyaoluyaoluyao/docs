---
title: "言語設定"
parent: "translatable-text"
menu_order: 10
tags:
  - "studio pro"
  - "翻訳"
  - "言語"
  - "翻訳可能なテキスト"
  - "言語を追加"
  - "日付の形式"
  - "完全さ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/language-settings.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

Mendixは、ユーザーが複数の言語で使用するように設計されています。 **プロジェクト設定** の **言語** タブでは、アプリがサポートする言語を選択できます。

![](attachments/language/01_project_settings.png)

次の2つの方法でこのタブにアクセスできます:

1. メニューオプション **言語 > 言語設定…** を選択します。
2. **プロジェクト {Name} > 設定** ダイアログボックスを [プロジェクト エクスプローラー](project-explorer) から開き、 **言語** タブを選択します。

## 2 標準言語の設定

デフォルトのアプリ言語が必要です。 ドロップダウン リストから **既定の言語** を選択します。 これにはアプリに追加されたすべての言語が含まれます。 アプリの開発を開始する際には、これを行うことをお勧めします。

デフォルト言語の設定には2つの関数があります:

* エンドユーザーが言語エンティティに関連付けられていない場合に表示される言語を設定します。 または、エンドユーザーの言語がアプリで有効になっていない場合
* エンドユーザーの言語に翻訳可能なテキストの翻訳がない場合に使用される言語を設定します たとえアプリの言語が有効になっていたとしても

初期設定言語は *英語、アメリカ合衆国* です。

## 3 アプリ言語の追加

You can add as many languages as you like from the list of supported languages by clicking **Add**, selecting the desired language, and clicking **OK**.

![](attachments/language/add-language.png)

ほとんどの言語は空の辞書で追加されますが、一部の翻訳はオランダ語辞書で既に設定されています。

## 4つの高度な言語設定{#advanced}

アプリの言語ごとに追加設定を行うことができます。

![言語を編集](attachments/language/edit-language.png)

### 4.1 完全性の確認

If you check the **Check completeness** box, you will get a warning (or error) message in the [Errors pane](errors-pane) for every text which has no entry in this language's dictionary.

これがデフォルト言語の場合、 **完全性をチェックする** ボックスがチェックされ、チェックを外すことはできません。

### 4.2 日付と時刻の書式設定

以下のようにカスタム書式を設定できます。

* **日付の形式**
* **時刻の形式**
* **日付と時刻の形式**

該当するボックスにフォーマット文字列を入力すると、下に日付がどのようにフォーマットされるかの例が表示されます。

**編集…** をクリックして、フォーマット文字列の完全な参照を提供するダイアログボックスを開きます:

![日付編集ダイアログ](attachments/language/date-format.png)
