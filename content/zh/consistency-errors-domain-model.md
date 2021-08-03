---
title: "域名模型一致性错误"
parent: "一致性错误"
menu_order: 40
description: "描述Mendix Studio中的域模型一致性错误以及修复这些错误的方法。"
tags:
  - "工作室"
  - "一致性错误"
  - "错误"
  - "域模型"
---

## 1 导言

在本文件中，我们解释如何解决在Mendix Studio配置域模型时可能发生的最常见的一致性错误。 欲了解更多域模型信息，请参阅 [域模型](domain-models)。

一致性错误的一个例子是两个实体的名称相同。

{{% alert type="info" %}}

此文档没有描述 *所有* 个错误，因为有许多错误可能发生。 其中有些简单，无需额外解释，另一些则极少和（或）严重依赖使用案件。

{{% /报警 %}}

一些错误有错误代码，如果这些错误在文档中描述，Studio就有一个可点击的链接到相应的文档。 在这种情况下，其他人没有错误代码。 您可以手动搜索文件中是否描述了某个错误 (您可以通过在 **检查** 面板中看到的消息搜索)。

## 2 域名一致性模型错误

下面的表描述了配置域模型时您可能遇到的最常见错误：

| 错误代码   | 检查面板中的消息                                                                  | 错误的原因                                                                                                                                                                                                                     | 修复路径                                                    |
| ------ | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| CE0001 | 可持久实体与不可持久实体之间的关联必须从不可持久实体开始并拥有者“默认”。                                     | 您创建了一个可持久实体和不可持久实体之间的关联。 协会从可持久的实体转为不可持续的实体（因此社团的所有者是可持久的实体）。 可持久的实体储存在数据库中，不可持续的实体储存在内存中。 您可以从内存指向数据库，但不是其他方式。 For more technical information, see [Persistability](/refguide/persistability) in the *Studio Pro Guide*. | 打开社团属性并交换社团的方向，从而改变社团所有人； 或改变实体财产中某一实体的可持久性。            |
| CE0017 | 无效的 [删除行为](domain-models-association-properties#delete-behavior)。         | 删除社团中的实体行为互相矛盾时发生错误。 关于发生错误时案例的更多信息，请参阅 [删除行为一致性错误和修复](#delete-behavior) 部分的方法。                                                                                                                                           | 关于如何修复此错误的信息，请参阅 [删除行为一致性错误和如何修复](#delete-behavior) 部分。 |
| CE0021 | 类型 {attribute type} 的属性仅在可持久实体中被支持。                                       | 不可持续的实体具有类型为自动卸载器或二进制的属性。 这些类型的属性需要存储到数据库中。                                                                                                                                                                               | 通过启用属性中的相应选项使实体可持久；或更改属性类型。                             |
| CE0065 | 模块 {name of the entity} 中重复的名称 {name of the module}。 实体、协会和点数不能分享名字。      | 您的域模型中有几个具有相同名称的实体。                                                                                                                                                                                                       | 重命名一个实体；所有实体名称都应是唯一的。                                   |
|        | 选中的属性 {name of attribute} 模棱两可。 它不允许有多个实体 {name of attribute}             | 您的域模型中有几个具有相同名称的实体。 所以这些重复的实体的属性给您带来了错误。                                                                                                                                                                                  | 重命名一个实体；所有实体名称都应是唯一的。                                   |
|        | 选定的关联 {name of the association} 模糊不清。 它不允许有多个关联 {name of the association} | 您的域模型中有一个与相同名称的关联。                                                                                                                                                                                                        | 重命名一个社团；所有社团名称都应该是唯一的。                                  |

### 2.1 删去行为一致性错误和修复其{#delete-behavior}

 与删除行为相关的一致性错误可在下列情况下发生：

*  删除从关联开始的实体的行为设置为 *删除 {name of entity} 个对象* 并且删除关联所指向的实体的行为设置为 *只有当它与 {name of other entity} 对象无关时才删除 {name of entity} 个对象*

    ![删除行为错误示例一](attachments/consistency-errors-domain-model/delete-behavior-error-example1.png)

*  删除关联从设置为 *的实体的行为。只有当它与 {name of other entity} 对象无关时，才删除 {name of entity} 对象* 并且删除关联点被设置为 *删除 {name of entity} 对象*

    ![删除行为错误示例二](attachments/consistency-errors-domain-model/delete-behavior-error-example2.png)

*  删除两个实体在关联中的行为设置为 *只有当它没有与 {name of other entity} 对象相关时才删除 {name of entity} 对象*

    ![删除例子3中的行为错误](attachments/consistency-errors-domain-model/delete-behavior-error-example3.png)

您可以通过以下方式修复删除行为错误：

* 如果您设置删除一个实体的行为为 *只有当它没有与 {name of other entity} 对象相关时才删除 {name of entity} 对象*, 设置删除其他实体的行为为 *保留 {name of entity} 对象*
* 设置两个实体的删除行为为 *保留 {name of entity} 对象*
* 设置删除两个实体的行为为 *删除 {name of entity} 个对象(s)以及*

欲了解更多关于删除行为的信息，请参见 [删除行为](domain-models-association-properties#delete-behavior) 部分 *关联* 中。

## 3 阅读更多

* [页面一致性错误](consistency-errors-pages)
* [导航一致性错误](consistency-errors-navigation)
* [微流一致性错误](consistency-errors-microflows)
* [检查](检查)