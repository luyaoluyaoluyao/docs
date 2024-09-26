---
title: "特定の条件が満たされたときのみフィールドを表示"
category: "ページ"
description: "Mendix Studioで条件付き表示を設定する方法を説明します。"
menu_order: 30
tags:
  - "スタジオ"
  - "ページ"
  - "どうやって?"
  - "可視性"
  - "表示"
---

## 1つの紹介

この方法では、条件付き可視性を設定することで、特定の条件が満たされた場合にのみ、エンドユーザーにフィールドを表示する方法を説明します。

**以下の方法を教えてくれます。**

* エンドユーザーが特定の属性値を選択したときにのみフィールドを表示する
* 特定のユーザーロールに対してのみフィールドを表示する
* 表示フィールドは特定の条件下でのみ表示されます

以下のユースケースについて説明します。

You have a web shop and you want to show a field with a billing address only when a customer unchecked the **Billing address is the same as delivery address** option (it is checked by default):

![請求先住所は配送先住所と同じです](attachments/pages-how-to-set-visibility/billing-address-same.png)

また、 **製品概要** というページがあり、リストの **編集** ボタンを管理者および営業マネージャーのみに表示するようにします。

{{% image_container width="450" %}}

![商品一覧](attachments/pages-how-to-set-visibility/list-of-products.png)

{{% /image_container %}}

ドメインモデルは次のようになります:

{{% image_container width="550" %}}

![ドメインモデル](attachments/pages-how-to-set-visibility/domain-model.png)

{{% /image_container %}}

次のユーザーロールがあります:

![ユーザーの役割](attachments/pages-how-to-set-visibility/user-roles.png)

セキュリティを有効にし、ユーザーロールを設定する方法の詳細については、 [アプリのセキュリティを確保し、その機能へのアクセスを設定する方法](security-how-to-configure-roles) を参照してください。

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio8/page-editor) を参照してください。
* 条件付きの可視性で自分自身をよく理解する。 詳細については、 [条件付き表示セクション](/studio8/page-editor-widgets-visibility-section) を参照してください。
* セキュリティを有効にし、ユーザーロールをアプリに追加します。 詳細については、 [アプリを保護し、その機能へのアクセスを構成する方法](security-how-to-configure-roles) を参照してください。
* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio8/domain-models) を参照してください。

## 3 請求先住所の条件の設定

*条件付き可視性* は、特定の条件が満たされたときにのみウィジェットを表示できるプロパティのセットです。

請求先住所の可視性は、顧客が請求先住所と異なることを確認するかどうかによって異なります。 In your domain model, you have an attribute of the Boolean type called **BillingAddressSame**, so when it is set to *false*, the billing address should be visible. This means that the visibility of the billing address depends on the value of the **BillingAddressSame** attribute, so the conditional visibility is *attribute-based*.

{{% alert type="info" %}}

属性ベースの条件付き可視性は、データコンテナ内にあるウィジェット(データビュー、リストビュー、またはデータグリッド)にのみ設定できます。

{{% /alert %}}

**Billing Address** フィールドに条件付き表示を設定するには、以下を行ってください:

1. 顧客が自分の詳細を指定するページを開きます:

    ![顧客詳細](attachments/pages-how-to-set-visibility/customer-page.png)

2. **請求先住所** フィールドを選択し、そのプロパティに移動します。

3. **条件付き可視性** セクションで、 **Attribute-Based** プロパティをクリックします。

    {{% image_container width="250" %}}![Conditional Visibility Section](attachments/pages-how-to-set-visibility/conditional-visibility-section.png){{% /image_container %}}

4. **属性の選択** ダイアログボックスで、 **BillingAddressSame** 属性を選択し、 **Select** をクリックします。

5. **属性値** プロパティがプロパティに表示されるようになりました。 Untick the *True* value as it does not meet the conditions you would like to set, and leave the **False** value selected:

    {{% image_container width="250" %}}![Attribute-Based Visibility](attachments/pages-how-to-set-visibility/attribute-based-visibility-set.png){{% /image_container %}}

よくできました！ If you [preview your app](/studio8/publishing-app), you will see that the billing address is only shown when you untick the  **Billing address is the same as delivery address** option.

## 4 特定のユーザーロールにのみ要素を表示する

 **編集** ボタンを持つ製品のリストがあります。 アプリには3つのユーザロールがあります: **管理者**、 **Sales_Managers**、および **顧客**、 そして、このボタンを管理者と営業マネージャーのみに表示し、顧客から非表示にします。 ユーザーロールの作成方法については、 [アプリのセキュリティ保護とその機能へのアクセスの構成](security-how-to-configure-roles) を参照してください。

特定のユーザーロールにのみ要素を表示するには、次の操作を行います。

1. **製品概要** ページを開き、 **** ボタンを選択します。

    {{% image_container width="450" %}}![List of Products](attachments/pages-how-to-set-visibility/list-of-products.png){{% /image_container %}}

2. プロパティを開き、 **条件付き可視性** セクションで **ロールベースの** プロパティを切り替えます。

    {{% image_container width="250" %}}![Role-Based Property](attachments/pages-how-to-set-visibility/role-based-property.png){{% /image_container %}}

3. アプリケーションで利用可能なロールのリストは、 **ロール** プロパティに表示されます。 **顧客** のロールのチェックを外します:

    {{% image_container width="250" %}}![Unselected Roles](attachments/pages-how-to-set-visibility/unselected-roles.png){{% /image_container %}}

よくできました！ **編集** ボタンは、 **管理者** および **Sales_Manager** のユーザロールのみに表示されます。

## 条件付き可視性を持つ3つの項目を表示

ページのどの要素が条件付き可視性を持っているかを簡単に見つけるには、それらを強調表示できます。 条件付き表示のウィジェットを表示するには、次の操作を行います。

1. ページを開きます。

2. ページの左上隅にある目のアイコンをクリックします。

    {{% image_container width="250" %}}![Eye Icon](attachments/pages-how-to-set-visibility/eye-icon.png){{% /image_container %}}

条件付き表示のウィジェットがハイライト表示されます:

![ハイライトされたウィジェット](attachments/pages-how-to-set-visibility/highlighted-widget.png)

おめでとうございます ウィジェットにいくつかの条件を設定し、これらのウィジェットを簡単に見つけられるようにページで表示する方法を学びました。

アプリをプレビューし、設定した条件をテストすることができます: 請求先住所が表示されている場合と、どのユーザーロールが **編集** ボタンを表示できます。 ページをプレビューする方法の詳細については、 [プレビュー中 & アプリを公開する](/studio8/publishing-app) を参照してください。
