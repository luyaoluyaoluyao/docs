---
title: "配置表单并显示与此相关的项目"
category: "页 次"
description: "描述如何在 Mendix Studio 中配置一个项目列表。"
menu_order: 10
tags:
  - "工作室"
  - "页面"
  - "邮件列表"
  - "如何处理"
---

## 1 导言

如何解释如何配置带有表单的页面，以及如何在同一页面显示与此表单相关的项目。 例如，显示与本报告有关的报告和核对表。

**这个教程将教你如何做以下事情：**

* 配置表单(数据视图)
* 在表中显示与此表单相关的项目

如何描述下面的用例：

贵公司HSE部门有以下检查报告：

![](attachments/pages-how-to-configure-form/report-example.png)

贵公司有一份申请书，供前往不同公司的检查员使用，并检查这些公司是否遵守安全条例。 他们填写他们的姓名、公司名称、地点地点、日期和进行检查的时间。 以及视察期间在场的督察的全名。

检查专员还有一份安全检查 *清单*。 检查员根据这份核对表评估公司是否通过了检查。 他们应该检查以下 *个问题* 是否符合要求：

* 如果显示紧急联系人海报
* 如果定期举行安全培训
* 如果可以获得急救包
* 如果存在紧急状态，则不会被阻止

如果上述任何一项要求没有得到满足，在下一次视察中，视察员将说明确定违反安全规定的日期。

您的应用已经包含了所有检查报告列表：

{{% image_container width="600" %}}![](attachments/pages-how-to-configure-form/inspection-report-list.png){{% /image_container %}}

您希望这个列表中的 **详细信息** 按钮打开一个显示所选报告详细信息的页面和一个包含与这个报告相关的清单问题的表格。 您还想要能够在表格中添加新的核对表或编辑现有的核对表。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio/page-editor)。

* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

* 请确保您的域模型配置如下：

    {{% image_container width="200" %}}![Domain Model](attachments/pages-how-to-configure-form/domain-model.png){{% /image_container %}}

    * 请确保您已将 **问题** 属性设置为以下枚举：

        {{% image_container width="550" %}}![](attachments/pages-how-to-configure-form/enumeration.png){{% /image_container %}}

* 请确保您的应用包含一个包含检查报告列表和 **详细信息** 按钮的页面：

    {{% image_container width="600" %}}![](attachments/pages-how-to-configure-form/inspection-report-list.png){{% /image_container %}}

## 3 添加带有表单的页面

检查报告列表中的 **详细信息** 按钮应该打开一个包含检查报告详细信息的页面。 要配置该页面，请执行以下操作：

1. 点击 **详细信息** 按钮并转到它的属性。

2. 将 **页面** 设置为单击动作，并点击 **页面** 属性。

    {{% image_container width="250" %}}![Button Properties](attachments/pages-how-to-configure-form/button-properties.png){{% /image_container %}}

3.  在 **选择页面** 对话框中，点击右上角的加号图标。

1.  在 **创建新页面** 对话框中，将 **标题** 设置为 **报告详细信息**并将 **布局** 设置为 **Atlas_default**。

2.  基于 Inspection 报表实体</strong> 选项的 **预填充页面内容已开启，所以页面模板 (表格) 是为您自动选择的。 选择 **垂直形式**:</p>

    {{% image_container width="550" %}}![Create New Page](attachments/pages-how-to-configure-form/create-new-page.png){{% /image_container %}}</li>

3

点击 **创建**。

7

创建了带有表单(数据视图)的页面。 打开数据视图属性并确保数据源自动设置为 **Context** and **Entity** 设置为 **InspecttionReport**

      {{% image_container width="250" %}}![](attachments/pages-how-to-configure-form/data-view-source.png){{% /image_container %}} </ol>


页面上的表单已配置：
{{% image_container width="600" %}}![](attachments/pages-how-to-configure-form/data-view-configured.png){{% /image_container %}}

## 显示清单问题

检查员有一个 *问题* 的列表，并用 **是** 或 **否** 说明公司是否符合要求：公司是否有具有紧急联系人的海报。 它是否定期进行安全培训等。 你想在检查报告下方显示一份清单问题表及其结果：

{{% image_container width="550" %}}

![](attachments/pages-how-to-configure-form/inspection-report-example.png)

{{% /image_container %}}

要在表中显示清单详情，您可以添加数据网格。 重要的是你把它 *放在数据视图* 中：这样数据网格就可以访问和只显示与当前报告相关联的清单项目，而不是显示所有添加到所有报告的清单项目。 这意味着您的数据网格将从一个关联获取数据，在这种情况下称为 *复查列表检查报告*。

遵循下面的步骤：

1. 打开 **工具箱** > **数据容器**。

2. 拖放 **数据网格** *在* 数据视图中：

    {{% image_container width="550" %}}![](attachments/pages-how-to-configure-form/data-grid-inside-data-view.png){{% /image_container %}}

3. 转到数据网格属性，然后点击 **实体**。

4. To show only checklist items associated with the current inspection report, choose the **Checklist** entity over association (*Checklist_InspectionReport/Checklist*) in the **Select Entity** dialog box and click **Select**:

    ![](attachments/pages-how-to-configure-form/data-grid-over-association.png)

5. 由于页面的主要目的是显示信息，您不需要数据网格中的 **搜索** 部分。 打开数据网格属性 > **搜索** 部分并禁用 **启用搜索** 切换：

    ![数据网格搜索](attachments/pages-how-to-configure-form/data-grid-search.png)

6. 为了能够在报告中添加新的清单项目，请在数据网格中选择 **新的** 按钮并打开它的属性。

7. 将 **单击动作** 设置为 **页面**。

8. 启用 **创建对象** 属性。 **实体** 属性自动设置为 **清单**：

    {{% image_container width="250" %}}![](attachments/pages-how-to-configure-form/new-button-properties.png){{% /image_container %}}

9. 点击 **页面** 属性。

10. 在 **选择页面** 对话框中，点击右上角的加号图标。

11. 在 **创建新页面** 对话框， 将 **标题** 设置为 **校验列表_详细信息** 和 **布局** 设置为 **弹出布局**。

12. 基于清单实体</strong> 选项的 **预填充页面内容已开启 这样页面模板(*Forms*) 会自动为您选择。 选择 **垂直形式**: </p>

    {{% image_container width="550" %}}![](attachments/pages-how-to-configure-form/manage-checklist.png){{% /image_container %}}</li>

13

点击 **创建**。

14

一个弹出窗口，最终用户可以添加新的核对表项目。 现在您可以选择一个页面作为 **编辑** 按钮的单击动作来编辑选定的检查列表。 点击 **编辑数据网格中的** 按钮并打开其属性。

15

将 **单击动作** 设置为 **页面**。

16

将 **页面** 属性设置为 **Management_Checklist**。

      {{% image_container width="250" %}}![](attachments/pages-how-to-configure-form/edit-button-properties.png){{% /image_container %}}</ol>

现在清单项目在表格中显示。 您可以通过点击表中的 **新的** 按钮来添加新的核对表。 点击 **编辑** 按钮来编辑选中的清单。

{{% image_container width="80%" %}}

![](attachments/pages-how-to-configure-form/data-grid-configured.png)

{{% /image_container %}}

恭喜！ 您有一个页面显示所选报告的详细信息和本报告的清单项目：

{{% image_container width="80%" %}}

![配置的页面](attachments/pages-how-to-configure-form/configured-page.png)

{{% /image_container %}}

您现在可以预览您的应用并测试您的页面。 关于如何预览您的页面的更多信息，请参阅 [预览 & 发布您的应用程序](/studio/publishing-app)。

例如，您也可以在页面细节上工作 将动态图像添加到检查报告列表中，以便在其名称旁边显示一个独特的公司标识。 关于动态图像的更多信息，见 [图像 & 文件](/studio/page-editor-widgets-images-and-files)

您也可以添加新的功能。 例如，你可以让视察员将图像附加到他们的报告。 欲了解更多信息，请参阅 [如何启用最终用户附加图像](pages-how-to-attach-images)。