---
title: "条件付き表示セクション"
parent: "page-editor-widgets"
description: "Mendix Studio のウィジェットのプロパティで条件付き表示セクションを説明します。"
menu_order: 30
tags:
  - "スタジオ"
  - "ページエディタ"
  - "ウィジェット"
  - "クリックアクション"
  - "イベント"
---

## 1つの紹介

ウィジェット プロパティの **条件付き可視性** セクションでは、特定の条件が満たされたときにのみウィジェットを表示できます。 次の条件に基づいてウィジェットを表示することができます。

* [ウィジェットの属性値](#attribute-based)
* [アプリのユーザーロール](#role-based)

例えば、 Webショップを持っていて、配達先住所が請求先住所と一致した場合に同じ住所を2回入力する必要はありません。 ユーザーが **請求先住所が配送先住所** オプション（デフォルトでチェックされている）と同じチェックを外した場合にのみ請求先住所を入力するフィールドを表示します。 この場合、 *属性値*に基づいて請求先住所フィールドを表示させることができます: フィールドは *BillingAddressSame* のチェックが外されている場合にのみ表示されます ( *false* に設定):

![](attachments/page-editor-widgets-visibility-section/attribute-based-example.png)

特定の *ユーザー ロール* にのみウィジェットを表示することもできます。 たとえば、給与金額を財務マネージャーにのみ表示するウィジェットを表示できます。

条件付き表示が設定されているウィジェットを確認するには、 目のアイコンをクリックすると、ページの左上隅にある **表示** オプションが表示されます。 ![](attachments/page-editor-widgets-visibility-section/highlight-conditional-items.png)

## 2 条件付き可視性プロパティ

選択した属性値および/またはユーザロールに基づいて条件付き表示を有効にできます。 条件付き可視性プロパティについては、以下で説明します。

### 2.1 属性ベース {#attribute-based}

**Attribute-Based** の可視性では、選択した属性の特定の値に一致する場合にのみウィジェットを表示できます。

{{% alert type="info" %}}

属性は、ブール型または列挙型でなければなりません。

{{% /alert %}}

{{% alert type="info" %}}

データコンテナ:データビューまたはリストビューにウィジェットが配置されている場合にのみ、属性ベースの条件付き表示を設定できます。

{{% /alert %}}

### 2.2 属性値

このプロパティは、 [Attribute-Based](#attribute-based) プロパティの属性が選択されている場合にのみ表示されます。 **属性値** プロパティでは、特定の属性値を選択できます。

例えば、 **Gold** グレードの顧客にのみ特別オファー価格を表示したいとします。 Select *Grade* in the **Attribute-Based** property and *Gold* in as the **Attribute Value**:

{{% image_container width="300" %}}
![](attachments/page-editor-widgets-visibility-section/attribute-based-visibility.png)
{{% /image_container %}}

### 2.3 ロールベース {#role-based}

ウィジェットは、アプリケーションで利用可能なユーザーロールの特定に表示させることができます。 有効にすると、この設定は選択したユーザーロールのいずれかにリンクされているすべてのユーザーにウィジェットを表示します。

{{% alert type="info" %}}

セキュリティが有効な場合にのみ、ロールベースの条件付き表示を設定できます。 詳細については、 [セキュリティ、ロール & 権限](settings-security) を参照してください。

{{% /alert %}}

### 2.4 ロール

**ロール** プロパティは、 [ロール ベースの](#role-based) プロパティが有効な場合にのみ表示され、アプリケーションで使用可能なロールのリストが表示されます。 ウィジェットを表示させるロールを選択します。 たとえば、タクシーの予約アプリで お客様や管理者にタクシー運転手を評価させたいのですが タクシー運転手からはっきり隠してください

{{% image_container width="300" %}}
![](attachments/page-editor-widgets-visibility-section/role-based-visbility.png)
{{% /image_container %}}

## 3 基本機能の実行

### 3.1 属性ベースの条件付き表示の設定

属性ベースの可視性を設定するには、次の操作を行います。

1. 特定の属性値にのみ表示したいウィジェットを選択し、そのプロパティに移動します。

2. **条件付き可視性** セクションで、 **Attribute-Based** プロパティをクリックします。

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/attribute-based-property.png){{% /image_container %}}

3. **属性の選択** ダイアログボックスで、ブール値または列挙型の属性を選択し、 **Select** をクリックします。

4. **属性値** プロパティがプロパティに表示されるようになりました。 設定したい条件を満たさない値のチェックを外します:

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/attribute-values.png){{% /image_container %}}

属性ベースの条件付き可視性はウィジェットに設定されます。

### 3.2 属性ベースの条件付き可視性を無効にする

属性ベースの可視性を無効にするには、以下の手順に従ってください。

1. 属性ベースの可視性を無効にしたいウィジェットを選択し、そのプロパティに移動します。

2. **条件付き可視性** セクションで、 **Attribute-Based** プロパティをクリックします。

3. **属性の選択** ダイアログボックスで、 **クリア** をクリックします。

    {{% image_container width="400" %}}![](attachments/page-editor-widgets-visibility-section/clear-attribute-based-visibility.png){{% /image_container %}}

属性ベースの条件付き表示がウィジェットでクリアされます。

### 3.3 ロールベースの条件付き表示の設定

ロールベースの条件付き可視性を設定するには、次の手順を実行します。

1. 特定のユーザー ロールにのみ表示したいウィジェットを選択し、そのプロパティに移動します。

2. **条件付き可視性** セクションで、 **ロール ベースの** プロパティを切り替えます。

3. アプリケーションで利用可能なロールのリストは、 **ロール** プロパティに表示されます。 ウィジェットを非表示にしたいロールのチェックを外します:

    {{% image_container width="300" %}}![](attachments/page-editor-widgets-visibility-section/role-based-example.png){{% /image_container %}}


ロールベースの条件付き可視性がウィジェットに設定されます。

### 3.4 ロールベースの条件付き表示を無効にする

ロールベースの条件付き表示を無効にするには、以下の手順に従ってください。

1. ロールベースの表示を無効にし、そのプロパティに移動するウィジェットを選択します。
2. **条件付き可視性** セクションで、 **ロール ベースの** プロパティを無効にします。

ロールベースの条件付き表示はウィジェットでは無効になります。

## 4 続きを読む

* [ウィジェット](page-editor-widgets)
* [セキュリティ、ロール & 権限](settings-security)
