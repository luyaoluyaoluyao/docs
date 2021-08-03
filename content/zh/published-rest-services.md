---
title: "发布的REST 服务"
parent: "集成"
#menu_order:
description: "Mendix 应用程序发布的REST 服务概览"
tags:
  - "发布"
  - "REST 服务"
  - "概览"
  - "配置"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-services.pdf)。
{{% /报警 %}}

## 1 导言

添加 [已发布的REST 服务](published-rest-service) 以暴露您的实体和微流程到其他应用，使用REST 标准。

## 2 已发布的REST 服务

当您添加一个已发布的服务时，可用选项的概述，见 [已发布的REST 服务](published-rest-service)。

您可以通过右键点击 [域模型中的实体](domain-model) 轻松暴露一个实体，并选择 [作为REST 资源](generate-rest-resource) 来暴露一个实体。

要发布微流程作为REST 操作，请右键点击编辑器的任意位置，并选择 [发布为 REST 服务操作](publish-microflow-as-rest-operation)。

## <a name="authorization"></a>3 次验证

已发布的REST 服务可以通过基本身份验证、 活动会话身份验证和自定义身份验证。 基本和活动会话身份验证是默认， 当您将应用程序的 [安全等级](project-security) 设置为 **原型/演示**  或 **生产** 时，自动应用它。

如果您不想要基本的身份验证，则有三个选项：

* 您可以选择对于特定发布的REST 服务有 [无身份验证](published-rest-service#authentication) 或者
* 当您 [允许匿名用户](project-security#anonymous-users) 到您的应用时，所有已发布的REST 服务都可以在没有身份验证的情况下使用 或者
* 您可以使用微流程</a> 实现

自定义身份验证</li> </ul> 
  
  {{% alert type="warning" %}}
  
  请注意，网络服务用户不能访问REST 服务。 
  
  {{% /报警 %}}
  
  欲了解更多详情，请查看 [已发布的REST Routing](published-rest-routing) and [需要认证](published-rest-service#authentication) 部分在 *已发布的REST 服务*。
  
  

## <a name="interactive-documentation"></a>4 文件

所有 [已发布的REST 服务](published-rest-service) 都是自动记录的。 此文档可在 `http://yourapp.com/rest-doc` 的应用程序中查阅。 每个服务都有一个交互文档页面，使用 [Swagger UI](https://swagger.io/swagger-ui/)。 您可以与服务交互，看看它是怎样做的。

服务文档可使用 [OpenAPI 2.0](open-api) 格式获取，许多系统和工具都可以读取。 It contains [JSON Schemas](published-rest-service-json-schema) for the messages definitions.



## 5 次日志记录

要记录与您已发布的REST 服务互动的详细信息 设置 **REST 发布的日志级别</a>** 日志节点为 **跟踪**</p> 



## 6 个示例

**如何在Studio Pro 8中发布REST**

{{% youtube Ff_P84NOcZk %}}
