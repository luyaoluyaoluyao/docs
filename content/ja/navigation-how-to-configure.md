---
title: "ナビゲーションバーの設定"
description: "この方法では、Mendix Studio でナビゲーション バーを構成するプロセスを説明します。"
menu_order: 15
tags:
  - "スタジオ"
  - "navigation"
  - "どうやって?"
  - "ナビゲーションバー"
---

## 1つの紹介

この方法では、メニュー項目やサブ項目などのアプリケーションのナビゲーションバーを設定する方法を説明します。

**以下の方法を教えてくれます。**

* ページをホームページとして設定する
* 新しいメニューバーアイテムとサブアイテムを作成

この方法では、次のようなユースケースを説明します。

アプリのメニューバーを設定します。

Studio では、ナビゲーションバーはほとんどのページテンプレートで構築され、ページ上でサイドバーまたはトップバーとして使用できます。 設定されたメニューバーは次のようになります:

![設定されたメニュー](attachments/navigation-how-to-configure/navigation-previewed.png)

現在、デフォルトのホームページとして設定されている **Home_Web** というページがあり、ホームメニュー項目にも設定されています。 現在のナビゲーションドキュメントは次のようになります:

![ナビゲーション デフォルト](attachments/navigation-how-to-configure/navigation-default.png)

ナビゲーションに追加したい複数のページがあります。

* **Employees** - 会社のすべての従業員をリストし、デフォルトのホームページにするページ。

* **新規_従業員** - 新規従業員を作成するためのページ

* **Job_Details** – contains a list with such details as employee's position, department, income; you would like to keep this page together with other two pages listed below under one menu item called  **Employee_Details**

* **Personal_Info** – contains a list with personal employee information, such as full name, emergency contacts, address; should be a menu sub-item of the **Employee_Details** menu item

* **Documents** – contains a list with employee files, such as employment contract, medical insurance; should be a menu sub-item of the **Employee_Details** menu item

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio/page-editor) を参照してください。
* ナビゲーション文書の用語に慣れてください。 詳細については、 [ナビゲーションドキュメント](/studio/navigation) を参照してください。
* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio/domain-models) を参照してください。

## 3 メニュー項目とサブ項目を作成する

### 3.1 従業員ページをデフォルトのホームページに設定する {#employees-page}

現在、 **Home_web** ページがあなたのアプリのホームページとして設定されています。 ただし、 **Employees** ページをホームページとして設定する必要があります。 次の操作を行います:

1. 左のメニューバーの **ナビゲーション ドキュメント** アイコンをクリックします。

2. ナビゲーションエディターのプロパティを開く > **デフォルトのホームページ**.

3. **ページ** プロパティをクリックして別のページを選択します。

    ![デフォルトのホームページ](attachments/navigation-how-to-configure/default-home-page.png)

4. **ページの選択** ダイアログボックスで、 **Employee** を選択し、 **Select** をクリックします。

5. 今度は、 **ホーム** メニューアイテムの **従業員** ページを設定する必要があります。それ以外の場合はナビゲーションツリーに表示されません。 **ホーム** メニュー項目をクリックし、そのプロパティを開きます。

6. **ページ** プロパティをクリックします。

    ![ホームメニュー項目](attachments/navigation-how-to-configure/home-menu-item.png)

7. **ページの選択** ダイアログボックスで、 **Employee** を選択し、 **Select** をクリックします。

**従業員** ページをアプリの新しいデフォルトのホームページとして設定しました。

### 3.2 新規従業員ページのメニューアイテムの作成

The **New_Employee** page contains a form with the details of the new employee, this means that it contains a data view that expects an *Employee* object. したがって、メニュー項目を作成する場合は、このオブジェクトを渡す必要があります。

**新規_従業員** ページのメニュー項目を作成するには、次の操作を行います。

1. ナビゲーション ツリーの下部にあるプラスをクリックして、メニュー アイテムを作成します:

    ![メニューアイテムを追加中](attachments/navigation-how-to-configure/adding-menu-item.png)

2. 新しいメニュー アイテムのプロパティを開き、次の操作を行います:

    1.  **on Click Action** を **Page** に設定します。

    2. **Create Object** オプションを切り替えて、 *Employee* オブジェクトをページに渡します。

    3. 必要なエンティティを設定するには、 **Entity** プロパティをクリックします。

        ![オブジェクトを作成](attachments/navigation-how-to-configure/create-object.png)

    4. **図形の選択** ダイアログボックスで、 **Employee** を選択し、 **Select** をクリックします。

    5. **ページ** プロパティをクリックします。

    6. **ページの選択** ダイアログボックスで、 **新規_従業員** ページを選択し、 **** をクリックします。

    7. **図表番号** プロパティで、 *ナビゲーション項目* 図表番号を削除し、 *新規従業員* と入力します。

    8. **アイコン** プロパティをクリックして、メニュー項目のアイコンを設定します。

    9. **アイコンの選択** ダイアログボックスで、 *+* アイコンを検索し、 **Select**:

         ![プラスアイコンを選択](attachments/navigation-how-to-configure/plus-icon.png)

よくできました！ ナビゲーションに **新規従業員** ページのメニュー アイテムを追加しました:

![新しいメニューアイテムが作成されました](attachments/navigation-how-to-configure/new-menu-item-created.png)

右上の **プレビュー** をクリックして、 [アプリをプレビュー](/studio/publishing-app) し、ナビゲーションメニューがどのように見えるかをテストします。 ![プレビューしたメニュー項目](attachments/navigation-how-to-configure/previewed-menu-items.png)

### 3.3 Employee_Details ページのメニュー項目を作成し、そのサブ項目を設定する

You would like to place **Job_Details**, **Personal_Info**, and **Documents** pages under one menu-item named **Employee Details**, which means that they will be opened by menu sub-items.

まず、3つのメニューサブアイテムを含むメニューアイテムを作成する必要があります。 次の操作を行います:

1. ナビゲーションツリーの下部にあるプラスをクリックしてメニュー項目を作成します。

2. 新しいメニュー アイテムのプロパティを開き、次の操作を行います:

    1. **図表番号** プロパティで、 *ナビゲーション項目* 図表番号を削除し、 *従業員の詳細* を入力します。
    2. **アイコン** プロパティをクリックして、メニュー項目のアイコンを設定します。
    3. **アイコンの選択** ダイアログボックスで、 *ユーザー* アイコンを検索し、 **選択** をクリックします。

3. *の横の* **従業員の詳細** メニュー項目の横にある format@@4 をクリックして、サブ項目を作成します。

    ![メニューサブ項目の作成](attachments/navigation-how-to-configure/creating-menu-sub-item.png)

4. プロパティを開き、次の操作を行います。

    1. **on Click Action** を **Page** に設定します。

    2. **ページ** プロパティをクリックします。

    3. **ページの選択** ダイアログボックスで、 **Job_Details** ページを選択し、 **Select** をクリックします。

    4. **図表番号** プロパティで、 *ナビゲーション項目* 図表番号を削除し、 *ジョブ詳細* を入力します。

        ![ジョブ詳細のプロパティ メニュー サブアイテム](attachments/navigation-how-to-configure/job-details-menu-item-properties.png)

    5. ステップ1-4を繰り返し、メニューサブ項目を作成して **Personal_Info** ページを開き、このサブ項目 *個人情報*と名付けます。

    6. 手順 1-4 を繰り返して、メニュー サブ項目を作成し、 **ドキュメント** ページを開き、このサブ項目に *ドキュメント* という名前を付けます。

    7. サブアイテムの順序は次のようになります: **ドキュメント**, **個人情報**, **作業詳細**. Drag and drop them to rearrange the order in the following way: **Job Details**, **Personal Info**, **Documents**.

**従業員の詳細** メニューアイテムのサブメニューアイテムを構成していること。

おめでとうございます アプリのナビゲーションを作成しました：

![ナビゲーションの設定](attachments/navigation-how-to-configure/configured-navigation.png)

[アプリをプレビューする](/studio/publishing-app) ナビゲーションメニューがどのように表示されるかを確認するには:

![プレビューナビゲーション](attachments/navigation-how-to-configure/navigation-previewed.png)

