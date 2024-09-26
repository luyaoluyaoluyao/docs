---
title: "已发布REST 请求路由"
parent: "已发布的技术详细信息"
menu_order: 10
description: "一个流程图，显示一个示例请求是如何处理的，应用了什么安全，以及服务返回了什么。"
tags:
  - "流程图"
  - "处理中"
  - "安全"
  - "服务"
  - "资源"
  - "操作"
  - "方法"
  - "身份认证"
  - "返回代码"
  - "已发布 REST"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-routing.pdf)。
{{% /报警 %}}

当REST HTTP 请求到达服务器时，服务器需要确定要执行哪个 [操作](published-rest-operation) 以及应用什么安全性。

这个流程图显示了一个示例请求、如何处理以及服务在不同情况下返回的内容。

请参考此流程图来回答以下问题：

* 我的 URL 将执行哪个REST 操作微流程？
* 在REST 操作微流中发生例外情况时会发生什么？
* REST 服务的基本身份验证是如何工作的？
* REST 服务的匿名身份验证是如何工作的？
* 当REST 操作微流程返回空的 HTTPResponse时会发生什么？
* 为什么我的REST 服务返回 _400 错误请求_？
* 为什么我的REST 服务返回 _401 未授权_？
* 为什么我的REST 服务返回 _404 找不到_？
* 为什么我的REST 服务返回 _405 方法不允许_？

示例请求是 `GET /rest/petstore/pet/12`。

![](attachments/published-rest-service/determine-operation.png)
