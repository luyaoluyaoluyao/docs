---
title: "禁止ルール"
parent: "errors-pane"
menu_order: 10
description: "Studio Pro で警告の抑制ルールについて説明します。"
tags:
  - "Studio Pro"
  - "整合性エラー"
  - "チェック"
  - "警告"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/suppression-rules.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介 {#intro}

プロジェクトで作業すると、Studio Proで一貫性のチェックが行われ、警告が表示される可能性があります。 警告は、重要ではなく、問題になる可能性のある問題を特定します。 これらの警告は **エラー** ペインに表示されます。

![エラーペイン内の警告](attachments/suppression-rules/errors-pane-with-warnings.png)

警告は貴重ですが、以下のように、無効にしたい場合があります。

* あなたは警告につながるあなたのプロジェクトで慎重な選択をしました、そしてあなたはこれが問題につながることはありません知っています。
* 警告が含まれている Marketplace モジュールを使用しており、Marketplace モジュールを変更したくない場合があります。
* 警告の数が多すぎるため、 **警告** タブはもう使用できません。 一部を一時的に無効にしたいのです

**抑制ルール** では警告を無効にすることができます。 You can [suppress warnings](#suppress-warning) from the **Errors** pane and [manage them](#managing-rules) via the **Suppression rules** option. [すべての Marketplace モジュール](#suppress-appstore-warnings) の警告を抑制することも可能です。

## 2 抑圧ルールのLogic {#suppression-rules-logic}

抑制ルールは、1人のユーザーと1つのプロジェクトのインスタンスに対して適用されます。 あなたが抑制した警告はユーザーやプロジェクト間で共有されません。 同じプロジェクトに取り組んでいるチームメンバーに対して警告は抑制されません

抑制ルールは、 *project-settings.user.json* というファイルの中に、プロジェクトディレクトリにローカルに保存されます。 Team Serverに変更を反映すると、Studio Proはこのファイルを無視します。

![Windows エクスプローラに表示される設定ファイル](attachments/suppression-rules/windows-explorer-showing-settings-files.png)

ただし、抑制ルールを手動でエクスポートおよびインポートすることは可能です。 警告のエクスポートとインポートの方法については、 [抑制ルール](#export) と [抑制ルール](#import) のセクションのインポートを参照してください。

## 3 エラーペインで警告を抑制する {#suppress-warning}

**エラー** ペインから、ドキュメント、モジュール、またはプロジェクト全体の警告を抑制できます。 ![警告を抑制する](attachments/suppression-rules/suppressing-warning.png)

### 3.1 特定の文書に対する警告の禁止

特定のドキュメントのみの警告を抑制するには、次の操作を行います。

1. 抑制したい警告を右クリックします。

2. **この警告を抑制する** > **ドキュメントについては {Document name}** を選択してください。


この警告は、特定の文書についてのみ抑制されます。 同じ警告が別のドキュメント(例えば、別のページ)に表示された場合でも、そのドキュメントに対して表示されます。

### 3.2 特定のモジュールに対する警告を抑制する

特定のモジュールの警告を抑制するには、次の操作を行います。

1. 抑制したい警告を右クリックします。

2. **この警告を抑制する** > **モジュール {Module name}については** を選択してください。


モジュール全体で警告が抑制されます。 同じ警告が別のモジュールに表示された場合でも、そのモジュールに対して表示されます。

### 3.3 プロジェクト全体の警告を抑制する

プロジェクト全体の警告を抑制するには、次の操作を行います。

1. 抑制したい警告を右クリックします。

2. **この警告を抑制する** > **プロジェクト全体の**.


この警告はプロジェクト全体で抑制され、警告の一覧は **エラー** ペインで更新されます。

抑制ルールを編集または削除する方法についての詳細は、 [抑制ルール](#managing-rules) のセクションを参照してください。

## 4 抑制ルール {#managing-rules}

抑制ルールの追加、編集、削除、エクスポート、またはインポートができます。 マーケットプレイスからの警告を抑制することもできます。

{{% alert type="info" %}}
抑制ルールを変更したら、 **OK** をクリックして **抑制ルールの管理** ダイアログボックスを閉じ、変更を適用します。
{{% /alert %}}

### 4.1 AMmarketplace警告を抑制する {#suppress-appstore-warnings}

マーケットプレイスの警告を抑制するには、以下を行ってください。

1.  **エラー** ペインの **抑制ルール** ボタンをクリックします。

    ![抑制された警告ルールを表示する](attachments/suppression-rules/errors-pane-suppress-warnings-button.png)

2. **抑制ルール** の管理ダイアログボックスで、 **マーケットプレイスモジュールからの警告を抑制する** オプションをチェックします。

    ![マーケットプレイスの警告を抑制する](attachments/suppression-rules/rules-dialog-app-store-setting.png)

3. **OK** をクリックして、新しい設定を適用します。

Marketplace モジュールからの警告は抑制されます。

### 4.2 ルールの追加

より高度な場合は、手動で新しいルールを追加することができます。 これにより、抑制する警告を決定する際に、ルールが使用する設定を完全に制御できます。

手動で新しいルールを追加するには、以下の手順に従ってください。

1. **エラー** ペインの **抑制ルール** ボタンをクリックします。

2. **抑制ルールの管理** ダイアログボックスで、 **新規** ボタンを選択します。

    ![ルールウィンドウ - 新規ボタン](attachments/suppression-rules/rules-dialog-new-button.png)

3. In the **Add Suppression Rule** dialog box, set the necessary options to add the rule (for more information on settings, see the [Rule Setting](#rule-settings) section.

    ![ルールウィンドウ - 抑制を追加](attachments/suppression-rules/new-warning-window.png)

4. **OK** をクリックして選択を確認します。

5. **抑制ルール** ダイアログボックスの **OK** をクリックして変更を保存します。

抑制ルールが作成されます。


### 4.3 ルールの編集

既存のルールを編集するには、以下の手順に従ってください:

1. **エラー** ペインの **抑制ルール** ボタンをクリックします。

2.  **抑制ルールの管理** ダイアログボックスで、 **** ボタンを選択します。

    ![ルールウィンドウ - 編集ボタン](attachments/suppression-rules/rules-dialog-edit-button.png)

3.  In the **Edit Suppression Rule** dialog box, edit options to change the rule (for more information on settings, see the [Suppression Rule Settings](#rule-settings) section.

    ![ルール設定ウィンドウ](attachments/suppression-rules/rule-settings-window.png)

4. **OK** をクリックして選択を確認します。

5. **抑制ルール** ダイアログボックスの **OK** をクリックして変更を保存します。

抑制ルールが編集されます。


### 4.4 ルールの削除

既存のルールを削除するには、以下の手順に従ってください。

1. **エラー** ペインの **抑制ルール** ボタンをクリックします。

2.   **抑制ルールの管理** ダイアログボックスで、 **削除** ボタンをクリックします。

    ![ルールウィンドウ - 削除ボタン](attachments/suppression-rules/rules-dialog-delete-button.png)

抑制ルールが削除されます。


### 4.5 抑制ルールのインポート {#import}

抑制ルールをインポートするには、次の操作を行います。

1. **エラー** ペインの **抑制ルール** ボタンをクリックします。

2.  **抑制ルールの管理** ダイアログボックスで、 **インポート** ボタンを選択します。

    ![インポートルールボタン](attachments/suppression-rules/import-rules.png)

3. インポートするフォルダを参照します (インポートするファイル拡張子は *.suppressions.json* である必要があります)。

4. **** をクリックしてファイルを選択します。

5.  確認ポップアップウィンドウで、 **OK** をクリックして閉じます。

    ![ルールのインポートの確認](attachments/suppression-rules/confirmation-dialog-after-rules-imported.png)

6. **抑制ルールの管理** ダイアログボックスの **OK** をクリックします。

警告のリストが更新されました。


### 4.6 あなたの抑制ルールのエクスポート {#export}

抑制ルールをエクスポートするには、次の手順を行います。

1. **エラー** ペインの **抑制ルール** ボタンをクリックします。

2.  **抑制ルールの管理** ダイアログボックスで、 **書き出し** ボタンを選択します。

    ![エクスポートルールボタン](attachments/suppression-rules/export-rules.png)

3. ルールをエクスポートするフォルダを参照します(デフォルトでは、ファイル名は `<your app name>.suppressions.json` です)。

4. **Save** ボタンをクリックして、エクスポートしたルールを保存します。

5.  確認ポップアップウィンドウで、 **OK** をクリックして閉じます。

    ![ルールのエクスポートの確認](attachments/suppression-rules/confirmation-dialog-after-rules-exported.png)

6. **抑制ルールの管理** ダイアログボックスの **OK** をクリックします。

抑制ルールがエクスポートされます。 別のユーザーは [同じ抑制ルールを使用するファイルを](#import) インポートできます。


## 5つの抑制ルールの設定 {#rule-settings}

以下の表は利用可能な設定について説明しています。

| 設定     | 説明                                                                                                                                                       |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| モジュール  | 選択したモジュール内の警告を抑制します。 **(All)** が選択されている場合、ルールはすべてのモジュールに適用されます。                                                                                          |
| ドキュメント | 選択したドキュメント内の警告を抑制します。 **(すべて)** を選択すると、選択したモジュール内のすべてのドキュメントにルールが適用されます。 **メモ**: 特定のドキュメントを選択するには、最初に **モジュール** を選択する必要があります。                            |
| 非表示:   | 特定の *エラーコード* または *すべての* 警告を抑制できます。                                                                                                                       |
| 値      | Only displayed when the **Error code** option is selected in the **Suppress for** selector above. この特定の警告だけを抑制するために、 **CW1234**などの特定のエラーコードを入力することができます。 |

## 6もっと読む {#read-more}

* [Errors Pane](errors-pane)
* [整合性エラー](一貫性エラー)
