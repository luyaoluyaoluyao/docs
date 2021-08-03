---
title: "消耗的OData服务要求"
parent: "消费-odata-服务"
menu-order: 20
description: "Mendix消耗的OData服务的要求。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/consumed-odata-service-requirements.pdf)。
{{% /报警 %}}

## 1 导言

本文件说明将要消耗的OData服务的要求。 这些要求在运行时没有得到进一步核实，预计将予以维持。 如果这些要求没有得到满足，就可能产生错误。

## 2 消耗的OData服务所需经费

Mendix 应用所使用的耗氧物质服务的要求如下：

* OData服务必须是返回 Atom XML的 OData v3 服务或返回 Atom XML 或 JSON 的 OData v4 服务
* 它应该支持OData种子上的查询，包括 `$filter` `$orderby`, `$top`, , `$skip`, `$expand`, 和 `$count` (或 `$inlinecount`)

## 3 对服务实体和属性的要求

本节描述在 Mendix 应用程序支持的消耗的 OData 服务。 在域模型中使用外部实体之前检查这些功能。

### 3.1 实体

词汇注释可以在服务中用于表示不支持的功能。 实体集识别以下词汇表注释：

* **计数** -- 将实体设置标记为 `Countable="false"` 阻止用户将实体添加到项目
* **可过滤** -- 将实体设置为 `Filterable="false"` 将所有属性设置为 不可过滤。
* **可排序** -- 将实体设置为 `Sortable="false"` 将所有属性设置为不可排序。
* 将一个实体设置为 `Filterable="false"` and `Sortable="false"` 将所有属性设置为不可过滤和不可排序； 用 `NonFilterableProperties标记属性` 注解或 `NonSortableProperties` 注解设置特定属性为不可过滤或不可排序。

一个实体只有在可以通过一个实体集访问时才能使用。

此外，一个实体只有在用钥匙识别出来的情况下才能使用。 只要满足以下条件，密钥可以由一个或多个属性组成：

* 属性不能为空(因此他们必须有 `isNullable="false"`
* 只允许以下类型： `Byte`, `SByte`, `Int16`, `Int32`, `Int64`, `布尔`, `十进制`, `单一`, `双精度`和 `字符串`
* 如果类型是 `字符串`, 必须指定 `MaxLength`

### 3.2 属性

{{% alert type="warning" %}}
无法使用标记为 `FC_KeepInContent=false` 的属性。
{{% /报警 %}}

属性类型必须是原始的(而不是复杂的集合或计数)。 您应用中的属性类型将基于OData元数据中的属性类型。 如下表所示：

| OData Type                | 菜单类型                                  |
| ------------------------- | ------------------------------------- |
| 二进制文件                     | 二进制(但见3.4)                            |
| Boolean                   | Boolean <sup><small>[1]</small></sup> |
| Byte, SByte, Int16, Int32 | 整数                                    |
| 日期时间、 日期时间偏移量             | 日期/时间                                 |
| 十进制, 双倍, 单面               | 小数 <sup><small>[2]</small></sup>      |
| Int64                     | 长                                     |
| 字符串，Guid                  | 字符串                                   |
| (其他)                      | (Ignored)                             |

{{% alert type="warning" %}}
当OData端点含有操作时，这些操作不会导入消耗的OData服务。 您可以使用 [调用 REST 服务](call-rest-action) 活动来调用这些操作。
{{% /报警 %}}

<sup><small>[1]</small></sup>: 在 Mendix, Booleans 不能为空。 如果服务返回 null，则Mendix 中的值将为false。

<sup><small>[2]</small></sup>: 目前不支持在 [Mendix 十进制范围之外的十进制值](attributes#type)。 如果服务返回范围以外的值，将出现错误。

### 3.3 概述

消耗的OData服务不支持进口一般化和专业化。 这意味着原始应用发布的OData服务合同将显示专业化为独立实体，其中包括一般化的属性以及专门实体的属性。

这意味着当您消耗Mendix OData端点时，不必同时消耗一种一般化及其专业化。 专业化现在将成为一个具有一般性特征和协会的实体。

目前离散的“专门化”实体将包括与已公布的OData服务中的其他曝光实体进行一般化的社团。

{{% alert type="warning" %}}
当一个一般化实体和一个专门实体在同一服务部门暴露时， 当这两个实体被消耗时，只有用于概括的协会才能看到。 现在分散的专业化将有继承的协会。 这方面的一个可能的工作是在不作一般化的情况下发布一项专业化的服务。 或者，一般化协会不应公布，从而可以保留专业领域中继承的协会。
{{% /报警 %}}

### 3.4 二进制属性

支持二进制数据格式为 *个介质实体*。 当媒体实体被拖入域模型时，将创建一个相应的外部实体。 该实体将有一个带有二进制数据的 `内容` 属性。

目前，二进制数据只能通过 Java 操作访问。

### 3.5 协会

OData v3 关联只有在有两个目的时才能使用。

OData v4 导航属性只有在有伙伴的情况下才能作为一个社团使用。

## 4 数据集许可限制 {#license-limitations}

Mendix Data Hub 是一个单独的许可产品。 The type of license that you have determines the total number of data objects that can be requested from a consumed OData service *per day* for *each* runtime instance of an app.

目前有两种类型的 Data Hub 许可：

* **Data Hub** - 这是 *默认的* 许可证，但不限制可以消耗的 OData 对象的数量。

* **Freemium** - 这使您能够为每个运行时的每日总共检索1000耗氧物质物体。 超过这一限制后，用户试图检索更多数据时将发生错误。 每天消耗的物品数量在午夜在 Mendix Runtime 调度器时区重置(可以在应用程序 [Project 设置](project-settings#scheduled) 中定义)。

  ●{% alert type="info" %}}Freemium Data Hub 许可证只是在邀请的基础上签发。 {{% /报警 %}}
  {{% alert type="info" %}}For Mendix 8.12.3 and later, apps running without a [Mendix license](/developerportal/deploy/licensing-apps-outside-mxcloud) (and also when running from the Studios) do not have this limitation. 这也意味着您可以从工作室运行您的应用而不受数据集许可限制。 {{% /报警 %}}

请联系您的 [Mendix Admin](/developerportal/control-center/index#company) 或Data Hub Admin 来找出您的组织拥有哪种类型的数据集许可协议。


### 4.1 地方发展

当地开发必须获得与自由金属模型相同的许可证。 您有能力检索总共1000个OData对象，然后将发生错误。 可以通过重启应用来重置它。
