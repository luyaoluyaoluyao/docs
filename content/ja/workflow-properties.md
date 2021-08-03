---
title: "ワークフローのプロパティ"
parent: "ワークフロー"
menu_order: 10
tags:
  - "ワークフロー"
  - "ワークフロー"
  - "ワークフローのプロパティ"
  - "Studio Pro"
---

## 1つの紹介

このドキュメントはワークフローのプロパティを説明します。 どのワークフローに対応しているか、どのような要素を使用できるかの詳細については、 [Workflow](workflows) を参照してください。

## 2 ワークフローのプロパティ

ワークフロー プロパティは、次のセクションで構成されています:

* [管理者ページ](#admin-page)
* [一般的な](#common)
* [データ](#data)
* [情報を表示](#display-info)
* [期限](#due-date)
* [全般](#general)
* [セキュリティ](#security)

### 2.1 管理ページセクション {#admin-page}

**管理者ページを上書きする** は、ワークフロー管理者にワークフローのインスタンスを表示するために使用される任意のページです。 これは、たとえば、アプリ内のワークフローインスタンスを表示するために使用される一般的なページを上書きします。 **ワークフロー管理ページ** を [オンクリックイベント](on-click-event#show-workflow-page) または [マイクロフローアクション](show-workflow-page) として設定し、このイベント/アクションで選択されたページをオーバーライドしたい場合。

**Workflow Commons** モジュールのテンプレートを使用してページを生成する場合、これらのテンプレートには必要なデータコンテナと関連するコンテキストエンティティが含まれます。

### 2.2 共通セクション {#common}

#### 2.2.1 名前 {#name}

**名前** はワークフロードキュメントの内部名です。 アプリでワークフローを参照する場合は、この名前を使用します。 モジュール内で一意である必要がありますが、異なるモジュール内で同じ名前を持つ2つのワークフローを持つことができます。 ワークフローを参照するとき 通常はモジュールの名前を付けて一意性を確保し、他のモジュールでワークフローを使用することができます。

ワークフローの **名前** を変更することはできませんが、 [図表番号](#general) を変更することができます。

#### 2.2.2 ドキュメント

**ドキュメント** を使用すると、ワークフローを簡単に説明することができます。

### 2.3 データセクション {#data}

**ワークフロー エンティティ** は、ワークフロー コンテキストとして使用されるエンティティです。 [システム](generalization-and-association) モジュールの **ワークフロー コンテキスト** エンティティの **** 専門化する必要があります。 System モジュール内のワークフロー関連エンティティの詳細について [ワークフロー](workflows#workflow-entities) の *システム モジュール* セクションにある format@@4 ワークフロー エンティティを参照してください。

ワークフローエンティティを「クリーン」、意味を保つことをお勧めします を使用すると、ワークフローの現在のインスタンスで重要な属性のみを持つようになり、関連付けを介して他のデータを追加できます。

![ドメインモデルの例](attachments/workflow-properties/domain-model-example.png)

### 2.4 情報セクション {#display-info}

#### 2.4.1 ワークフロー名

**ワークフロー名** は、属性として **ワークフロー** エンティティのシステム モジュールに格納されており、実行中のアプリで動的にデータを表示することができます。 If you are using the **Workflow Commons** module, the **Workflow name** is used on preconfigured pages: the Admin Center and Workflow Admin page.

**ワークフロー名** には、ブレース間で記述されるパラメータを含めることができます。例: {1}.

パラメータの使用に関する詳細は、以下の [パラメータ](#parameters) セクションを参照してください。

#### 2.4.2 ワークフローの説明

**ワークフローの説明** は、属性として **ワークフロー** エンティティのシステム モジュールに格納されており、実行中のアプリで動的にデータを表示することができます。 **Workflow Commons** モジュールを使用している場合は、 **Workflow description** がページテンプレートに使用されます。

**Workflow description** は、ブレース間で記述されるパラメータを含めることができます。例: {1}.

#### 2.4.3 パラメータ {#parameters}

パラメータは、その値が表示される属性です。 たとえば、 **FullName**  パラメータを使用してオンボーディングされている新しい従業員の名前を表示できます。

To view **Parameters**, click the ellipsis icon next to the **Workflow name** or **Workflow description** in properties depending on where you would like to display these parameters.

パラメータには以下の設定があります:

* **Index** - パラメータの識別番号
* **式** - 表示される XPath 式

##### 2.4.3.1 新しいパラメータの追加

**ワークフロー 名** または **ワークフロー 説明**にパラメータを追加するには、次の操作を行います:

1. **ワークフロー 名** または **ワークフロー 説明** の横にある省略記号アイコンをクリックします。

2. **Edit workflow name** dialog box > **Parameters** section, click the **New** button.

3. **テンプレートパラメーター (文字列)** ダイアログボックスで式を指定し、選択を確認します。

    ![属性の指定](attachments/workflow-properties/specifying-attribute.png)

    {{% alert type="info" %}}式で使用する属性が文字列型であることを確認してください。{{% /alert %}}

4. In the **Template** setting, write the text you would like to display and type **Index** of the parameter you would like to include. 以下の例では、新規採用者のフルネームを含めるには、 {1} インデックスを使用する必要があります:

    ![format@@0ダイアログ ボックス](attachments/workflow-properties/edit-workflow-name.png)

##### 2.4.3.2 パラメータに対するその他のアクションの実行

新しいパラメータの追加に加えて、パラメータに対して以下のアクションを実行できます。

* **Delete** – パラメータを削除するには、 **Delete** をクリックするか、キーボードの <kbd>Delete</kbd> を押します
* **編集** - パラメータをダブルクリックして編集するか、 **編集** をクリックします
* **Move up** – to move a parameter up in the list of parameters and also to change its index, click **Move up**
* **Move down** – to move a parameter down in the list of parameters and also to change its index, click **Move down**

### 2.5 締切セクション {#due-date}

**によって** によって指定された属性として **ワークフロー** エンティティのシステム モジュールに格納されており、実行中のアプリでそのデータを動的に表示することができます。 たとえば、ワークフローの期限を設定したり、アプリケーションに表示したりできます。 ただし、これは自動リマインダーではなく、ワークフローを追跡する際に期限を参照します。 If you are using the **Workflow Commons** module, **Due by** is used in page templates.

### 2.6 一般セクション {#general}

**説明** はワークフローのタイトルを定義します。 ワークフローの [名前](#name) を変更することはできませんが、 **図表番号** を変更することができます。

### 2.7 セキュリティセクション {#security}

**許可されたロール** は、ユーザがワークフローを実行できる必要がある [モジュールロール](module-security#module-role) を定義します。

{{% alert type="warning" %}}
これらのロールは、ワークフローがクライアントから実行された場合にのみチェックされます。
{{% /alert %}}

詳細については、 [モジュールセキュリティ](module-security) を参照してください。

## 3 続きを読む

* [Studio Proで従業員のオンボーディングプロセスのワークフローを構成する方法](/howto/logic-business-rules/workflow-how-to-configure)
* [ワークフロー](workflows)