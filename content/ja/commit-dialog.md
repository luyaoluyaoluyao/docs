---
title: "コミット"
parent: "version-control-menu"
menu_order: 20
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/commit-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

format@@0 ダイアログは、Team Server への変更のコミットに使用されます。 メッセージを入力し、該当する場合は関連するストーリーを選択できます。

![バージョン管理メニュー](attachments/version-control-menu/commit-dialog-stories.png)

## 2支局

ダイアログボックスの上部に、コミットしているブランチが表示されます。 これは次のいずれかになります:

| ブランチの説明                                                            | メモ                  |
| ------------------------------------------------------------------ | ------------------- |
| ![バージョン管理メニュー](attachments/version-control-menu/commit-main.png)   | お前は主要な線を引いている       |
| ![バージョン管理メニュー](attachments/version-control-menu/commit-branch.png) | 指定されたブランチをコミットしています |

## 3件のメッセージ

変更内容を説明するメッセージを入力します。 このメッセージは複数行を含んでいる可能性があります。 キーボードを使用してコミットを行う場合は、 <kbd>Ctrl</kbd>+<kbd>Enter</kbd> を押すことができます。

## 4つのタブをコミット

### 4.1 関連するストーリー {#stories}

![バージョン管理メニュー](attachments/version-control-menu/commit-dialog-stories.png)

コミットに関連するストーリーの横にあるボックスにチェックを入れます。 私たちは、一度に少ない数の変更を行うことをお勧めします, 通常、一つの関連する話があります.

### 4.2 モデルの変更

![バージョン管理メニュー](attachments/version-control-menu/commit-dialog-model-changes.png)

モデルに変更がある場合、このタブにはそれらの変更の概要が表示されます。 Studio Pro でどのように変更が報告されるかについては、 [変更 ペイン](changes-pane) を参照してください。

### 4.3 ディスク上の変更

![バージョン管理メニュー](attachments/version-control-menu/commit-dialog-disk-changes.png)

ディスクに変更がある場合、このページにはそれらの変更の概要が表示されます。 **含まれるフォルダを開く** をクリックして、Windows エクスプローラで選択したファイルを含むフォルダを開きます。

ディスクが変更されていない場合、タブページは非表示になります。 多くの場合、モデルの変更はありますが、ディスク上の唯一の変更は、これらのモデルの変更を反映したプロジェクト ファイル (.mpr) です。 この場合、役に立つ情報を追加しないので、非表示になります。
