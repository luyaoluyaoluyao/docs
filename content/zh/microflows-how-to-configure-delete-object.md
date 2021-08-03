---
title: "配置删除对象动作"
category: "微型流动"
menu_order: 80
description: "如何在数据视图和Mendix Studio列表视图中描述配置删除对象动作的过程。"
tags:
  - "工作室"
  - "页面编辑器"
  - "删除对象"
  - "列表视图"
  - "数据视图"
  - "如何处理"
---

## 1 导言

如何在Mendix Studio中配置删除对象动作。

**这个教程将教你如何做以下事情：**

* 在 [列表视图中配置 **删除对象** 动作](page-editor-data-view-list-view#list-view-properties)
* 配置 **在 [数据视图](page-editor-data-view-list-view#data-view-properties) 中删除对象** 动作

这个如何描述以下使用情况：你想要从客户列表中删除客户的名称。

{{% alert type="info" %}}

您可以在点击按钮或静态图像等小部件的动作时配置 **删除对象**。 在这个方法中， **删除** 按钮被用作一个小部件的示例， **删除对象** 点击动作。 For more information, see the [Delete Object Action](page-editor-widgets-events-section#delete-object-action) section in *Events Section in Widgets*.

{{% /报警 %}}

## 2 配置域名模型并创建页面

要列出客户名称并在列表中显示更详细的信息，您需要创建一个实体 *客户*， 添加属性 *名称* 和 *地址* 到它， 然后创建一个您将列出客户名称的页面。

要配置域模型并创建页面，请执行以下操作：

1. 打开您的 [域模型](domain-models)。

2. 创建实体 *客户*。 关于如何创建实体的更多信息，见第 [3节，在 *域模型概述* 中添加新实体](domain-models)。

3.  为 **客户** 实体创建属性 (关于如何创建属性的更多信息, 参见 [4 部分，添加新属性](domain-models) 在 *域模型概述*并做以下操作：<br/>

    a. 将属性的 **名称** 设置为 *名称*.<br/>

    b. 会议文件。 设置 [**类型**](domain-models-attributes) 为 **字符串**。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/name-attribute.png)<br/>    
   b. 会议文件。 点击 **创建** 以添加新属性。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/customer-entity.png)

4. Repeat step 3 to create an attribute *Address* of string type.

5.  现在您需要一个页面列出客户的名称。 创建空白页面并命名 *客户*。 关于创建页面的更多信息，见第 [3.2节在 *页面* 中创建一个新页面](page-editor)。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/create-page.png)

新建空白页面。

![](attachments/microflows-how-to-configure-delete-object/blank-page-created.png)

## 在列表视图中配置删除对象操作

现在您将配置列表视图，并将添加一个按钮，包含 [**删除对象** 动作](page-editor-widgets-events-section#delete-object-action) 当用户点击按钮时删除对应的客户。 执行以下操作：

1. 打开您创建的页面 *客户*。

2.  在 **构建块** > **列表** 找到 **列表 1**, 拖放到页面. 此建筑块默认包含列表视图。

    ![](attachments/microflows-how-to-configure-delete-object/list-1.png)

3.  现在您需要配置列表视图。 打开列表视图属性，执行以下操作： <br/>

    a.  选择 **数据库** 作为 **数据源**。<br/>

    b. 会议文件。  将 **实体** 设置为 **客户**。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/list-view-properties.png) <br/> 现在列表视图已连接到 **客户** 实体。 <br/>

4.  选择文本 *名称* 并在 **属性** 中执行以下任务：<br/>

    a. 在 **内容**, 删除文本 *名称*.<br/>

    b. 会议文件。 点击 **添加属性** (或按 <kbd>Ctrl</kbd> + <kbd>空格</kbd>) 并选择 **名称** 属性。 <br/>

    ![](attachments/microflows-how-to-configure-delete-object/text-content.png)<br/> 现在文本小部件已连接到 **name** 属性，并将在列表中向您显示客户名称。<br/>

5.  单击显示为箭头的按钮并删除它。

    ![](attachments/microflows-how-to-configure-delete-object/arrow-button.png)

6.  在 **工具箱** > **小部件** > **按钮** 找到 **删除对象**, 拖放到箭头按钮留下的容器内。

    ![](attachments/microflows-how-to-configure-delete-object/container-for-the-delete-button.png)

7.  在 **中， **删除** 按钮的属性** 您可以看到 **点击** 动作被自动设置为 **删除对象** 和标题设置为 **删除**，因为小部件是在Studio中预配置的。

    ![](attachments/microflows-how-to-configure-delete-object/delete-button-properties.png)

您已创建了列出客户名称的页面。 如果用户点击其中一行中的 **删除** 此行指明的客户将与客户的详细信息一起从应用程序中删除。 欲了解更多信息，请参见 [2.3 删除对象行动](page-editor-widgets-events-section#delete-object-action) *小部件事件部分*。

## 在数据视图中配置删除对象操作

您也可以在数据视图中配置 [**删除对象** 操作](page-editor-widgets-events-section#delete-object-action)。 在这种情况下 **删除对象** 将会删除所连接的对象。 要配置数据视图和您页面上的 **删除** 按钮，请做以下操作：

1.  在命名为 *客户*的页面， 打开 **布局网格** 属性 (使用屏幕底部的面包屑查找布局网格)。

    ![](attachments/microflows-how-to-configure-delete-object/breadcrumb.png)

2.  在 **属性** > **添加行**, 点击按钮，在下方添加一行，您需要将数据视图放置在那里。

    ![](attachments/microflows-how-to-configure-delete-object/add-row.png)

3. 在 **工具箱** > **小部件** > **数据容器**, 查找数据视图，将其拖放到列内(与新行一起添加)。

4.  现在您需要配置数据视图。 在 **数据视图中的属性** 中，执行以下操作： <br/>

    a. 将 **数据源** 设置为 **列表小部件**。<br/>

    b. 会议文件。 将 **小部件** 设置为 **实体客户列表**。 现在数据视图的数据源是放在同一页面上的列表视图。<br/>

    ![](attachments/microflows-how-to-configure-delete-object/data-view-list-widget.png)

5. 您需要用数据填写数据视图。 在 **工具箱** >**小部件** > **类型**, 选择 **文本**, 拖放到数据视图内容内。

6.  您将从刚刚添加的 **文本** 小部件中绘制一个标题。 Open the **Properties** of the **Text** and do the following:<br/>

    a. 在 **Content**, 删除单词 *Text* 并输入 *客户详细信息*。<br/>

    b. 会议文件。 将 **渲染模式** 设置为 **H4**. <br/>

    ![](attachments/microflows-how-to-configure-delete-object/text-heading4.png)<br/>

7. 现在您将添加一个文本框来显示所选客户的详细信息。 在 **小部件** > **输入元素**, 选择 **文本框**, 拖放在数据视图内容内。

8.  Open the **Properties** of the **Text Box**, and in **Data Source**, set **Attribute** to **Name** (the label for the text box will be changed to **Name** automatically).

    ![](attachments/microflows-how-to-configure-delete-object/text-box-name.png)

9. 重复第 7 步，再添加一个 **文本框** 到页面。

10. Open the **Properties** of the **Text Box**, and in **Data Source**, set **Attribute** to **Address** (the label for the text box will be changed to **Address** automatically).

    ![](attachments/microflows-how-to-configure-delete-object/text-box-address.png)

11. 在 **工具箱** > **小部件** > **按钮** 找到 **删除对象**, 在数据视图中拖放它。

12. 该按钮已经被预配置：它的 **单击操作** 已设置为 **删除对象**， 和 **标题** 已设置为 **删除**。 但你会给它添加一些样式。 执行以下操作：<br/>

    a. 在 **常规** 部分中，将 **样式** 设置为 **危险**.<br/>

    b. 会议文件。 在 **设计** 部分中，设置 **自对** 至 **右对齐**。<br/>

现在您已经配置了数据视图，一旦您在列表中选择此客户，将会向您显示客户的名称和地址。

![](attachments/microflows-how-to-configure-delete-object/configured-page.png)

数据视图中 **删除** 按钮的工作流(红色 **删除** 按钮)如下：

1. 用户在列表中选择客户的名称。

2. 客户的详细信息（名称和地址）见下面的数据视图。

3. 用户点击 **删除**。

4. 整个客户的记录已删除。

   ![](attachments/microflows-how-to-configure-delete-object/published-page-example.png)

欲了解更多信息，请参见 [2.3 删除对象行动](page-editor-widgets-events-section#delete-object-action) *小部件事件部分*。

恭喜！ 您在列表视图和数据视图中配置了 **删除** 个按钮。 
