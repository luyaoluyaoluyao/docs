---
title: "共同開発のトラブルシューティング"
parent: "共同開発"
description: "Mendix Desktop ModelerとMendix Web Modelerとの共同開発のためのトラブルシューティングについて説明します。"
tags:
  - "デスクトップモデラー"
  - "共同開発は"
  - "トラブルシューティング"
  - "トラブルシューティング"
---

## 1つの紹介

{{% alert type="warning" %}}

共同開発は、Mendix バージョン 7.23.3 以降のプロジェクトの場合にのみ利用できます。 Mendix バージョン 7.23.2 以下のプロジェクトでは、Web Modelerとの同期はできません。

Webモデラーでプロジェクトを開くことができます(Webモデラーは自動的に7の最新バージョンにアップグレードします)。 3)  ただし、Web Modelerからの変更を同期するには、Mendix Desktop Modelerバージョン7.23.3以上を使用する必要があります。

{{% /alert %}}

共同開発により、ユーザーはモデルの変更を互いに共有することができます。 このドキュメントは、変更をWebモデラーと共有するプロセス中に発生する可能性のある問題のトラブルシューティングに役立ちます。

## 2つのコンセプト

概念と定義については、 [バージョンコントロール](version-control#concepts) のセクション *2 コンセプト* を参照してください。

## 3 Webモデラーが同期していません {#out-of-sync}

通常、Web Modelerの作業コピーは、Desktop Modelerユーザが更新またはコミットを行うと、Desktop Modelerと同期されます。 ただし、コミットやアップデートがデスクトップモデラー以外で発生した場合(Tortoise SVN などのバージョン管理ツールを使用している場合) Webモデラーは一時的に同期できません。 この場合、警告が表示されます:

![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)

次のいずれかを実行できます:

1.  **Merge** (推奨)– デスクトップモデラーは、Webモデラーからの同期されていない変更を自動的にマージしようとします。 ローカルの変更があれば、Web Modelerの変更と組み合わされます。 Web Modelerからの変更は自動的に作成されたブランチに保存され、プロセスに変更が失われないようにします。 ブランチはブランチマネージャーに表示されます。 このプロセスは、次のいずれかの結果をもたらす可能性があります: <br/>

    a  マージ処理が正常に終了すると(競合なしに)作成されたブランチが作業コピーにマージされ、Web モデラーの変更が表示されます。 統合された変更を確認し、Web ModelerとDesktop Modelerを再度同期させるためにコミットする必要があります。 その後、自動的に作成されたブランチを削除できます。<br/>

    B プロセスにマージ競合が見つかった場合は、それらを解決し、その後変更をコミットする必要があります。 競合を解決して変更をコミットしたら、自動的に作成されたブランチを削除できます。<br/>

    ![](attachments/collaborative-development-troubleshooting/automatically-created-branch.png)

2. **あとで解決** – 変更は後でマージすることができます。 一方、Web ModelerとTeam Serverの開発ラインからの変更は同期されません。 この場合、変更のコミット/更新/マージ時にダイアログが再び表示されます。

## 4デスクトップモデラーとWebモデラーの変更の統合に失敗しました

Web Modelerが有効になっているブランチと、Desktop Modelerの外部のコミットが別の行にマージされている場合。 次のようなメッセージが表示されます

![](attachments/collaborative-development-troubleshooting/cannot-merge-automatically.png)

次のいずれかを選択できます:

1.  **マージをキャンセル** (推奨) – プロセスをキャンセルし、最初にWebモデラーと同期することができます。 次の操作を行います:<br/> a.  Web Modeler対応の開発ライン<br/> を開く b.  The warning descriptions [3 The Desktop Modeler & the Web Modeleris out of Sync](#out-of-sync) will be displayed.<br/>

    ![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)<br/>

    C **Merge** をクリックして、変更を Web Modelerと同期します。<br/>

    D 前のブランチを開き、再度マージを行います。

2. **Merge とにかく** – Webモデラーからの変更なしにマージは続行されます。 この場合、Desktop Modelerからの変更のみが含まれます。 Desktop ModelerとWeb Modelerは同期されていないため、後でこの問題を解決する必要があります。 See section [3 Desktop Modeler & Web Modelerは同期されていません](#out-of-sync)

## 5 リポジトリサービスが利用できません

**Update** 操作中、変更は Web Modelerから要求され、現在のプロジェクトに統合されます。  更新プロセスには追加のステップ **ブランチステータス** を取得します。 このステップでは、Web Modelerの変更が取得されます。

![](attachments/collaborative-development-troubleshooting/retrieving-branch-status.png)

ネットワークまたはサービスに問題がある場合は、Desktop Modelerはリポジトリサービスに接続できず、警告メッセージが表示されます。

![](attachments/collaborative-development-troubleshooting/changes-are-not-retrieved.png)

次のいずれかを実行できます:

1. **キャンセル** (推奨) – 操作はキャンセルされます。ネットワークの問題が解決された場合は、後でもう一度お試しください。

2. **** – 更新プロセスは継続しますが、Webモデラーからの変更は取得されません。 Desktop ModelerとWeb Modelerは同期されていないため、後でこの問題を解決する必要があります。 See section [3 Desktop Modeler & Web Modelerは同期されていません](#out-of-sync)

## 6 他の操作が進行中です

あなたのチームメンバーがブロック操作を開始するとき (コミット/更新/マージWebモデラー有効ブランチ/スイッチWebモデラー有効ブランチ) それと同時にブロッキング操作も開始します。下のダイアログが表示されます。

![](attachments/collaborative-development-troubleshooting/another-operation-in-progress.png)

次のいずれかを実行できます:

1. **キャンセル** (推奨) – 操作はキャンセルされます。 最新の変更と作業コピーとWebモデラーが同期されるように、数分で更新を行うことをお勧めします
2. **** – 更新プロセスは継続しますが、Webモデラーからの変更は取得されません。 Desktop ModelerとWeb Modelerは同期されていないため、後でこの問題を解決する必要があります。 See section [3 Desktop Modeler & Web Modelerは同期されていません](#out-of-sync)

## 7 続きを読む

* [バージョン管理](version-control)
* [Webモデラーにおける共同開発](/studio7/general-collaborative-development)
