---
title: "一括翻訳"
parent: "translatable-text"
menu_order: 30
tags:
  - "studio pro"
  - "翻訳"
  - "言語"
  - "翻訳可能なテキスト"
---

## 1つの紹介

**バッチ翻訳** を使用すると、別の言語のテキストに対応する1つの言語でテキストを入力できます。

通常は、デフォルトの言語から第二の言語に翻訳したいと思うでしょうが、テキストの他の辞書を使用することができます。 For example, if your default language is *English, United States* you may already have translated the text into *Dutch, Netherlands* and you can use this as a reference for translating into *Dutch, Belgium* as there are likely to be more similarities.

![](attachments/language/batch-translate.png)

## 2 一括翻訳を使用する

一括翻訳は2つの言語間で行われます。 When you select batch translate you will be asked to select the two languages you wish to use, a **Source language** to use as a reference, and a **Destination language** which is the one you want to update.

![翻訳元言語と翻訳先言語を選択](attachments/language/batch-translate-languages.png)

### 2.1 ドキュメント/モジュール

一括翻訳に使用するモジュールを1つ以上選択できます。 たとえば、既にインポートされたモジュールとシステムモジュールの翻訳があり、独自のモジュールの翻訳に集中したい場合などです。

**Select…** そして作業したいモジュールを確認してください。

![モジュール選択画面](attachments/language/batch-replace-modules.png)

デフォルトでは、アプリ内のすべてのモジュールで動作します。

### 2.2 ソーステキストに含まれるソース テキスト

元の言語テキスト内の特定のフレーズを検索するには、検索対象のフレーズを入力します。 宛先言語でテキストを検索することはできません。

![一括翻訳検索](attachments/language/batch-translate-search.png)

デフォルトでは、選択したモジュールのすべての翻訳可能なテキストが表示されます。

見つかった各テキストは **ソース** 列に表示されます。 **#** 列には、選択したモジュールで発生する回数が表示されます。

行を選択した場合。 **発生を表示** セクションを見て、テキストを含む **オブジェクト** と、それが表示される **ドキュメント** を見ることができます。 ドキュメントをダブルクリックするか、 **発生を表示** をクリックすると、ドキュメントが開き、オブジェクトを選択してコンテキストを簡単に見ることができます。

{{% alert type="success" %}}
ヒント: ダイアログボックスを片側に移動して、ドキュメントをよりよく見ることができます。
{{% /alert %}}

### 2.3 翻訳

**翻訳**では、既存のテキストの代わりに使用する新しいテキストを入力します。 **Translate** をクリックして置き換えを確認します。

![](attachments/language/batch-translate-translate.png)

翻訳言語で同じですが、翻訳言語で異なる2つのテキストがある場合。 個別に見直し変える必要があります これはあまり一般的ではありませんが、例えば想像してみてください あなたは `注文行` を *の両方に* 行の行を記述し、 *いくつかの行をソートするボタン*を使用しました。 個々のテキストを変更する方法については、 [言語メニュー](translatable-texts#selected-language) の *現在選択されている言語での作業* を参照してください。

## 3 エクスポート & テキスト{#export-import} をインポート

Studio Pro 以外の言語を翻訳したい場合は、Microsoft Excel (*) に翻訳可能なテキストをエクスポートできます。 lsx * )*) 変更を行い、更新された Excel ファイルから変更をインポートします。</p>

これは、複数のアプリで作業していて、翻訳を別のアプリに適用したい場合に特に便利です。

### 3.1 Excel にエクスポート

**Excel にエクスポート…** をクリックして、現在表示されているテキストアイテムを Microsoft Excel (*.xlsx*) 形式ファイルにエクスポートします。

ファイルの形式は以下のとおりです。

![Excelファイルのサンプル](attachments/language/batch-translate-excel.png)

**Row 1** – *Filter:* はエクスポートされたファイルに含まれるモジュールを示します。

**Row 2**  – ソース言語と翻訳言語を示します。 最初の列は現在のテキスト、2番目の列は *翻訳* テキストを表します。

**Rows 3+**  – 現在のテキストを表示

ファイルがインポートされると処理される列 B に変更を加えることができます。

### 3.2 Excel からインポート

**Excel からインポート…** をクリックして、正しく構築された Microsoft Excel (*.xlsx*) 形式ファイルをインポートします。

これにより、以下が行われます。

* 選択したモジュールはファイルの *フィルター:* 行にあるモジュールに設定されます。
* 列Bに空のテキストはすべて無視されます
* 選択したモジュール内の翻訳可能なテキストと一致しない列Aのテキストはすべて無視されます
* 無視されていない列Bのすべてのテキストが **翻訳** 列に入力されます

**Translate** をクリックすると変更が行われます。

{{% alert type="warning" %}}
バッチ翻訳とバッチ置き換え用のExcelファイルの形式は似ています。 バッチ置き換えファイルやバッチ翻訳ファイルを間違った言語でインポートしようとすると警告されますが、警告を無視するとインポートできます。
{{% /alert %}}
