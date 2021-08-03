---
title: "ウィジェット内のイベントセクション"
parent: "page-editor-widgets"
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

In the **Events** section, you can set the **On Click Action** for widgets and specify what action will be performed when users click the widget. たとえば、ユーザーがプロフィール画像をクリックすると、ユーザーの個人アカウントを持つページが開きます。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/events-section.png)
{{% /image_container %}}

## 2 クリックアクション {#on-click-action}

クリック操作に関する説明は以下の通りです:

* **なし** - ユーザーがウィジェットをクリックしたときにアクションは実行されません
* **ページ** – 指定されたページが開きます
  * **Create Object** – 新しいオブジェクトを作成し、選択したページに渡します (デフォルトでは無効)。 詳しい情報については、 [2.1 オブジェクトの作成オプション](#create-object-option) セクションを参照してください。
* **Microflow** - 選択したマイクロフローが実行されます
* **詳細** - 以下のタイプのアクションが含まれています:
  * **Save Changes** – ページで行われたすべての変更を保存(コミット)
  * **Cancel Changes** – ページ上のすべての変更をロールバックします
  * **ページを閉じる** - ポップアップウィンドウを閉じるか、以前に訪問したページに移動します
  * **サインアウト** – 現在のユーザーがアプリからログアウトしています
  * **Open Link** - リンクタイプに基づいたアクションをトリガーします（詳細については、セクション [2.2 Open Link Action](#open-link-action) を参照してください。
  * **オブジェクトの削除** - オブジェクトを削除 (詳細については、 [2.3 オブジェクトのアクションの削除](#delete-object-action) セクションを参照してください)

{{% alert type="info" %}}

クリック操作のリストは、ウィジェットによって異なる場合があります。 例えば、 **Delete Object** on-click action はリストビューでは使用できません。

{{% /alert %}}

### 2.1 オブジェクトの作成オプション {#create-object-option}

**On Click Action** を **Open Page**に設定すると、 **Create Object** オプションを有効にすることができます。 選択したページがコンテキストを想定している場合は、オブジェクトを渡す必要があります。

例を見てみましょう: **New** ボタンをクリックして、新しい顧客を作成します。 このボタンは、新しい顧客の詳細を入力して保存できるページを開きます。 However, the *Customer Details* page needs to get data first, in other words, it expects the object *Customer* to be passed to it.

{{% image_container width="350" %}}![データビューが顧客オブジェクトを期待する](attachments/consistency-errors-pages/data-view-customer.png)
{{% /image_container %}}

Thus, when setting the on-click action of the **New** button to **Page**, you need to enable the **Create Object** option and select the **Customer** entity.

![](attachments/page-editor-widgets-events-section/create-object-example.png)

**Create Object** オプションを有効にするには、次のように設定する必要があります。

* **ページ** - 新しく作成されたオブジェクトで表示するページを指定します。 このページには、このオブジェクトを期待するデータビューが含まれている必要があります。
* **エンティティ** – コンテキストとして選択したページにエンティティを作成し、渡すオブジェクトを指定します。

### 2.2 リンクを開くアクション {#open-link-action}

**On Click Action** を **Open Link**に設定すると、いくつかのプロパティが利用できます。

{{% image_container width="300" %}}![](attachments/page-editor-widgets-events-section/open-link-action.png)
{{% /image_container %}}

以下の表の説明を参照してください。

| アクションプロパティ | 説明                                                                                                                                                                                                                                                                                                                                        |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Link Type  | **リンクタイプ** の値は以下のとおりです。 <ul><li>**Web** – ウェブサイトにナビゲートします</li><li>**メール** – メールを作成</li><li>**電話** – 通話を開始</li><li>**テキストメッセージ** – テキストメッセージを送信</li></ul>                                                                                                                                                                                                                                                                                          |
| ソース        | **ソース** の可能な値は以下のとおりです: <ul><li>**リテラル値を使用** – 値を入力することができます (**Web**に**URL**を指定し、**受信者**を**電子メール**に、**電話番号**を**電話カル**と**メッセージ**にします) </li><li>**属性を使用** – リストビューのデータソースとして**データベース**>**エンティティ**を選択した場合。 エンティティに属する文字列型の属性を選択したり、新しい属性を作成したりできます（**属性を使用** オプションが設定されている場合） 手動で情報を記入する必要はありません。動的に更新されます)</li></ul>{{%alert type="info" %}}When you configure **Email**, **Phone Call** or **Message** options, the corresponding default app will be opened on the device when the action is triggered, for example, the default email client will be opened to compose a message.<br />{{%/alert %}} |

### 2.3 オブジェクトの削除アクション {#delete-object-action}

**Delete Object** アクションの動作は、配置されているデータコンテナに依存します。 [リストビュー](page-editor-data-view-list-view#list-view-properties) または [データビュー](page-editor-data-view-list-view#data-view-properties)。

#### 2.3.1 リストビューのオブジェクトアクションの削除

リストビューに **Delete Object** を配置した場合。 ユーザーがボタンをクリックすると、対応するリストビュー項目が削除されます。

たとえば、顧客名を表示するリストビューのページがあります。 **削除** ボタンは、各名前の隣にリスト内に配置されます。 したがって、「Peter」という行で **Delete** をクリックすると、この顧客とすべての顧客の詳細が削除されます。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/list-view-delete.png)
{{% /image_container %}}


#### 2.3.2 データビューでのオブジェクトアクションの削除

データビューに配置された場合、 **Delete Object** は接続されているオブジェクトを削除します。 たとえば、顧客の詳細が記載されたページを開きました。 詳細はデータ ビューに配置されます。 ページ下部に **保存** と **削除** ボタンがあります。 **削除**を押すと、顧客の "John" と顧客の詳細が削除され、ページが閉じられます。

{{% image_container width="350" %}}![](attachments/page-editor-widgets-events-section/data-view-delete.png)
{{% /image_container %}}

## 3 続きを読む

* [ウィジェット](page-editor-widgets)
