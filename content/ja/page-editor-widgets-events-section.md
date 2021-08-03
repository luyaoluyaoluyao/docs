---
title: "イベントセクション"
parent: "page-editor-widgets"
menu_order: 70
description: "Mendix Studioのウィジェットのプロパティでformat@@0セクションを説明します。"
tags:
  - "スタジオ"
  - "ページエディタ"
  - "ウィジェット"
  - "クリックアクション"
  - "イベント"
---

## 1つの紹介

**イベント** セクションは **プロパティ** タブのセクションで、Mendix Studio の異なるウィジェットに共通しています。 たとえば、静的画像、ボタン、リストビュー、データビューなどです。

In the **Events** section, you can set the **On Click Action** for widgets and specify what action will be performed when end-users click the widget. たとえば、ユーザーがプロフィール画像をクリックすると、ユーザーの個人アカウントを持つページが開きます。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/events-section.png)
{{% /image_container %}}

## 2 クリックアクション {#on-click-action}

クリック操作の詳細は以下のとおりです。

* [なし](#do-nothing)
* [ページ](#show-page)
* [マイクロフロー](#microflow)
* [ワークフローに発信](#call-workflow)
* [ワークフローページを表示](#show-workflow-page)
* [タスクページを表示](#show-task-page)
* [Complete Task](#complete-task)
* [変更を保存](#save-changes)
* [変更をキャンセル](#cancel-changes)
* [ページを閉じる](#close-page)
* [サインアウト](#sign-out)
* [リンクを開く](#open-link-action)
* [オブジェクトを削除](#delete-object-action)

{{% alert type="info" %}}

使用可能なオンクリック操作のリストは、ウィジェットによって異なる場合があります。 例えば、 **Delete Object** on-click action はリストビューでは使用できません。

{{% /alert %}}

### 2.1 なし {#do-nothing}

アクションは実行されません。 このオプションは、基本機能をまだ定義せずにページを設定する場合に便利です。

### 2.2 ページ {#show-page}

**ページ** アクションは、指定したページを開きます。

このアクションに固有のプロパティは次のとおりです:

* **ページ** – 開くべき [ページ](page-editor)。

* **Create Object** – 新しいオブジェクトを作成し、選択したページに渡します (デフォルトでは無効)。 詳細については、以下の [オブジェクトオプションの作成](#create-object-option) セクションを参照してください。

#### 2.2.1 オブジェクトの作成オプション {#create-object-option}

**On Click Action** を **Page**に設定すると、 **Create Object** オプションを有効にすることができます。 選択したページがコンテキストを想定している場合は、オブジェクトを渡す必要があります。

たとえば、 **New** ボタンをクリックして新しい顧客を作成します。 このボタンは、新しい顧客の詳細を入力して保存できるページを開きます。 However, the *Customer Details* page needs to get data first, in other words, it expects the object *Customer* to be passed to it.

{{% image_container width="350" %}}![データビューが顧客オブジェクトを期待する](attachments/consistency-errors-pages/data-view-customer.png)
{{% /image_container %}}

Thus, when setting the on-click action of the **New** button to **Page**, you need to enable the **Create Object** option and select the **Customer** entity.

![](attachments/page-editor-widgets-events-section/create-object-example.png)

**Create Object** オプションを有効にするには、次のように設定する必要があります。

* **ページ** – 新しいオブジェクトを表示するページを指定します。 このページには、このオブジェクトを期待するデータビューが含まれている必要があります。
* **エンティティ** – コンテキストとして選択したページにエンティティを作成し、渡すオブジェクトを指定します。

### 2.3 マイクロフロー {#microflow}

**Microflow** アクションは、選択したマイクロフローを実行します。 マイクロフローを選択できる **Microflow** プロパティは、この操作に固有です。

### 2.4 ワークフローを呼び出す {#call-workflow}

**ワークフロー** アクションは指定されたワークフローを実行します。

このアクションに固有のプロパティは次のとおりです:

* **ワークフロー** – 実行すべき [ワークフロー](workflows)。
* **ページを閉じる** – 現在のページを閉じるかどうかを指定します。
* **コミット** – ワークフローを実行するときにオブジェクトをコミットするかどうかを指定します。

### 2.5 ワークフローページを表示 {#show-workflow-page}

**ワークフローページ** を表示すると概要ページ (管理者) が開きます。 このオンクリックアクションを持つ要素は、 **System.WorkflowInstance** エンティティに接続されたデータコンテナに配置する必要があります。

### 2.6 タスクページを表示 {#show-task-page}

**タスクページを表示する** は、プロパティで [ユーザー タスク](workflows-user-task) に設定された概要ページを開きます。 このオンクリックアクションを持つ要素は、 **System.WorkflowUserTask** エンティティに接続されたデータコンテナに配置する必要があります。

### 2.7 Complete Task {#complete-task}

**タスクの完了** アクションは、ワークフロー内の指定されたユーザー タスクを完了としてマークします。

このアクションに固有のプロパティは次のとおりです:

* **タスク** – 完了とマークされる [ユーザー タスク](workflows-user-task)。

* **結果** - 選択した [ユーザー タスク](workflows-user-task) の結果を一覧表示し、選択した結果に従います。 ユーザー タスクに結果が 1 つしかない場合、 **デフォルト** が結果として設定され、プロパティは編集できません。

* **ページを閉じる** – 現在のページを閉じるかどうかを指定します。

* **コミット** – タスクを完了としてマークするときにオブジェクトをコミットするかどうかを指定します。

### 2.8 変更を保存 {#save-changes}

**Save Changes** アクションは、ページに加えられたすべての変更を保存(コミット)します。

### 2.9 変更をキャンセル {#cancel-changes}

**キャンセル** アクションは、ページで行われたすべての変更をロールバックします。

### 2.10 ページを閉じる {#close-page}

**ページを閉じる** アクションはポップアップウィンドウを閉じるか、以前に訪問したページに移動します。

### 2.11 サインアウト {#sign-out}

**サインアウト** アクションは、現在サインインしているエンドユーザーにアプリからサインアウトします。

### 2.12 リンクを開くアクション {#open-link-action}

**Open Link** アクションは、リンクタイプに基づいてアクションをトリガーします:

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/open-link-action.png)
{{% /image_container %}}

このアクションに固有のプロパティは次のとおりです:

* **リンクタイプ** - リンクが実行するアクションを指定します。 **リンクタイプ** の値は以下のとおりです。

  * **Web** – ウェブサイトに移動します。

  * **Email** – メールを作成します。

  * **電話** – 電話を開始します。

  * **Text Message** – テキストメッセージを送信する。

    {{%alert type="info" %}} **Email**, **Phone Call** or **Message** options. アクションがトリガーされると、対応するデフォルトのアプリがデバイス上で開かれます。 例えば、メッセージを構成するためにデフォルトの電子メールクライアントが開かれます。

    {{%/alert %}}

* **Source** – 選択したリンクタイプと、リテラル値を使用するか、属性の値を使用するかによって異なります。 **ソース** の可能な値は以下のとおりです:

  * **Use literal value** – You can fill a value out (Specify **Url** for **Web**, **Recipient** for **Email**, and **Phone Number** for **Phone Cal**l and **Message**).
  * **Use attribute** – If you select **Database**>**Entity** as a data source for the list view,  you can choose the attribute of a string type that belongs to the entity or create a new one (when the **Use attribute** option is configured, you do not need to fill out any information manually, it will be updated dynamically).

### 2.13 オブジェクトアクションの削除 {#delete-object-action}

**Delete Object** アクションの動作は、配置されているデータコンテナに依存します。 [リストビュー](page-editor-data-view-list-view#list-view-properties) または [データビュー](page-editor-data-view-list-view#data-view-properties)。

#### 2.13.1 リストビューのオブジェクトアクションの削除

リストビューに **Delete Object** を配置した場合。 ユーザーがボタンをクリックすると、対応するリストビュー項目が削除されます。

たとえば、顧客名を表示するリストビューのページがあります。 **削除** ボタンは、各名前の隣にリスト内に配置されます。 したがって、「Peter」という行で **Delete** をクリックすると、この顧客とすべての顧客の詳細が削除されます。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/list-view-delete.png)
{{% /image_container %}}


#### 2.13.2 データビューでのオブジェクトアクションの削除

データビューに配置された場合、 **Delete Object** は接続されているオブジェクトを削除します。 たとえば、顧客の詳細が記載されたページを開きました。 詳細はデータ ビューに配置されます。 ページ下部に **保存** と **削除** ボタンがあります。 **削除**を押すと、顧客の "John" と顧客の詳細が削除され、ページが閉じられます。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/data-view-delete.png)
{{% /image_container %}}

## 3 続きを読む

* [ウィジェット](page-editor-widgets)
