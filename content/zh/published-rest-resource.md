---
title: "发布的REST 资源"
parent: "已发布的rest-service"
menu_order: 50
description: "发布的REST 资源的可配置选项"
tags:
  - "已发布 REST"
  - "资源"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-resource.pdf)。
{{% /报警 %}}

## 1 导言

已发布的REST 资源是 [已发布的REST 服务](published-rest-service) 的一部分，是可以定义一个或多个 [操作](published-rest-operation) 的项目集合。

您可以从您的域模型中的实体生成已发布的REST 资源。 查看 [生成已发布的REST 资源](generate-rest-resource)。

## 2 概况

### <a name="name"></a>2.1 资源名称

资源名称独特标识 [服务](published-rest-service) 中的资源。 它是操作位置的一部分，所以它不能包含空格或特殊字符。

## <a name="public-documentation"></a>2.2 公开文件

公共文档被用于服务的 [OpenAPI (Swagger) 文档页](published-rest-services#interactive-documentation) 中。 您可以使用 [GitHub-flavered markdown](gfm-syntax) 作为丰富文本。
