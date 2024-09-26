---
title: "共同開発のトラブルシューティング"
parent: "共同開発"
description: "Mendix Studio Pro と Mendix Studio の共同開発に関するトラブルシューティングについて説明します。"
tags:
  - "studio pro"
  - "スタジオ"
  - "共同開発は"
  - "トラブルシューティング"
  - "トラブルシューティング"
---

## 1つの紹介

共同開発により、ユーザーはモデルの変更を互いに共有することができます。 このドキュメントは、Mendix Studio で変更を共有するプロセス中に発生する可能性のある問題のトラブルシューティングに役立ちます。

## 2つのコンセプト

概念と定義については、 [バージョンコントロール](version-control#concepts) の *コンセプト* のセクションを参照してください。

## 3 Studio が同期されていません {#out-of-sync}

通常、Studio Pro ユーザーが更新またはコミットを行うと、Studio の作業コピーは Studio Pro と同期されます。 ただし、コミットやアップデートがStudio Pro以外で発生した場合(Tortoise SVNなどのバージョン管理ツールを使用)。 Studio は一時的に同期できません。 この場合、警告が表示されます:

![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)

次のいずれかを実行できます:

1.  **Merge** (推奨)– Studio Pro は、Studio からの同期されていない変更を自動的にマージしようとします。 ローカルの変更があれば、Studio の変更と組み合わされます。 Studio からの変更は自動的に作成されたブランチに保存され、プロセスに変更が失われないようにします。 ブランチはブランチマネージャーに表示されます。 このプロセスは、次のいずれかの結果をもたらす可能性があります: <br/>

    a  マージ処理が正常に終了すると(競合なしに)、作成されたブランチが作業コピーにマージされ、Studio の変更が表示されます。 マージされた変更を確認し、それらをコミットして、Studio と Studio Pro の同期を再度取得する必要があります。 その後、自動的に作成されたブランチを削除できます。<br/>

    B プロセスにマージ競合が見つかった場合は、それらを解決し、その後変更をコミットする必要があります。 競合を解決して変更をコミットしたら、自動的に作成されたブランチを削除できます。<br/>

    ![](attachments/collaborative-development-troubleshooting/automatically-created-branch.png)

2. **あとで解決** – 変更は後でマージすることができます。 一方、Studio と Team Server 開発ラインからの変更は同期されません。 この場合、変更のコミット/更新/マージ時にダイアログが再び表示されます。

## Studio Pro と Studio の変更の統合に失敗しました 4

Studio Pro 外でコミットが有効になっている Studio が別の行とマージされている場合、以下のメッセージが表示されます。

![](attachments/collaborative-development-troubleshooting/cannot-merge-automatically.png)

次のいずれかを選択できます:

1.  **Merge** をキャンセル (推奨) – プロセスをキャンセルして、最初に Studio と同期してみることができます。 次の操作を行います:<br/> a.  Studio 対応の開発ラインを開きます。<br/> b.  [Studio Pro & Studio Are Out of Sync](#out-of-sync) セクションで説明されている警告が表示されます。<br/>

    ![](attachments/collaborative-development-troubleshooting/changes-are-out-of-sync.png)<br/>

    C **Merge** をクリックして変更を Studio と同期します。<br/>

    D 前のブランチを開き、再度マージを行います。

2. **Merge とにかく** – Studio からの変更なしにマージは続行されます。 この場合、Studio Pro からの変更のみが含まれます。 Studio Pro と Studio は同期されていないため、後でこの問題を解決する必要があります。 [Studio Pro & Studio Are Out of Sync](#out-of-sync) セクションを参照してください。

## 5 リポジトリサービスが利用できません

**Update** 操作中、変更は Studio から要求され、現在のプロジェクトに統合されます。  更新プロセスには追加のステップ **ブランチステータス** を取得します。 このステップでは、Studio の変更が取得されます。

![](attachments/collaborative-development-troubleshooting/retrieving-branch-status.png)

ネットワークまたはサービスの問題がある場合、Studio Proはリポジトリサービスに接続できず、警告メッセージが表示されます。

![](attachments/collaborative-development-troubleshooting/changes-are-not-retrieved.png)

次のいずれかを実行できます:

1. **キャンセル** (推奨) - ネットワークの問題が解決された場合、操作はキャンセルされます。後で再試行できます。

2. **** – 更新プロセスは継続されますが、Studio からの変更は取得されません。 Studio Pro と Studio は同期されていないため、後でこの問題を解決する必要があります。 [Studio Pro & Studio Are Out of Sync](#out-of-sync) セクションを参照してください。

## 6 他の操作が進行中です

チームメンバーがブロック操作を開始したとき (スタジオが有効なブランチをコミット/更新/マージするか、スタジオが有効なブランチを切り替えます) それと同時にブロッキング操作も開始します。下のダイアログが表示されます。

![](attachments/collaborative-development-troubleshooting/another-operation-in-progress.png)

次のいずれかを実行できます:

1. **キャンセル** (推奨) – 操作はキャンセルされます。 数分で更新を行うことをお勧めします。これにより、最新の変更が得られ、作業コピーと Studio が同期されます。
2. **** – 更新プロセスは継続されますが、Studio からの変更は取得されません。 Studio Pro と Studio は同期されていないため、後でこの問題を解決する必要があります。 [Studio Pro & Studio Are Out of Sync](#out-of-sync) セクションを参照してください。

## 7 続きを読む

* [バージョン管理](version-control)
* [Studio での共同開発](/studio8/collaborative-development)
