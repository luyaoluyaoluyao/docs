---
title: "支線を作成"
parent: "branch-line-manager-dialog"
menu_order: 90
tags:
  - "studio pro"
  - "分岐線を作成"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/create-branch-line-dialog.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**分岐線** の作成ダイアログ ボックスを使用して、 [分岐線](version-control#branches) を **分岐線 マネージャー** を介して作成します。

![](attachments/version-control-menu/create-branch-line.png)

**分岐線の作成** ダイアログボックスを表示するには、次の操作を行います:

1. Open **Version Control** > **Manage Branch Lines**.
2. **ブランチラインマネージャー**で、 **New** をクリックします。

**分岐線** の作成ダイアログボックスが表示されます。

分岐線の管理方法の詳細については、 [Collaborative Development](collaborative-development#managing-branches) と *Branch Line Manager* の [Studio Pro で開発ラインを管理する](branch-line-manager-dialog) セクションを参照してください。 バージョン管理の詳細については、 [バージョンコントロール](version-control) を参照してください。

## 2 ブランチの作成

**** から分岐を作成すると、分岐ラインを作成したい分岐ラインを選択できます。 次のいずれかのオプションを選択できます:

* <a name="main-line"></a>**メインライン** - メインラインとは独立して大きな機能を開発したい場合は、通常 *メインライン* を選択する必要があります。
* <a name="branch-line"></a>**ブランチライン** - 他のブランチラインからブランチラインを作成することができます
* <a name="tagged-version"></a>**タグ付けされたバージョン** - デプロイされたバージョンでメンテナンスを行っている場合は、 *タグ付けされたバージョン* を選択することをお勧めします。

## 3 Revision

この設定は、 [からブランチを作成](#main-line) で [メインライン](#branch-line) または **ブランチライン** を選択した場合にのみ使用できます。

メインラインまたはブランチラインを作成するブランチラインのリビジョンを選択します。 多くの場合、最新バージョンを選択したいと思うでしょう。

## 4支線

この設定は、 [ブランチの作成](#branch-line) で **ブランチライン** を選択した場合にのみ使用できます。

別の分岐線を作成する分岐線を選択します。 私たちは、あなたが本線からのみ支線を作ることをお勧めしますが、場合によっては支線を分岐することが有用である場合があります。

## タグ付けされた5バージョン

この設定は、 [](#tagged-version) からブランチを作成する **で** タグ付けされたバージョン </strong> を選択した場合にのみ使用できます。

ブランチラインを作成するタグ付けされたバージョンを選択します。 デプロイメント・アーカイブを作成するたびに、タグが作成され、プロジェクトのそのバージョンを常に参照できるようになります。

## 6支店名

新しいブランチラインの名前を入力します。

{{% alert type="warning" %}}
ブランチ名に特殊文字を含めることはできません(例: `@`, `$`, `#`)。
{{% /alert %}}

## 既存の支線7本

ブランチライン名は一意でなければならないため、このオプションは既存のブランチラインを表示します。 同じ名前のブランチを誤って作成しないようにします。

## 8 続きを読む

* [バージョン管理](version-control)
* [共同開発](collaborative-development)
