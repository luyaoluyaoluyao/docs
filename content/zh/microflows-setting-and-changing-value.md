---
title: "设置 & 更改不同活动的值"
category: "微型流动"
menu_order: 50
description: "描述在 Mendix Studio 中设置对象或变量初始值的过程。"
tags:
  - "工作室"
  - "微流"
  - "设置值"
  - "变量"
---

## 1 导言

本文档描述如何设置和更改Mendix Studio微流中各种活动的值。

当您配置以下活动的属性时，您需要为对象/变量分配一个值：

* **创建对象** - 您可以创建一个具有此活动的对象，并为对象的属性提供初始值
* **创建变量** - 你可以创建一个变量并通过此活动给它分配一个值

您也可以在配置以下活动时更改值：

* **更改对象** - 可以用来更改此对象的现有对象或属性
* **更改变量** - 更改当前微流中现有变量的值

您也可以为 **结束事件** 配置返回值——微流将停止的位置。

关于这些活动功能的更多信息，见 [微流](microflows)。

## 2 设置创建对象的初始值和更改更改对象的值

 要设置对象的初始值或改变其值，请执行以下操作：

1. 添加 **创建对象**/**将对象** 活动更改为微流程。 欲了解更多信息，请参阅 *Microflow* 中的 [添加新事件或活动](microflows#adding-activity-to-microflow) 部分。
2. 点击活动查看其属性。
3.  选择活动的数据源，然后点击 **添加新值**

    ![](attachments/microflows-setting-and-changing-value/add-new-value.png)

4. 在 **设置初始值**/**更改值对话框**中，选择一个属性或关联。
5.  设置初始值 (用于 **创建对象**) 或分配一个新值 (用于 **更改对象**) 在 **变量/属性** **常量**, 或 **表达式** 选项卡。  关于这些标签的更多信息，请参阅 [常见元素](#set-value-common-elements) 部分。

    ![](attachments/microflows-setting-and-changing-value/set-initial-value-object-dialog.png)

## 3 设置创建变量和更改变量值的初始值

要设置一个变量的初始值或改变其值，请执行以下操作：

1. 添加 **创建变量**/**将变量** 改为微流程。 关于如何在微流中添加元素的更多信息 查看 [在 *Microflow* 中添加新事件或活动](microflows#adding-activity-to-microflow) 部分。
2. 点击活动查看其属性。
3.  选择活动的数据类型，然后点击 **设置初始值** / **更改值**

    ![](attachments/microflows-setting-and-changing-value/set-initial-value-var.png)

4.  设置初始值 (用于 **创建变量**) 或分配一个新值 (用于 **更改变量**在 **变量/属性**中设置一个新值 **常量**, 或 **表达式** 选项卡。  关于这些标签的更多信息，见第 [部分 Common Elements](#set-value-common-elements) 部分。

    ![](attachments/microflows-setting-and-changing-value/change-value-var-dialog.png)

## 4 为结束事件配置退货值

返回值是返回到流或调用当前流的小部件的值。 要配置返回值，请执行以下操作：

1. 将 **结束事件** 添加到微流程或选择现有的结束事件。 欲了解更多信息，请参阅 *Microflow* 中的 [添加新事件或活动](microflows#adding-activity-to-microflow) 部分。
2. 点击事件查看其属性。
3.  将 **返回** 选项设置为 **值**.

    ![](attachments/microflows-setting-and-changing-value/end-event-returns-value-setting.png)

4.  选择数据类型，然后点击 **值** 来进行配置。

    ![](attachments/microflows-setting-and-changing-value/configure-return-value.png)

5.  在 **变量/属性**中设置返回值。 **常量**, 或 **表达式** 选项卡。 欲了解更多信息，请参阅 [常见元素](#set-value-common-elements) 部分。

    ![](attachments/microflows-setting-and-changing-value/configure-retuen-value-dialog.png)

## 5 共同要素 {#set-value-common-elements}

您可以在配置值时看到下列共同元素：

* **变量/属性** 标签
* **常量** 标签
* **表达式** 标签

下表说明了这些标签的功能：

| Tab   | 描述                                                                                                                                                                                                                                            |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 变化/属性 | 显示与您想要创建或更改的属性类型、关联或变量匹配的变量和属性。 <br />例如，当您选择十进制类型的属性时，小数和整数类型的变量将会在标签中显示。 这是因为十进制可以包含整数 (整数)。 然而，如果您选择整数类型的属性，将不会显示小数点的变量， 因为整数 (整数) 不能包含小数。  欲了解更多关于属性类型的信息，请参阅 [属性](domain-models-attributes)。<br />**备注** 长长类型的属性将作为整数显示在微流中。 |
| 常数    | 通过这个标签，您可以从枚举类型的属性中选择一个新值。                                                                                                                                                                                                                    |
| 表达式   | 通过此标签，您可以根据您在表达式中写入的内容分配属性、关联性或变量不同的值。 关于表达式的更多信息，见 [微流程表达式](microflows-expressions)。                                                                                                                                                         |

## 6 阅读更多

* [微型流动](微流)
* [微流程表达式](microflows-expressions)
