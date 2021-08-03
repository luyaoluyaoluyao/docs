---
title: "OpenAPI 2.0 文档"
parent: "已发布的技术详细信息"
menu_order: 30
description: "由发布的REST 服务生成的 swagger.json 文件描述"
tags:
  - "swagger"
  - "swagger.json"
  - "OpenAPI 2.0"
  - "文件"
  - "路径"
  - "操作"
  - "studio pro"
---

## 1 导言

所有 [已发布的REST 服务](published-rest-service) 都是自动记录的。 系统生成一个 *swagger.json* 文件，符合 [OpenAPI 2.0 规格](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md) (前称“交换规格”)。 This file can be [saved from Studio Pro](published-rest-service#export-swagger-json) or downloaded from */rest-doc/servicename/swagger.json*.

如果您需要与另一个应用的服务进行沟通，您可以使用 *交换器。 在 Microsoft Visual Studio 、React、Angular 和 Java 等系统中生成一个 API 的 son* 文件。 这使得您的不同应用之间的沟通变得容易。

许多流行的 API 工具支持 OpenAPI 2。 , including [SoapUI](https://www.soapui.org/), [Postman](https://www.getpostman.com/), , , 和 [Swagger UI](https://swagger.io/swagger-ui/) (支持工具的较长列表见 [交换工具)。 o/commercial-tool](https://swagger.io/commercial-tools/) 这意味着您可以很容易地从任何这些工具测试您已发布的服务。

下面是一个技术描述，生成了 *swagger.json* 文件的部分。

## 2 个模式

主schema对象记录该服务。

服务</a> 的 公开文档。</td> </tr> 

</tbody> </table> 



## 3 条路径

服务的操作按 [操作路径](published-rest-operation#operation-path) 分组. 每个组生成一个 `路径项目` ，以操作路径作为名称。 `路径项目` 在组中的每个操作都有 `操作` 属性。



## 4 业务

每次操作生成 `操作` 对象：

| 财产        | 生成的值                                                |
| --------- | --------------------------------------------------- |
| `标签`      | 资源的 [名称](published-rest-resource#name)。             |
| `summary` | 操作的 [公开文档摘要](published-rest-operation#summary)。     |
| `描述`      | 操作的 [公开文档描述](published-rest-operation#description)。 |
| `参数`      | 路径和查询参数。 对于POST、PUT、PATCH和OPTIONS 方法，也有一个物体参数。      |
| `回应`      | OK 响应。 如果启用安全性，这也是未经授权的反应。                          |
| `已弃用`     | 当操作被标记为已弃用时，设置为 true。                               |
