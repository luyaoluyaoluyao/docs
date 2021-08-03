---
title: "枚举数"
parent: "域名模型"
description: "描述Mendix Studio中的枚举."
tags:
  - "工作室"
  - "域模型"
  - "属性"
  - "枚举数"
---

## 1 导言

本文档描述Mendix Studio中的枚举。 枚举是一个或多个项目的列表(值)。 每个项目代表一个选项。 例如，客户可以被分配给 *青铜*, *银质*, 和 *黄金* 等级。 因此， *客户等级* 是一个列举。 *青铜*, *银币*, 和 *金币* 是列举项。  欲了解更多项目信息，请参阅 [枚举项](#enumeration-items) 部分。

当您创建 *枚举* 属性时，您要么给它分配一个现有的枚举，要么创建一个新的枚举。 关于枚举类型属性属性的详细信息，请参阅 *属性中的 [属性](domain-models-attributes#attribute-properties) 部分*。

## 2 枚举项 {#enumeration-items}

枚举由枚举项或数值组成。 每个项目代表一个选项。

枚举还可以代表 *未初始化状态*。 例如，如果您不将任何成绩分配给客户，成绩状态是 *空的*。

## 3 基本操作

当您将枚举类型的属性添加到您的域模型时，枚举是配置的。 您可以 [创建一个新的](#create-new-enumeration) 或 [选择一个现有的枚举](#select-existing-enumeration)。

### 3.1 创建一个新的枚举值 {#create-new-enumeration}

若要创建一个新的计数，请执行以下操作：

1. 打开您的 [域模型](domain-models)。

2. 选择一个您想要创建属性的实体。 欲了解如何创建实体的更多信息，请参阅 *域模型概述* 中的 [添加新实体](domain-models#adding-new-entities) 部分。

3.  若要创建枚举类型的新属性，请点击 **新属性** 并执行以下内容：<br /> a。 设置属性 **名称**。 在我们的示例中，属性的名称是 *级*。<br /> b. 将[类型](domain-models-attributes)设置为**枚举**。<br /> c. 点击**选择枚举**。<br />d。 在 **选择枚举** 对话框中，点击右上角的加号图标。<br/> e。 在 **中创建新枚举** 对话框， 点击 **添加项目** 以添加可能的枚举选项(**名称** 自动填写并与属性名称相同)。<br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item.png)<br />

    g. 平均输出功率超过1瓦； 填写**标题** (**名称** 自动填写)。 在下面的示例中，您需要填充  *青铜*， 作为列举的三个可能项目之一：青铜、银和金矿。 <br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item-bronze.png)<br />

    g. 点击 **添加** 并重复上面的步骤来创建其他枚举项目。<br /> h. 点击**创建**来关闭对话框并创建新属性。

    ![](attachments/domain-models-enumeration/new-enumeration-bronze-silver-gold.png)

已创建属性和枚举项。

### 3.2 选择枚举数 {#select-existing-enumeration}

您也可以为枚举类型的属性设置一个现有枚举. 执行以下操作：

1. 打开您的 [域模型](domain-models)。

2. 选择一个您想要创建属性的实体。 关于如何创建实体的更多信息，见第 [3节，在 *域模型概述* 中添加新实体](domain-models#adding-new-entities)。

3.  要创建枚举类型的新属性，请点击 **新属性** 并执行以下操作：<br />

    a. 设置属性 **名称**。 在我们的示例中，属性的名称是 *级*。<br /> b. 将[类型](domain-models-attributes)设置为**枚举**。<br /> c. 点击**选择枚举**。<br />

    ![](attachments/domain-models-enumeration/new-attribute-select-enumeration.png) <br/>

    b. 平均输出功率超过1瓦； 在 **选择枚举** 对话框中，现有的枚举显示在列表中。 点击您想要使用的单击，然后点击 **选择**。<br />

    ![](attachments/domain-models-enumeration/selecting-existing-enumeration.png)

现有枚举是为枚举类型的属性选定的。

### 3.3 复制并粘贴枚举数

您可以复制并粘贴枚举到另一工作室应用程序。 遵循下面的步骤：

1. 打开您的 [域模型](domain-models)。

2. 选择枚举类型的属性，然后点击属性中的 **枚举**。

3. 在 **选择枚举** 对话框中，选择要复制的枚举，然后单击椭圆图标。

4. 在下拉菜单中选择 **复制到剪贴板** 选项。 ![复制 Enumeration](attachments/domain-models-enumeration/copy-to-clipboard.png)

5. 打开不同的模块或 Studio 应用程序，导航到域型号并按 <kbd>Ctrl</kbd> + <kbd>V</kbd>。

枚举被粘贴。 欲了解工作室中复制/粘贴函数的更多信息，请在 *常规信息* 中查看 [复制/粘贴页面、微流和枚举](general#copy-paste-documents) 部分。

### 3.4 复制枚举

若要重复列举，请按下面步骤：

1. 打开您的 [域模型](domain-models)。

2. 选择枚举类型的属性，然后点击属性中的 **枚举**。

3. 在 **选择枚举** 对话框中，选择你想要重复的枚举并点击椭圆图标。

4.  在下拉菜单中选择 **重复的** 选项。

    ![重复枚举](attachments/domain-models-enumeration/duplicate.png)

5. 关闭对话框。

此列举重复进行。

#### 3.5 删除枚举中

若要删除枚举，请按下面步骤：

1. 打开您的 [域模型](domain-models)。

2. 选择枚举类型的属性，然后点击属性中的 **枚举**。

3. 在 **选择枚举** 对话框中，选择要删除的枚举，然后单击椭圆图标。

4. 在下拉菜单中选择 **删除** 选项：

    ![删除枚举数](attachments/domain-models-enumeration/delete-enumeration.png)

5. 确认您的选择并关闭对话框。

枚举已删除。

## 4 阅读更多

* [域模型](域名模型)
* [属性](domain-models-attributes) 
