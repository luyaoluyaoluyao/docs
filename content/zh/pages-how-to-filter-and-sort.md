---
title: "筛选和排序列表中的项目"
category: "页 次"
description: "描述如何在 Mendix Studio 中筛选和排序项目。"
menu_order: 50
tags:
  - "工作室"
  - "页面"
  - "邮件列表"
  - "如何处理"
  - "筛选器"
  - "排序"
---

## 1 导言

此操作可以解释您如何在列表视图或数据网格中筛选和排序Mendix Studio中的项目。

**这个教程将教你如何做以下事情：**

* 配置列表中项目的过滤器
* 在列表中排序项目

如何描述下面的用例：

您已经建立了一个包含检查报告列表的页面，这些报告显示了公司在遵守安全条例方面的检查。 您只想显示此检查失败的公司。 你还想只显示今天的报告。 此外，项目应从最新项目开始的日期和时间分列。

检查报告列表显示在一个页面上。 如果您在列表视图中，页面可以看到以下方式：

{{% image_container width="600" %}}
![](attachments/pages-how-to-filter-and-sort/list-view-example.png)
{{% /image_container %}}

或者如果您的列表在数据网格中，页面可以看到以下方式：

{{% image_container width="600" %}}
![](attachments/pages-how-to-filter-and-sort/page-example-data-grid.png)
{{% /image_container %}}

域模型在这个使用案例中的配置方式如下：

{{% image_container width="250" %}}
![](attachments/pages-how-to-filter-and-sort/domain-model.png)
{{% /image_container %}}

## 2 个前提条件

在启动此操作之前，请确保您已完成以下前提条件：

* 熟悉页面条款和如何在页面上执行基本功能。 欲了解更多信息，请参阅 [页面](/studio/page-editor)。
* 熟悉数据过滤器上的条款。 欲了解更多信息，请参阅 [Data Filters](/studio/data-filters)。
* 熟悉域模型条款并学习如何执行基本功能。 欲了解更多信息，请参阅 [域模型](/studio/domain-models)。

## 3 过滤信息

首先，您需要在列表中添加过滤器。  因为你只想显示那些检查失败的公司， **跳过** 属性(见上面的域模型图像)本应在检查报告中标记为 *否*

您还想要显示2020年2月创建或修改的报告。 这意味着 **DateAndTime** 属性应该从2020年2月1日至2020年2月29日。

要配置过滤器，请执行以下操作：

1. 选择列表视图或数据网格并打开其属性：

2. 在 **数据源** 部分中，点击 **过滤器**：

    {{% image_container width="250" %}}![](attachments/pages-how-to-filter-and-sort/properties-filter.png){{% /image_container %}}

3. 在 **添加滤镜** 对话框中，通过以下操作添加过滤器条件：

    1. 在下拉菜单中选择 **通过** 属性：

        {{% image_container width="550" %}}![](attachments/pages-how-to-filter-and-sort/add-filter-select-attribute.png){{% /image_container %}}

    2. 一旦您选择该条件的第一部分，您可以选择另一个部分来完成它。 选择 *false*:

        {{% image_container width="550" %}}![](attachments/pages-how-to-filter-and-sort/add-filter-condition.png){{% /image_container %}}

    3. 过滤当前日子的检查报告 您需要添加其他条件到过滤器：点击 **添加新条件** 并在下拉菜单中选择 **DateAndTime** 属性。

    4. 添加条件的第二部分：日期应为今天的日期。 在下拉菜单中选择 *今日*

        {{% image_container width="550" %}}![](attachments/pages-how-to-filter-and-sort/filter-date-and-time.png){{% /image_container %}}

    5. 点击 **添加**。

干得好！ 您已经创建了具有两个条件并读取以下方式的过滤器： *选择检查报告的记录，因为通过的记录是假的，日期和时间是今天。* 这意味着这个过滤器将只向您显示两个条件下的报告：那些检查失败的报告，以及那些在当前日子创建或修改的报告。

## 4 个排序项目

按日期和时间从最近一次开始排序列表中的项目，按下面的步骤：

1. 选择列表视图或数据网格并打开其属性。

2. 在 **排序顺序** 属性中，点击 **添加排序规则**。

3. 在 **添加排序规则** 对话框，选择 **DateAndTime** 属性并将 **订单** 设置为 *降序*。

    {{% image_container width="450" %}}![](attachments/pages-how-to-filter-and-sort/add-sorting-rule.png){{% /image_container %}}

4. 点击 **添加**。

恭喜！ 您已经向您的列表添加了一个过滤器和排序顺序。 您现在可以预览您的应用并测试您的页面。 关于如何预览您的页面的更多信息，请参阅 [预览 & 发布您的应用程序](/studio/publishing-app)。