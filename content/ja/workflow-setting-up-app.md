---
title: "既存のアプリにワークフローを追加する: 基本の設定"
parent: "ワークフロー"
description: "Mendix Studio Proの既存アプリでワークフローコモンズを使用する方法について説明します。"
menu_order: 55
tags:
  - "studio pro"
  - "ワークフロー"
  - "タスク"
  - "オンボーディング"
---

## 1つの紹介

**Workflow Commons** はワークフロー固有のモジュールで、ページ、スニペット、ページテアンプ、マイクロフローなど、多くの事前設定済みドキュメントを含みます。 Mendix Marketplace から [Workflow Commons モジュール](https://marketplace.mendix.com/link/component/117066) をダウンロードし、アプリに統合することができますが、これにはまず準備が必要です。

Workflow Commonsモジュールをアプリに追加する前に、以下の内容が完了していることを確認してください。

* アプリケーションを Mendix 9 にアップグレード
* Mendix マーケットプレイスから Atlas 3 をインストールします。ワークフローコモンズによって異なります。
* Atlas 3のインストールの結果 Workflow Commonsが依存する以下のモジュールを含める必要があります: Atlas Core, Atlas Web Content, DataGrid

## 2 アプリの準備

デフォルトでは、 ワークフロー コモンズは [Mendix SSO](https://marketplace.mendix.com/link/component/117212) と統合し、開発者ポータルの [アプリユーザー管理ページ](/developerportal/collaborate/general-settings) でユーザーとロールを招待および管理できます。 Mendix SSO は Mendix Marketplace からダウンロードできます。 Mendix SSOがインストールされていない場合は、Workflow Commonsをインストールした後、一貫性のエラーが表示されます。 Mendix SSOモジュールを追加すると、Workflow Commonsのインストールによって生じる一貫性のエラーはなくなります。 別のユーザー認証とユーザー管理方法を実装する場合 ワークフローコモンズでMendix SSOへの参照を、好みのユーザーエンティティと置き換えることができます。

## 3ワークフローコモンズコンポーネント

Workflow Commonsの目的は、開発時間を節約できる便利なページ、ページテンプレート、スニペット、およびマイクロフローを提供することです。 All documents in the **Private** folder are meant for internal purposes within the module itself, but you can find a couple of useful documents that you can make use of in the **UseMe** folder.

### 3.1 ページ

Workflow Commonsモジュールには、あなたとあなたのユーザーがワークフローで開始できるようにするための3つのページがあります。 これらのページに含まれる機能はすぐに使用できます。 アプリの [ナビゲーション](navigation) にこれらのページを追加するだけで、使い始めることができます。 ワークフローコモンズでは、以下のページをご覧いただけます。

*   **DefaultWorkflowAdmin** – ワークフロー管理者がワークフローインスタンスの表示と管理に使用できるデフォルトのワークフロー管理者ページ。 このページは、 _Show workflow admin page_ microflow activity and button actionsで使用できます。
*   **TaskDashboard** – エンドユーザーにアプリのワークフローのパフォーマンスの概要を提供します。 これには、ユーザーが完了したタスクの数などの情報が含まれています タスクを完了するまでの平均時間と期限内に完了したタスクの割合です
*   **TaskInbox** – ユーザーが操作できるすべてのタスクの便利なリストが含まれています。 _My open tasks_ shows the tasks assigned to current users, _All open tasks_ is a list of tasks they could pick up, _Unassigned tasks_ shows all unassigned tasks, and _Completed tasks_ gives an overview of all tasks that were finished.
*   **WorkflowAdminCenter** – ワークフロー管理者向けのナビゲーションページ。 From here, a workflow administrator can go the the _Workflow dashboard_, which gives them general statistics of workflows, much like the _MyTaskDashboard_ does for users. ワークフロー管理者は _ワークフロー管理者センター_にもアクセスできます 特定のワークフローのすべてのインスタンスを見ることができ、データを変更したり、中止したりすることもできます。

### 3.2 ページ テンプレート

ワークフロー コモンズには、ワークフロー関連のページの構築を簡単に開始できるようにページテンプレートが含まれています。 これらのテンプレートは、ユーザー タスクまたはワークフロー プロパティから新しいページを作成すると自動的に提案されます。 ワークフローコモンズには、次のページテンプレートがあります。

*   **UserTask_Basic** – タスク名と説明を含むヘッダーを表示する基本的なテンプレート 担当者の状況やタスクの詳細が書かれたサイドバー そして、タスクを完了するための入力ウィジェットとボタンが生成されるメインビューです。
*   **UserTask_Extended** – 基本ユーザータスクテンプレートと全く同じことを行います。 添付ファイルやコメントセクションを追加するだけでなく、アクティビティのタイムラインを追加して、このワークフローで何が起こったかを確認することができます。
*   **Workflow_Overview** – 特定のワークフローの概要ページを簡単に生成できます。 ワークフローの名前と管理者のアクションメニューを含むヘッダーが含まれています。 _一般情報_, _タスクの詳細_, および _メモと添付ファイル_ の 3 つのタブがあります。 _一般情報_ タブには、ワークフローの現在の状態が表示されます。 それが始まって終わった時期と失敗の可能性がある理由と同様に アクティビティのタイムラインが表示されます 入力ウィジェットが生成されたセクションで管理者がワークフロー内のデータを変更できます 個々のタスクの詳細については、誰がそれらに取り組んだか、誰がそれらを拾うことができたでしょう。 _タスクの詳細_ タブに移動します。 最後に、 __ タブには、このワークフローに追加されたすべてのノートと添付ファイルの概要が表示されます。

### 3.3 スニペット

ページテンプレートをカスタマイズしたい場合は、Workflow Commonsが提供するスニペットを使用して行うことができます。 ワークフローコモンズモジュールの **スニペット** フォルダにあります。

### 3.4 Microflow

構成済みのマイクロフローは、ユーザータスクを割り当てるのに役立ちます。また、ワークフローを中断することもできます。 以下のマイクロフローは、Workflow Commonsで確認できます。

*   **ACT_UserTask_AssignToMe** – パラメータとして渡されるユーザータスクを割り当て、現在のユーザーに割り当てます。
*   **ACT_UserTask_AssignToUser** – 指定されたユーザーにユーザータスクを割り当てます。
*   **ACT_UserTask_Unassign** – パラメータとして渡されるユーザータスクから担当者を削除します。
*   **ACT_Workflow_Abort** – 現在実行中のユーザータスクとワークフローインスタンスを中断します。 ワークフローインスタンスはパラメータとして渡されます。

## 4 ユーザー割り当てとセキュリティの設定

Workflow Commonsモジュールには、使用するための2つのモジュールロールがあります。 **ユーザー** モジュールロールを持つユーザーは、 **MyTaskDashboard** と **MyTaskInbox** ページにアクセスできます。 ワークフロー上の添付ファイルやメモを作成および変更することができます。 誰かに **管理者** 権限を与えることで、 **WorkflowAdminCenter**を探索し、誰からの添付ファイルやメモを管理し、ワークフローを中止することができます。

アプリケーションに必要なユーザーロールに応じて、ワークフロー管理者と通常の管理者を区別する必要があります。 その場合は、以下の手順に従ってください。

1.   ワークフロー管理者のための新しいユーザーロールを作成します。
2.   Workflow Commonsの **管理者** モジュールロールにユーザーロールをリンクします。
3.   ユーザーロールを **ユーザー** と **WorkflowAdministrator** モジュールロールの両方にリンクします。

最後に [プロジェクト設定](project-settings#workflows) の format@@2 タブに移動し、Workflow Commons で使用しているユーザーと同じユーザーエンティティを選択します。 Mendix SSO を使用している場合は、 **MendixSSO.MendixSSOUser** に設定してください。 次に、このエンティティのプロパティを使用して、タスクをformat@@0プロパティでタスクを選択できるユーザーをフィルタリングできます。 ユーザー タスク プロパティの詳細については、 [ユーザー タスク](user-task) を参照してください。

## 5 ワークフローコモンズのカスタマイズ

Workflow Commonsはすぐに役に立つドキュメントを提供しますが、コンテンツを変更したり、ページを会社固有にするなどする必要がある場合があります。 その場合。 **WorkflowCommonsCustomizations**という名前のローカルモジュールに変更するドキュメントのコピーを作成することをお勧めします。 新しいバージョンにアップグレードする際に、将来の変更を誤って上書きしないようにします。 モジュールの **Private** フォルダを参照して、スニペットとサブマイクロフローを見つけることもできます。 ワークフローを構成し、ページやその他の要素を設定する方法の詳細については、 を参照してください [従業員のオンボーディングプロセスの Studio Pro でワークフローを構成する方法](/howto/logic-business-rules/workflow-how-to-configure)。

## ワークフローのベストプラクティス6選

ワークフローを扱う際には、以下のベストプラクティスをお勧めします。

*   ワークフローエンティティを作成する際、関連付けを使用して関連情報に接続し、現在のワークフローインスタンスに関連する属性のみを作成します。 An example could be an **Expense** entity containing a description and amount, associated with an **ExpenseApproval** entity which has attributes for the approval state and a reason for rejection.
*   ユーザータスクを作成する際に、対象となるユーザーの簡単な説明をタスクのキャプションに追加します。 例えば、 **HR: 従業員のオンボーディングワークフローでオンボーディングトレーニング** をスケジュールすることができます。
*   システムタスクのマイクロフローを作成するときは、 **WF\_**でプレフィックスを付けることで、ワークフローで使用されていることを誰もが知ることができます。

## 7 続きを読む

*   [ワークフロー](workflows)
*   [Studio Proで従業員のオンボーディングプロセスのワークフローを構成する方法](/howto/logic-business-rules/workflow-how-to-configure)

