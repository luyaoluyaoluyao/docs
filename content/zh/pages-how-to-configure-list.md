---
title: "配置列表和查看列表项详细信息"
category: "页 次"
description: "描述如何在 Mendix Studio 中配置一个项目列表。"
menu_order: 40
tags:
  - "工作室"
  - "页面"
  - "邮件列表"
  - "如何处理"
---

## 1 导言

这个操作可以解释如何配置项目列表并查看此列表中所选项目的详细信息。

**这个教程将教你如何做以下事情：**

* 创建一个新页面
* 配置列表视图
* 配置显示列表视图中选中项目详细信息的数据视图

如何描述下面的用例：

您公司的销售代表想查看机会联系人列表——潜在的客户。 当销售代表点击此列表中的一行时，相应机会联系人的详细信息将显示在列表旁边：

![](attachments/pages-how-to-configure-list/configured-page.png)

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio/page-editor)。

* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

* 请确保您的域模型配置如下：

    {{% image_container width="200" %}}![](attachments/pages-how-to-configure-list/domain-model.png){{% /image_container %}}

## 3 添加主详细页面

您想在主页上打开一个带有商机联系人列表及其详细信息的页面。 执行以下操作：

1. 打开您的主页并导航到 **工具箱** > **小部件**。

2. 搜索 **打开页面** 按钮，然后拖放到页面。

    {{% image_container width="250" %}}![Open Page](attachments/pages-how-to-configure-list/open-page-button.png){{% /image_container %}}

3. 打开按钮属性并按下面的步骤：

    1. 将 **页面** 设置为单击动作，并点击 **页面** 属性。

        {{% image_container width="250" %}}![Button Properties](attachments/pages-how-to-configure-list/button-properties.png){{% /image_container %}}

    2.  在 **选择页面** 对话框中，点击右上角的加号图标。

    3.  在 **创建新页面** 对话框，填写页面标题。

    4. 点击侧边栏中的 **主详细信息** 选择页面模板，并选择 **主详细信息**：

        {{% image_container width="550" %}}![](attachments/pages-how-to-configure-list/create-master-detail.png){{% /image_container %}}

    5. 点击 **创建**。


页面已创建。 在响应(桌面)视图中，列表显示在左边，列表项目细节显示在右边：

![](attachments/pages-how-to-configure-list/master-details.png)

## 4 配置列表

页面已创建，现在您需要进行配置。 首先，您需要将数据连接到列表。 执行以下操作：

1. 选择列表视图，然后点击属性中的 **实体** 选项：

    {{% image_container width="250" %}}![List View Properties](attachments/pages-how-to-configure-list/list-view-entity.png){{% /image_container %}}

2. 在 **选择实体** 对话框中，选择 **商机联系人** 并通过点击 **选择** 来确认您的选择。 现在该列表已连接到 **商业机会联系** 实体。

3. 要显示每家公司每份报告的名字，请做以下工作：

    1. 在列表视图中选择 **名称** 文本，并打开 **属性** 标签。

        {{% image_container width="300" %}}![](attachments/pages-how-to-configure-list/text.png){{% /image_container %}}

    2. 在 **内容** 属性中，删除 *名称* 并点击 **添加** > **属性**:

        ![](attachments/pages-how-to-configure-list/text-content.png)

    3. 在 **选择属性** 对话框中，选择 **名称** 然后点击 **选择**。

4. 从列表中删除图像以及此图像放置的列： 当前图像显示的用户图像与您正在显示的机会联系人不对应。
    {{% image_container width="300" %}}![](attachments/pages-how-to-configure-list/list-with-no-image.png){{% /image_container %}}

5. 由于新页面的目标仅仅是显示数据。 删除列表视图上面的 **新的** 按钮以及放置在其中的容器：

    {{% image_container width="300" %}}![](attachments/pages-how-to-configure-list/container.png){{% /image_container %}}

现在列表视图将按其名称显示机会联系人列表：

{{% image_container width="300" %}}![Configured List](attachments/pages-how-to-configure-list/list-configured.png){{% /image_container %}}

## 5 配置报告详细信息

现在您需要配置在列表旁边显示的商业机会详细联系方式。 当您从列表中选择名称时，所选联系人的详细信息将被显示。

您的页面基于的主详细信息页面模板有一个预配置的数据视图，它会监听列表视图。 这意味着数据视图显示列表视图中选择的机会联系人数据。

现在您需要在数据视图中配置部件以显示 *查看报告* 实体的属性。 或者用其他语句来显示商业机会联系人拥有的所有详细信息，如名称、工作标题、电话、电子邮件。

若要显示联系人拥有的所有详细信息，请做以下操作：

1. 删除空列并 **编辑**, **发送电子邮件**并且 **删除数据视图中的** 按钮，因为您只会显示数据，而不会更改它：

    ![](attachments/pages-how-to-configure-list/data-view-buttons.png)

2. 双击 *用户详细信息* 文本部件(显示为数据视图标题)，并将其重命名为 *机会详细信息*。

3. 打开 **工具箱** 并搜索 **单选按钮**, 拖拽它 *到* 上方的数据视图 **名称** 文本框。

    ![](attachments/pages-how-to-configure-list/radio-buttons.png)

4. 打开单选按钮属性，然后点击 **数据源** > **属性**。

5. 在 **选择属性** 对话框中，选择 **标题** 然后点击 **选择**

    {{% image_container width="400" %}}![](attachments/pages-how-to-configure-list/title.png){{% /image_container %}}

6. 选择 **name** 文本框，然后点击 **数据源** > **属性** 属性。

7. 在 **选择属性** 对话框中，选择 **名称** 然后点击 **选择**。

8. 重复步骤6和步骤7，为 **电话号码** 文本框设置 **电话** 属性， **电子邮件** 属性为 **电子邮件** 文本框， **生日的日期** **生日** 文本框， 和 **估值 **Bio** 文本框**

    ![](attachments/pages-how-to-configure-list/attributes-replaced.png)

9. 您缺少联系人的工作标题和状态信息。 要添加作业标题信息，请打开 **工具箱**，搜索 **文本框**拖放到数据视图中 **名称** 文本框下方：

    ![](attachments/pages-how-to-configure-list/job-title-text-box.png)

10. 打开文本框属性，然后点击 **数据源** > **属性**。

11. 在 **选择属性** 对话框中，选择 **JobTitle** 然后点击 **选择**。

12. 要添加机会联系人状态的信息，请打开 **Toolbox**， 搜索 **无线电按钮**, 拖放到数据视图中 **估算值** 文本框内。

13. 打开单选按钮属性，然后点击 **数据源** > **属性**。

14. 在 **选择属性** 对话框中，选择 **状态** 并点击 **选择**。

恭喜！ 您有一个页面显示机会联系人列表和所选联系人的详细信息：

![配置的页面](attachments/pages-how-to-configure-list/configured-page.png)

您现在可以预览您的应用并测试您的页面。 关于如何预览您的页面的更多信息，请参阅 [预览 & 发布您的应用程序](/studio/publishing-app)。

例如，您也可以在页面细节上工作 在列表中添加动态图像以显示机会联系人在他们的名字旁边的个人资料图片。 关于动态图像的更多信息，见 [图像 & 文件](/studio/page-editor-widgets-images-and-files)