---
title: "社会联系"
parent: "域名模型"
description: "在 Mendix Studio 中描述关联属性。"
tags:
  - "工作室"
  - "域模型"
---

## 1 导言

一个协会描述了实体之间的关系。 在域模型中，一个协会由两个实体之间的一条线或一条箭头来代表。

在 Mendix Studio 中，社团拥有以下属性：

* [名称](#name)
* [多重性](#multiplicity)
* [删除行为](#delete-behavior)

    ![](attachments/domain-models-association-properties/association-properties.png)

关于该单元，社团可分为两类：

* 一个模块内的关联
* [交叉模块关联](#cross-module-associations)

## 2 个名称 {#name}

协会的名称用来指它来自表格、微流等。

## 3 多重性 {#multiplicity}

多重性定义了可能推荐对象的数量。 一个社团的信用度(或被推荐对象的数量)在社团的任何一侧都以第一位(`1`)或星号(`*`)表示出来。

多重性可以是以下类型：

* 一对一——一个X对象与一个Y对象关联
* 一对多——一个X对象与多个Y对象关联
* 多对多——多个X对象与多个Y对象关联

多重性显示社团的所有者和方向，如果社团是一对多或多对多类型。 在域模型中，它显示为指向方向的箭头。 所有者是社团起始的实体，因此它位于箭头之初。 在一对一的协会中，两个实体都是业主。

![](attachments/domain-models-association-properties/association-domainmodel.png)

如果其类型是一对多或多对多的，您可以交换多重性的方向。 在这种情况下，您将更改关联所有者。

{{% alert type="info" %}}
欲了解更多有关协会推理的详情，所有权和多重性； 查看 [Introduction](/refguide/associations#intro) 部分 of *Associations* in *Studio Pro Guide*。
{{% /报警 %}}

## 4 删除行为 {#delete-behavior}

删除行为定义删除对象时相关对象应发生的情况。 以下选项可以为每一结尾的关联配置。

| 值                                                            | 描述                                                                                                        |
| ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| 保留 {name of entity} 对象(s)                                    | 当一个对象被删除时，关联对象不会被删除。                                                                                      |
| 删除 {name of entity} 对象(s)                                    | 当一个对象被删除时，关联对象也会被删除。                                                                                      |
| 只有当对象未与 {name of other entity} 对象相关时，才删除 {name of entity} 对象 | 一个对象只能在与任何其他对象无关的情况下被删除。 <br />当最终用户试图删除与其他实体对象相关联的对象时，您也可以为他们指定一个错误消息。 例如："您不能删除这个位置，因为一个课程与它相关联。" |

对于删除行为配置的例子， 查看

删除 *中的行为</a> 部分。如何创建基本数据层* 在 *Mendix Studio Pro How-to's* 中。</p> 




## 5 跨模块关联 {#cross-module-associations}

跨单元协会是不同单元实体之间的协会。

{{% alert type="info" %}}

您不能在 Studio 中创建单独的模块。 但如果您在 Studio Pro中拥有不同的模块， 您可以看到不同域模型的列表(系统模块和市场模块除外)，并在工作室进行跨模块关联。 

{{% /报警 %}}

在Studio中，跨模块的联系如下所示：

*  具有此关联的实体旁边的图标：
  
  ![](attachments/domain-models-association-properties/association-icon.png)

*  一个弹出窗口，当您点击图标时显示：
  
  ![](attachments/domain-models-association-properties/association-pop-up.png)

交叉模块关联具有以下属性：

| 财产                   | 描述                                 |
| -------------------- | ---------------------------------- |
| 类型                   | 定义关联的方向，可以是两种类型： **输出** and **输入** |
| 名称                   | 定义关联名称                             |
| [多重性](#multiplicity) | 定义多重性的类型                           |
| Target               | 定义关联的模块(点前的名称)和第二个实体(紧随点之后)。       |




## 6 阅读更多

* [域模型](域名模型)
