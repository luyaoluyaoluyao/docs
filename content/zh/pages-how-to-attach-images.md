---
title: "启用最终用户附加图像"
category: "页 次"
description: "描述如何在 Mendix Studio 中配置图像上传器。"
menu_order: 60
tags:
  - "工作室"
  - "页面"
  - "图片"
  - "图片上传器"
  - "附件"
  - "附加图像"
---

## 1 导言

这个如何解释您如何能够让您的最终用户附加图像。 他们将能够从不同设备附加图像：电话、平板电脑或桌面；或者他们可以在手机摄像头拍摄新图像。

**这个教程将教你如何做以下事情：**

* 创建图像实体
* 创建一个带有表格的页面，允许您的最终用户附加图像
* 在列表中显示附加图像

如何描述下面的用例：

您有 **新报告** 页面带有表单(数据视图)，员工可以提交旅行报销报告。 他们填写他们的姓名、部门、目的和旅行日期，并报销总额：

{{% image_container width="600" %}}![](attachments/pages-how-to-upload-images/form-example.png){{% /image_container %}}

您的域模型看起来如下方式：

{{% image_container width="200" %}}
![](attachments/pages-how-to-upload-images/domain-model.png)
{{% /image_container %}}

您想要添加一个新功能：创建偿还报告时 员工需要附加收据——屏幕截图或他们支付的费用的扫描图像。

您还想要在报表下方的列表中显示附加图像，并使您的最终用户能够在需要时从列表中删除图像。

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio/page-editor)。
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

## 3 正在创建图像实体

首先，， 要能够附加和上传图像，您需要将特殊类型的实体添加到您的域模型：图像实体。 执行以下操作：

1. 打开您的域模型并打开 **工具箱** 标签。

2. 选择 **图像实体** 并拖放到您的域模型。

3. In the **Create New Image Entity** dialog box, set **Name** to *Receipt* and click **Create**.

    {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/create-new-image-entity.png){{% /image_container %}}

4. 现在您需要从 **镜像** 实体创建到 **报表** 实体。 做以下一件：

    1. 悬停在 **图像** 实体上，点击点图标，将点拖动到 **举报** 实体：

        {{% image_container width="500" %}}![](attachments/pages-how-to-upload-images/association-method1.png){{% /image_container %}}

    2. 选择 **图像** 实体，单击箭头图标，选择 **举报** 作为关联的第二个实体：

        {{% image_container width="250" %}}![](attachments/pages-how-to-upload-images/association-method2.png){{% /image_container %}}

干得好！ 您已经创建了图像实体和一个从它到 **报告** 实体的关联：

{{% image_container width="600" %}}![](attachments/pages-how-to-upload-images/domain-model-configured.png){{% /image_container %}}

## 4 个图片上传器

**图像上传器** 是一个允许您最终用户附加图像的部件。 然而，仍然存在着这种情况。 它只能在数据容器中起作用(列表视图或数据视图)，并且只能有一个图像实体作为其数据源。 如果您只需拖放图像上传到您的报告表格，它将无法正常运转， 因为您当前的数据视图有 **报告** 实体作为其数据源，它不是一个图像实体：

{{% image_container width="600" %}}![](attachments/pages-how-to-upload-images/form-example.png){{% /image_container %}}

为了解决这个问题，您可以添加一个按钮来打开一个弹出页面，您的最终用户可以附加图像。 此页面将通过 *Image_Report* 关联连接到您当前的报告表单，并将将图像上传为 **Image** 实体并与此特定报告相关联。

遵循下面的步骤：

1. 打开雇员提交新报告的 **新报告** 页面。

2. 打开 **工具箱** 并搜索 **创建对象** 按钮。

3. 拖放按钮到 **上方保存** and **取消** 按钮：

    {{% image_container width="450" %}}![](attachments/pages-how-to-upload-images/new-button.png){{% /image_container %}}

4. 打开按钮属性 > **标题** 属性，并将它从 *新* 重命名为 *附加图像*。

5. 点击 **图标** 属性。

6. 在 **选择图标** 对话框中，搜索 *图片* 图标并选择它。

7. 在按钮属性中，单击 **风格** 属性，然后将其从 **默认** 更改为 **成功**。 在您的更改后，按钮将显示如下方式：

    {{% image_container width="150" %}}![](attachments/pages-how-to-upload-images/button-style-change.png){{% /image_container %}}

8. 在按钮属性中，点击 **实体** 属性。

9. 在 **选择实体** 对话框中，选择 **收据** 实体从 **接收报告** 关联并点击 **选择**：

    {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/image-report-association.png){{% /image_container %}}

10. 在按钮属性中，点击 **页面**。

11. 在 **选择页面** 对话框中，点击右上角的加号图标。

12. 在 **创建新页面** 对话框中，执行以下操作：

     1. 将 **标题** 设置为 *附加图像*。

     2. 将 **布局** 设置为 *弹出布局*。

     3. 基于 receipt 实体</strong> 选项的 **预填充页面内容已开启，所以页面模板 (表单) 是为您自动选择的。 选择 **垂直表单** 并点击 **创建**。</p>

         {{% image_container width="500" %}}![](attachments/pages-how-to-upload-images/create-new-page-images.png){{% /image_container %}}</li> </ol></li>

13

创建一个带有预配置表单的弹出页面(数据视图)：

     {{% image_container width="500" %}}![](attachments/pages-how-to-upload-images/attach-images-page.png){{% /image_container %}}

     由于您只需要您的最终用户在这个页面上附加图像，请删除 **动态图像** 小部件， **数据视图中的名称** 和 **大小** 文本框。

14

打开 **工具箱**，搜索 **图像上传器**，拖放到数据视图中。 </ol>

您已经创建了弹出页面，这将允许员工将图像附加到他们的报销报告：

{{% image_container width="450" %}}![](attachments/pages-how-to-upload-images/attach-images-pop-up-page.png){{% /image_container %}}


## 5 显示附加图像

用户附加图像后， 最好能够显示他们的附加物，并给他们一个机会来删除他们不需要的附加物。 要做到这一点，您需要添加一个带动态图像的列表：

1. 打开 **新报告** 页面。

2. 在 **建筑块**， 搜索 **列表中包含图像** 并在 **附加图像** 按钮下拖放它*内* 数据视图)。 包含小部件的列表视图被添加到您的页面：

    ![](attachments/pages-how-to-upload-images/list-4.png)

3. 打开列表视图属性，执行以下操作：

    1. 点击 **实体** 属性。
    2. 在 **选择实体** 对话框中，选择 **选择实体** 对话框， 选择 **收据** 实体通过 **收据报告** 关联并点击 **选择**：

        {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/image-report-association.png){{% /image_container %}}

4. 点击列表视图中的图像，打开其属性，并执行以下操作。

    1. 若要显示用户附加的图像，请将 **图像源** 从 **静态图像** 更改为 **动态图像**。
    2. 点击 **图像实体** 属性。
    3. 在 **选择图像实体**中，选择 **收据** 然后点击 **选择**。
    4. 在 **默认图像** 属性中，点击 **选择图像**， 在 **选择图片** 对话框中，点击 **清除**

        {{% image_container width="300" %}}![](attachments/pages-how-to-upload-images/image-properties.png){{% /image_container %}}

5. 删除列表视图中的字幕，表示 *次要文本*。

6. 在列表视图中选择 **列表项标题** 文本并打开其属性。

    1. 在 **内容** 属性中，删除 *列表项标题* 文本并点击 **添加**  > **属性**。
    2. 在 **选择属性** 对话框中 选择 **名称** 属性并点击 **选择** 以显示附加图像的名称。

        {{% image_container width="400" %}}![](attachments/pages-how-to-upload-images/select-attribute.png){{% /image_container %}}

7. 选择列表视图中的按钮，打开其属性，并执行以下操作：

    1. 在 **事件** 部分 > 中， **点击动作** 属性，选择 **更多**。

    2. 在 **动作** 属性中，选择 **删除对象**。

    3. 在 **常规** 章节 > 中， **标题** 属性，设置按钮标题为 *删除*。

    4. 点击图标属性，然后点击 **清除 **选择图标** 对话框中的** 来删除图标。

    5. 更改 **渲染模式** 从 **链接** 到 **按钮**

    6. 在 **风格** 属性中，将 **默认** 更改为 **危险**。

      ![](attachments/pages-how-to-upload-images/button-properties.png)

干得好！ 现在您有了显示附加图像的图像列表，如果需要，您的用户将能够从列表中删除图像：

![](attachments/pages-how-to-upload-images/configured-image-list.png)

恭喜！ 您已经配置了允许用户附加图像并在列表中显示这些图像的报告。

[预览您的应用程序](/studio/publishing-app) 来测试图像上传的工作方式。 您也可以配置一个按钮来附加文件而不是图像。 关于文件的更多信息，请参阅 [图像 & 文件](/studio/page-editor-widgets-images-and-files)