---
title: "查找、找到优秀的用法"
parent: "编辑菜单"
description: "描述Mendix Studio Pro中的查找、查找和查找用法。"
menu_order: 10
tags:
  - "studio pro"
  - "找到高级版"
  - "查找用法"
  - "查找"
  - "编辑菜单"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/find-and-find-advanced.pdf)。
{{% /报警 %}}

## 1 导言

您可以在应用程序中搜索不同元素、文档、Xpath、对各种元素的更改或用法。  您通过 **查找**, **查找高级**, 以及 **查找用法** 在 **编辑** 菜单下的选项。

![查找选项](attachments/find-and-find-advanced/find-options.jpg)

## 2 查找选项

您可以通过 **找到** 个选项在您的应用程序中找到各种元素。 例如，您想要在域模型、页面编辑器中找到元素， 和微流程编辑器，使用了“员工”一词：页面、实体、协会、表达式等。 执行以下操作：

1. 点击 **编辑** > **在顶部栏中查找** <kbd>Ctrl</kbd>+<kbd>F</kbd>.

2. 在 **查找** 对话框中，退出 **匹配案件** 和 **匹配整个单词** 未选中。 这样您就可以搜索“员工”一词的所有实例，包括“员工”、“员工”或“Department_Employee”等实例：

3. 在 **中** 部分取消选择您不想搜索的项目:

   ![在部分中查看](attachments/find-and-find-advanced/look-in.jpg)

您可以在 **查找结果** 面板中看到搜索结果：

![搜索结果](attachments/find-and-find-advanced/search-results.jpg)

## 3 查找高级选项

使用 **查找高级** 选项您可以设置高级标准并在您的项目中找到特定元素。 例如所有 [对象活动](#find-object-activities)或 [未使用的元素](#find-unused-elements)。

### 3.1 寻找对象活动 {#find-object-activities}

您可以搜索具有对象活动的微流。 执行以下操作：

1.  点击 **编辑** > **查找** **高级** 在顶部栏中按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F</kbd>. **查找高级** 对话框将打开： ![](attachments/find-and-find-advanced/find-advanced-dialog-box.png)
3.  在 **搜索** 选项中，选择 **微流程操作**： ![](attachments/find-and-find-advanced/search-for-microflow-actions.png)
3.  选择您想要搜索对象活动的实体，然后点击 **找到**。

您可以在 **查找结果** 面板中看到搜索结果。

### 3.2 寻找未使用的元素 {#find-unused-elements}

当你开发你的应用时，它可能会出现这个特定的功能(例如，) 在应用程序的最后版本中，页面或microflow不再适用。 为了让您的应用保持清理和易于维护，建议您清理所有未使用的项目。

要查找未使用的物品，请执行以下操作：

1. Studio Pro的顶级酒吧， 点击 **编辑** > **查找高级** 或按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F</kbd>.

2. 在 **查找高级** 对话框中，选择 **未使用的项目** 在 **搜索** 选项中：

   ![](attachments/find-and-find-advanced/search-for-unused-items.png)

3. 点击 **找到**。

结果将显示在 **查找结果** 窗格中。 要过滤结果，请点击 **在窗格右上角显示所有** 按钮。

请注意，删除任何未使用的项目可能会导致更多未使用的项目。 例如，如果您删除一个未使用的页面，仅在该页面上使用的微流将成为一个未使用的项目本身。 如果您正在清理您的应用，请定期刷新未使用的项目列表。

{{% alert type="info" %}}

从市场下载的模块可能包含大量未使用的项目。 如果您删除这些项目并且模块稍后更新，这些项目将回到您的模型中。 所以建议您不要从市场模块中删除任何未使用的项目。

{{% /报警 %}}

{{% alert type="info" %}}

任何被排除在项目之外的对象都不会出现在未使用的项目列表中。

{{% /报警 %}}

### 3.3 标记未使用的对象

某些页面和微流仅从 Java 代码中使用，将被列为未使用的项目，因为Studio Pro 无法访问 Java 源代码。 为了防止任何人移除这些对象，您可以标记页面或微流程。 执行以下操作：

1. 打开需要标记为使用的页面或微流。

2. 导航到属性并将 **标记为已使用的** 属性从 **否** 更改为 **是**

   ![](attachments/find-and-find-advanced/mark-as-used-property.png)

## 4 查找用量选项

**查找使用** 选项允许您找到某个元素在哪里使用。 例如，要找到打开某个页面的所有按钮。

{{% alert type="info" %}}
此选项只能找到所选实体/属性被选中的位置。 这意味着它将找不到实体/属性被暗示推断的实例(例如通过跟踪一个协会)。
{{% /报警 %}}

为了找到某个元素的使用地点，请做以下操作：

1. 打开包含元素的文档。 例如，打开域模型。
2. 选择一个元素 (例如) 点击 **编辑** > **在顶部栏或右键点击元素中查找用法** 查找用法 **查找用法** ![查找用法](attachments/find-and-find-advanced/find-usages.png)

Studio Pro 在 **查找结果** 面板中显示此实体的所有用法。 ![查找结果面板](attachments/find-and-find-advanced/found-usages.png)

在 **查找结果** 窗格中双击一个项目来打开相应的文档。

点击 **在 **查找结果** 面板中锁定结果**。 现在，如果点击 **查找用法**，结果将会显示在第二 **查找结果** 窗格中。 这允许您保留几个搜索结果。

## 5 阅读更多

* [转到选项](go-to-option)
