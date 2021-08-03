---
title: "枚举数"
category: "域模型"
description: "描述Mendix Studio中枚举类型的属性。"
tags:
  - "工作室"
  - "域模型"
  - "属性"
  - "属性类型"
  - "枚举数"
---

## 1 导言

本文档描述Mendix Studio中的枚举属性类型。 枚举是具有预定义选项列表的属性类型。 枚举有一个或多个项目 (值)。 每个项目代表一个选项。 例如，客户等级可以是青铜、银和金级。 因此，客户级别的枚举将由三个项目组成： *青铜*, *Silver*, *Gold*。  欲了解更多信息，请参阅 [枚举项](#enumeration-items)。

## 2 枚举项 {#enumeration-items}

枚举由枚举项或数值组成。 每个项目代表一个选项。

枚举类型的属性也可以代表未初始化状态。 例如，如果您不将任何成绩分配给客户，成绩状态是 *空的*。

## 3 基本操作

当您将枚举类型的属性添加到您的域模型时，枚举是配置的。 您可以 [创建一个新的](#create-new-enumeration) 或 [选择一个现有的枚举](#select-existing-enumeration)。

### 3.1 创建一个新的枚举值 {#create-new-enumeration}

若要创建一个新的计数，请执行以下操作：

1. 打开您的 [域模型](domain-models)。

2. 选择一个您想要创建属性的实体。 关于如何创建实体的更多信息，见第 [3节，在 *域模型概述* 中添加新实体](domain-models#adding-new-entities)。

3.  若要创建枚举类型的新属性，请点击 **新属性** 并执行以下内容：<br /> a。 设置属性 **名称**。 在我们的示例中，属性的名称是 *级*。<br /> b. 设置[**类型**](domain-models-attributes)为**枚举**。<br /> c. 点击**选择枚举**以创建一个新的枚举。<br />d。 在 **选择枚举** 对话框窗口中，点击 **新**。<br/> e。 在 **创建新枚举** 对话框窗口， 点击 **添加项目** 以添加可能的枚举选项(**名称** 自动填写并与属性名称相同)。<br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item.png)<br />

    g. 平均输出功率超过1瓦； 填写**标题** (**名称** 自动填写)。 在我们的示例中，我们首先填写  *Bronze*, 作为枚举的三个可能的项目之一：Bronze, Silver和Gold。 <br />

    ![](attachments/domain-models-enumeration/new-enumeration-add-item-bronze.png)<br />

    g. 点击 **添加** 并重复上面的步骤来创建其他枚举项目。<br /> h. 点击**创建**来关闭对话框窗口并创建新属性。

    ![](attachments/domain-models-enumeration/new-enumeration-bronze-silver-gold.png)

已创建属性和枚举项。

### 3.2 选择一个现有的枚举数 {#select-existing-enumeration}

您也可以为枚举类型的属性设置一个现有枚举. 执行以下操作：

1. 打开您的 [域模型](domain-models)。

2. 选择一个您想要创建属性的实体。 关于如何创建实体的更多信息，见第 [3节，在 *域模型概述* 中添加新实体](domain-models#adding-new-entities)。

3.  要创建枚举类型的新属性，请点击 **新属性** 并执行以下操作：<br />

    a. 设置属性 **名称**。 在我们的示例中，属性的名称是 *级*。<br /> b. 设置[**类型**](domain-models-attributes)为**枚举**。<br /> c. 点击**选择枚举**来创建一个新的枚举。<br />

    ![](attachments/domain-models-enumeration/new-attribute-select-enumeration.png) <br/>

    b. 平均输出功率超过1瓦； 在 **选择枚举** 对话框窗口中，现有的枚举显示在列表中。 点击您想要使用的单击，然后点击 **选择**。<br />

    ![](attachments/domain-models-enumeration/selecting-existing-enumeration.png)

现有枚举是为枚举类型的属性选定的。

## 4 属性

关于枚举类型属性属性的详情，请见 [3 属性](domain-models-attributes#attribute-properties) 在 *属性类型* 中。

## 5 阅读更多

* [域模型](域名模型)
* [属性类型](domain-models-attributes) 
