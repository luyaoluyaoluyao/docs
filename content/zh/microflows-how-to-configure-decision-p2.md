---
title: "第 2 步：将微流程嵌入您的应用程序"
parent: "microflow-how to config-decision"
description: "如何描述在 Mendix Studio 中配置决策的过程。"
menu_order: 20
tags:
  - "工作室"
  - "微流"
  - "决 定"
  - "页面"
---

## 1 导言

在 [前一步](microflows-how-to-configure-decision-p1)中，您已配置了微流程和校验属性类型和布尔属性类型的判定。 现在您可以通过添加它们到页面来验证微流。 这个如何解释您如何可以在 Mendix Studio 中添加决策微流程。

**这个教程将教你如何做以下事情：**

* 将创建的微流程嵌入到您的页面

## 2 个前提条件

要启动此教程，请确保您已完成以下前提条件：

* [第 1 步：构建域模型 & 配置微流](microflows-how-to-configure-decision-p1)

## 3 嵌入微流程到页面

在创建微流程后，您可以将它们添加到页面以便在您的应用程序中运行。

### 3.1 将微流程与枚举类型属性嵌入中 {#embedding-decision-enumeration}

若要将微流与决策(枚举类型的属性)嵌入到页面，请做以下操作：

1. 为现有客户详细信息创建一个页面并命名 *Customer_details*。 欲了解更多关于创建页面的信息，请参阅 [在 *页面* 中创建一个新页面](/studio/page-editor) 部分。

2.  在 **工具箱** > **小部件** > **数据容器**, 找到 **数据视图**.

    ![](attachments/microflows-how-to-configure-decision/data-view.png)

3. 拖拽 **数据视图** 到页面。

4.  在数据视图的 **属性** 标签中，执行以下操作：

    1. 将 **数据源** 设置为 **上下文。**
    2. 将 **实体** 设置为 **客户**。

        ![](attachments/microflows-how-to-configure-decision/data-view-properties.png)

5. 在 **工具箱**>**小部件** >**按钮** 找到 **创建对象**, 拖放到数据视图容器内(默认名称是 **新**)。

6. 您将创建一个新的页面，在用户点击 **新的** 按钮时将被打开。 打开已创建按钮的 **属性** 标签，执行以下操作：

    1. 设置 **客户** 为 **实体** 在 **事件** 部分。
    2. 点击 **选择页面**。

        ![](attachments/microflows-how-to-configure-decision/create-button-properties.png)

    3. 在 **选择页面** 对话框中，点击右上角的加号图标。
    4. 在 **创建新页面** 对话框，填写页面标题，例如 *新客户*。
    5. Tick **基于客户实体** 预填充页面内容，然后点击 **创建**

        ![](attachments/microflows-how-to-configure-decision/pre-fill-contents.png)

   包含客户详细信息的页面已生成。

7. 返回 **Customer_details** 页 和 in **工具箱**>**小部件** >**数据容器**, 找到 **列表视图**，拖放到页面。

8. 为列表视图打开 **属性** 并将 **客户** 设置为 **数据源**>**实体**.

9. 在 **工具箱** > **构建块** > **列表** 选择 **邮件列表4**拖放到列表视图中。

    ![](attachments/microflows-how-to-configure-decision/list-view-list4.png)

10. 从列表视图中删除以下元素：

    1. 带字幕的**TEXT**部件。
    2. **IMAGE** 部件。

11. Open the **Properties** of the **Details** button, and do the following:

    1. 设置 **事件**>**点击动作** 到 **微流程**。
    2. 点击 **选择微流** 并设置 **显示级别指定页面**。

        ![](attachments/microflows-how-to-configure-decision/details-button-microflow.png)

恭喜！ 现在用户点击 **详情**时，将打开相应客户等级的表格。

您现在可以 [预览您的应用程序](/studio/publishing-app) 或发布它。

### 3.2 将微流程带有布尔型属性的决定

若要将微流与决定嵌入(布尔类型的属性)，请执行以下操作：

1. 您需要添加一个选项来将客户标记为已屏蔽。 要做到这一点，请打开上一部分创建的 **新客户** 页面。 欲了解更多信息，请参阅 [将微流程与枚举类型的属性结合起来。](#embedding-decision-enumeration)。

2. 在 **工具箱** > **小部件** > **输入元素** 选择 **单选按钮**, 拖放此部件到 **数据视图** 容器。

3.  在无线电按钮的 **属性** 中，点击 **数据源** > **属性** 并选择 **被屏蔽的布尔值**。 这是在你的页面上看起来像样的方式：

    ![](attachments/microflows-how-to-configure-decision/new-customer-page-blocked-attribute.png)

4. 现在您将添加微流程到页面。 打开页面 **Order_form_for_bronze_customers**

5.  在 **工具箱** > **小部件** > **数据容器**, 找到 **数据视图**.

    ![](attachments/microflows-how-to-configure-decision/data-view.png)

6.  拖拽 **数据视图** 到页面。

    ![](attachments/microflows-how-to-configure-decision/data-view-select-data-view-source.png)

7.  在数据视图的 **属性** 中，执行以下操作：

    1. 将 **数据源** 设置为 **上下文。**
    2. 将 **实体** 设置为 **客户**。

        ![](attachments/microflows-how-to-configure-decision/data-view-properties.png)

8. 在 **工具箱**>**小部件**>**按钮**, 找到 **通话微流** 按钮，拖拽到 **数据视图** 容器。

    ![](attachments/microflows-how-to-configure-decision/call-microflow-button-in-data-view.png)

9. 点击 **调用 Microflow** 按钮查看其属性。

10. 在 **属性** 选项卡中，选择 **Customers_status_check microflow**。

    ![](attachments/microflows-how-to-configure-decision/call-microflow-button-selected-microflow.png)

11. 更改 **标题** 从 **微流** 到 **下订单**。

12. 打开页面 **Order_form_for_silver_customs** 并重复步骤 4-11.

13. 打开页面 **Order_form_for_gold_customs** 并重复步骤 4-11.

恭喜！ 当最终用户点击 **下单**时，只有未被阻止的客户才能够继续。 如果客户被阻止，他们将收到一条错误消息。

您可以预览和/或发布您的应用程序。 关于如何预览和发布应用程序的更多信息，请参阅 [预览 & 发布您的应用程序](/studio/publishing-app)
