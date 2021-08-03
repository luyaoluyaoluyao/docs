---
title: "配置文件上传和下载"
category: "页 次"
description: "描述如何在 Mendix Studio 中配置文件管理器。"
menu_order: 70
tags:
  - "工作室"
  - "页面"
  - "文件"
  - "上传文件"
  - "附件"
  - "文件管理器"
---

## 1 导言

这将解释您如何能够让您的最终用户附加和下载文件，例如PDF文件或Microsoft Word 文档。 他们将能够从不同的设备上附加文件：电话、平板电脑或桌面，以及从列表中下载附加文件。

**这个教程将教你如何做以下事情：**

* 创建文件实体
* 创建一个表格，允许您的最终用户上传文件
* 在列表中显示附加文件
* 允许您的最终用户下载文件

如何描述下面的用例：

您的公司有一个应用，公司的IT部门将跟踪分配给雇员的资产。 您有 **员工简介** 页面有一个表单(数据视图)，它有雇员姓名等详细信息。 部门、他们的电子邮件、电话、标题和分配给他们的资产（例如手机或膝上型电脑）。 这些信息由信息技术管理员填写和更新：

{{% image_container width="600" %}}
![员工个人资料页面](attachments/pages-how-to-attach-files/employee-profile-form.png)
{{% /image_container %}}

域模型看起来如下方式：

{{% image_container width="200" %}}![Domain Model](attachments/pages-how-to-attach-files/domain-model.png){{% /image_container %}}

您想要添加一个新功能：IT管理员应该能够将文件附加到员工配置文件， 例如，附加雇员签署的电话或膝上型计算机政策。

您还想要启用 IT 管理员从文件列表下载所附文件。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio8/page-editor)。
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio8/domain-models)。

## 3 正在创建文件实体

首先，， 要能够附加和/或下载文件，您需要将特殊类型的实体添加到您的域模型： [文件实体](/studio8/domain-models#entity-types)。 执行以下操作：

1. 打开您的域模型并打开 **工具箱** 标签。

2. 选择 **文件实体** 并拖放到您的域模型。

3. In the **Create New File Entity** dialog box, set **Name** to *Document* and click **Create**.

    {{% image_container width="450" %}}![Create File Entity](attachments/pages-how-to-attach-files/create-file-entity.png){{% /image_container %}}

4. 现在您需要从 **文件** 实体创建一个关联到 **员工** 实体。 做以下一件：

    1. 悬停在 **文件** 实体上，点击点图标，将点拖动到 **员工** 实体：

        {{% image_container width="500" %}}![Create Association](attachments/pages-how-to-attach-files/create-association-method-one.png){{% /image_container %}}

    2. 选择 **文件** 实体，点击箭头图标，选择 **员工** 作为关联的第二个实体：

        {{% image_container width="250" %}}![Create Association](attachments/pages-how-to-attach-files/create-association-method-two.png){{% /image_container %}}

干得好！ 您已经创建了文件实体和一个从它到 **员工** 实体的关联：

{{% image_container width="600" %}}![Domain Model Configured](attachments/pages-how-to-attach-files/domain-model-configured.png){{% /image_container %}}

## 4 添加文件管理器

**文件管理器** 是一个允许您最终用户附加和/或下载文件的小部件。 然而，它只能在数据容器内起作用(列表视图或数据视图)， 和列表视图或数据视图只能有一个文件实体作为其数据源。 如果你只是拖放文件管理器到你的员工个人资料表，它将无法正常工作。 因为您当前的数据视图有 **员工** 实体作为其数据源， 您需要数据源作为一个文件实体，在这种情况下就是 **文档** 实体：

{{% image_container width="600" %}}![Employee Profile Page](attachments/pages-how-to-attach-files/employee-profile-form.png){{% /image_container %}}

为了解决这个问题，您可以添加一个按钮来打开一个弹出页面，您的最终用户 (IT 管理员) 可以上传图像。 此页面将通过 *Document_Employee* 关联连接到您当前的报告表格，并将上传与此特定报告相关的文件。

遵循下面的步骤：

1. 打开 **员工配置文件** 页面，其中IT管理员创建并编辑有关分配给他们的员工和资产的信息。

2. 打开 **工具箱** 并搜索 **创建对象** 按钮。

3. 拖放按钮到 **上方保存** and **取消** 按钮：

    {{% image_container width="450" %}}![Create Object Button](attachments/pages-how-to-attach-files/create-object-button.png){{% /image_container %}}

4. 打开按钮属性并执行以下操作：

    1. 选择 **标题** 属性并将其重命名为 *New* 到 *附加文件*.

    2. 点击 **图标** 属性。

    3. 在 **选择图标** 对话框中，搜索 *文件* 图标，然后点击 **选择**。

    4. 点击 **风格** 属性并将其从 **默认** 改为 **成功**。 在您的更改后，按钮将显示如下方式：

        {{% image_container width="150" %}}![Attach Files](attachments/pages-how-to-attach-files/attach-file-button.png){{% /image_container %}}

    5. 点击 **实体** 属性。

    6. 在 **选择实体** 对话框中 选择 **文档** 实体超过 **Document_Employee** 关联 (*Document_Employee/Document*) 然后点击 **选择**

        {{% image_container width="400" %}}![Select File Entity](attachments/pages-how-to-attach-files/select-file-entity.png){{% /image_container %}}

    7. 点击 **页面** 属性。

    8. 在 **选择打开页面** 对话框中，点击 **新页面**

    9. 在 **创建新页面** 对话框中，执行以下操作：

         1. 将 **标题** 设置为 *附加文件*.

         2. 将 **布局** 设置为 *弹出布局*。

         3. 基于文档实体</strong> 选项的 **预填充页面内容已开启，所以页面模板 (表格) 是为您自动选择的。 选择 **垂直表单** 并点击 **创建**。</p>

             {{% image_container width="500" %}}![](attachments/pages-how-to-attach-files/create-attach-file-page.png){{% /image_container %}}

        4. 创建一个带有预配置表单的弹出页面(数据视图)：

             {{% image_container width="500" %}}![Attach Files Page](attachments/pages-how-to-attach-files/attach-file-page.png){{% /image_container %}}

        5. 因为您只需要您的最终用户在这个页面上附加文件， 从数据视图中删除 **名称** 和 **大小** 文本框。

        6. 打开 **工具箱**，搜索 **文件上传器**，拖放到数据视图中。 </li> </ol></li> </ol></li> </ol>

您已经创建了弹出页面，允许IT管理员将文件附加到员工配置表：

{{% image_container width="450" %}}![Attach Files Page Configured](attachments/pages-how-to-attach-files/attach-file-page-configured.png){{% /image_container %}}


## 5 个正在下载文件

在您的最终用户附加文件后， 最好在列表中显示文件并在需要时让用户有机会下载附加文件。 要做到这一点，您需要添加一个列表：

1. 打开 **Employeee_Profile** 页面。

2. In the **Building Blocks**, search for **List 4** and drag and drop it under the **Attach File** button (make sure you drop it *inside* the data view, this way you will be able to list only files associated with a selected employee instead of all files that were attached to any employee profile). 包含小部件的列表视图被添加到您的页面：

    {{% image_container width="550" %}}![List 4](attachments/pages-how-to-attach-files/list-4.png){{% /image_container %}}

3. 选择列表视图，打开其属性，并执行以下操作：

    1. 点击 **实体** 属性。

    2. 在 **选择实体** 对话框中 选择 **文档** 实体超过 **Document_Employee** 关联 (*Document_Employee/Document*) 然后点击 **选择**

        ![选择实体](attachments/pages-how-to-attach-files/select-file-entity.png)

4. 删除图像和从列表中放置的一列：

    ![从列表中删除列](attachments/pages-how-to-attach-files/column-list.png)

5. 删除列表中的字幕，表示 *您可以放置字幕*。

6. 在列表视图中选择 **命名** 文本，打开它的属性，并执行以下操作：

    1. 在 **内容** 属性中，删除 *名称* 文本，然后点击 **添加属性**。
    2. 在 **选择属性** 对话框中 选择 **名称** 属性并点击 **选择** 以显示所附文件的名称。

        {{% image_container width="400" %}}![Select Attribute](attachments/pages-how-to-attach-files/select-attribute.png){{% /image_container %}}

7. 删除列表视图中的 **详细信息** 按钮。

8. 打开 **Toolbox** 并搜索 **文件下载器**, 拖放到放置 **详细信息** 按钮的位置。

9. 打开 **文件下载器** (**文件管理器**) 属性 > **标签** 属性并删除 *文件* 文本。

干得好！ 现在您有显示附加文件的列表，并且您的用户可以从这个列表下载文件：

{{% image_container width="500" %}}![Configured List View](attachments/pages-how-to-attach-files/list-view-configured.png){{% /image_container %}}

恭喜！ 您已配置了允许IT管理员附加文件并在列表中显示这些文件的表单。

[预览您的应用程序](/studio8/publishing-app) 来测试文件上传和下载如何运行：

![预览列表](attachments/pages-how-to-attach-files/list-previewed.png)

您也可以配置一个按钮来附加图像而不是文件。 欲了解更多信息，请参阅 [如何启用最终用户附加图像](pages-how-to-attach-images)。