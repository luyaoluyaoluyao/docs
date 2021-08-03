---
title: "消耗的 OData 服务"
parent: "集成"
menu_order: 5
description: "工作室消耗的OData服务概览"
tags:
  - "studio pro"
---

## 1 导言

数据可以通过 [已发布的 OData 服务](published-odata-services) 从应用程序发布，供其他应用使用。 消耗的 OData 服务可以通过 [Mendix Data 集成应用程序中的外部数据源](/data-hub/)。

Mendix Data Hub 能够将来自不同来源的数据源整合到您的 Mendix 应用中。  在 [数据枢纽目录中注册的 OData 服务](/data-hub/data-hub-catalog/) 揭示了可以拖拽到您的域模型中的实体通过 [数据枢纽窗格](data-hub-pane) 作为外部实体。 添加到您应用的OData服务文档为检索服务和曝光实体的元数据提供了信息。

关于消耗的 OData 服务文档和更新您应用中消耗的 OData 服务的详细信息，请参阅 [消耗的 OData 服务](consumed-odata-service)。

{{% alert type="info" %}}
Mendix 数据集群是一个许可产品。 使用外部实体消耗OData服务需要许可证， 以及您拥有的许可证类型将定义可以消耗多少数据记录。  欲了解更多详情，请参阅 *消耗的OData服务要求中的 [数据中心许可证限制](consumed-odata-service-requirements#license-limitations) 部分*。 要了解更多关于您的数据集群许可证的信息，请联系 [Mendix Support](https://support.mendix.com)。
{{% /报警 %}}

关于已发布的OData服务必须支持的功能以及从Mendix数据模型转换和转换到Mendix数据模型的工作的详细信息。 查看 [消耗的 OData 服务要求](consumed-odata-service-requirements)。

## 2 OData服务和外部实体

当外部实体被用于应用程序时， 该实体的相关数据集通过消耗的OData服务合同中的信息检索并归还。

### 2.1 外部实体

与可持久实体相比，外部实体有一些局限性：

* 外部实体是只读
* 外部实体不能使用总功能（平均、金额、最大、最小）
* 外部实体的 XPath 约束有某些限制(例如) 您不能过滤可持久实体和外部实体之间的关联)
* 外部实体不能用于数据集
* [无法设置外部实体访问规则中的 XPath 约束](/refguide/xpath-constraints)

外部实体之间的关联(根据起源应用的定义)将在域模型中显示。 您只能使用双方曝光的关联。

您可以在本地 [可持久实体](persistability#persistable) 和外部实体之间创建关联。 对这些协会来说，可持久的实体必须是业主。

### 2.2 消耗的OData服务

当一个外部实体被拖动到域模型时， 添加到模型的  **消耗的 Odata** 文档将从服务端显示元数据合同的值。

在 **数据枢纽** 面板中， 服务和实体将被显示为在搜索结果面板和 **App** 面板中消费。

如果指定服务端的元数据合同不同于当前应用模型中的合同， 这将在 **数据枢纽** 窗格搜索结果和  **属性** 带蓝色服务的窗格 **更新** 箭头：

{{% image_container width="300" %}}![Data Hub Pane update](attachments/consumed-odata-service/project-pane-update-available.png){{% /image_container %}}

This means that the consumed service will have to be **Updated** to the new contract. 如果不这样做，当必须根据过时的合同从终点检索数据时，这将造成错误。 消耗的耗氧物质服务合同的变化在 [更新或切换耗用的耗氧物质服务](consumed-odata-service#updating) 中得到进一步描述。

## 3 运行时间方面的考虑

每次检索消耗的OData服务都需要该服务端点。 因此，外部消费实体的数据检索可能比当地可持久实体要慢。
