---
title: "フィールドを読み取り専用または必須として設定"
category: "ページ"
description: "Mendix Studio で検証と編集性を設定する方法を説明します。"
menu_order: 20
tags:
  - "スタジオ"
  - "ページ"
  - "フォーム"
  - "どうやって?"
  - "検証"
  - "必須"
  - "読み取り専用"
  - "編集性"
---

## 1つの紹介

この方法では、フォーム内のフィールドを必要に応じて、または読み取り専用で構成する方法を説明します。

**以下の方法を教えてくれます。**

* 編集可能性を設定して、読み取り専用としてフィールドを設定します
* バリデーションを設定して、必須項目を構成します。

以下のユースケースについて説明します。

お客様には、契約内容や個人情報など、従業員が自身の情報を表示および編集できる人事アプリがあります。 従業員詳細ページがあります：

{{% image_container width="600" %}}
![](attachments/pages-how-to-set-validation-and-editability/employee-details-page.png)
{{% /image_container %}}

このページのいくつかのフィールドを(必須)記入し、読み取り専用にしたいと考えています。

Domain model is configured the following way in this use case:

{{% image_container width="250" %}}
![](attachments/pages-how-to-set-validation-and-editability/domain-model.png)
{{% /image_container %}}

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio8/page-editor) を参照してください。
* 入力要素の編集可能性と入力検証プロパティに慣れています。 詳細については、 [入力要素](/studio8/page-editor-widgets-input-elements#editability) の [](/studio8/page-editor-widgets-input-elements#validation) セクションと *入力検証セクション* を参照してください。
* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio8/domain-models) を参照してください。

## 3 読み取り専用として項目を設定する

次の従業員の詳細を読み取り専用にしたい場合:

* 従業員番号
* コントラクトタイプ

フィールドを読み取り専用にするには、次の操作を行います。

1. **従業員詳細** ページを開きます。

2. **[** ] フィールドを選択し、そのプロパティを開きます。

    {{% image_container width="600" %}}![](attachments/pages-how-to-set-validation-and-editability/contract-type.png){{% /image_container %}}

3. **一般** セクションで、 **編集可能性** プロパティを読み取り専用に設定します。

    {{% image_container width="250" %}}![](attachments/pages-how-to-set-validation-and-editability/editability.png){{% /image_container %}}

4. **Employee 番号** フィールドを選択し、そのプロパティを開きます。

5. **一般** セクション > **編集可能性**, すでに読み取り専用に設定されており、このプロパティは変更できません。 これは、ドメインモデルの **EmployeeNumber** 属性が *autonumber* 型であるためです。 つまり、この番号は自動的に生成され、編集できません。

    ![](attachments/pages-how-to-set-validation-and-editability/autonumber-read-only.png)

**Employee number** と **Contract type** フィールドが読み取り専用になりました。 灰色表示になっておりエンドユーザーは編集できなくなります

{{% image_container width="600" %}}![](attachments/pages-how-to-set-validation-and-editability/read-only-configured.png){{% /image_container %}}

## 4 必須項目として設定

従業員に必須項目として次の項目を設定します:

* 名前
* 住所
* Eメールアドレス
* 電話番号

必要に応じてフィールドを設定するには、次の操作を行います:

1. **従業員詳細** ページを開きます。

2. **Name** フィールドを選択し、そのプロパティを開きます。

3. **Input Validation** セクションで、 **Validation Type** プロパティを **Required** に設定します:

    {{% image_container width="250" %}}![](attachments/pages-how-to-set-validation-and-editability/validation-type-required.png){{% /image_container %}}

4. 従業員がこのフィールドを空のままにしようとすると、フィールドの下にエラーメッセージが表示されます。 **メッセージ** プロパティにこのメッセージを指定します:

    {{% image_container width="250" %}}![](attachments/pages-how-to-set-validation-and-editability/validation-message.png){{% /image_container %}}

5. **アドレス**、 **メール**、および **電話** の項目についても、ステップ2-4 を繰り返し、必要に応じて設定します。

よくできました！ Now when an employee attempts to leave **Name**, **Address**, **Email**, or **Phone** fields empty and tries to save changes, an error message will be displayed under the field saying "This field is required":

{{% image_container width="600" %}}![](attachments/pages-how-to-set-validation-and-editability/validation-example.png){{% /image_container %}}

すべての必須項目が入力されるまで変更は保存されません。

おめでとうございます 項目を読み取り専用として設定しており、従業員の詳細を持つフォームに必須です。

アプリをプレビューしてページをテストできるようになりました。 ページをプレビューする方法の詳細については、 [プレビュー中 & アプリを公開する](/studio8/publishing-app) を参照してください。

また、アプリケーションに新しい機能を追加することもできます。たとえば、従業員が出張レポートに画像を添付できるようになります。 詳細については、 [エンドユーザーが画像を添付できるようにする方法](pages-how-to-attach-images) を参照してください。