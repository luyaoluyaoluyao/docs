---
title: "HttpRequest & HttpResponse System 实体"
parent: "集成"
---

## 1 导言

`HttpRequest` 是一个向服务器提出请求的系统实体。 `HttpResponse` 代表了服务器的响应。 当 [发布](published-rest-services) 或 [消耗](consumed-rest-services) REST 服务时，使用这些实体。

![](attachments/http-request-and-response-entities/http-request-and-response-domain-model.png)

## 2 HttpRequest {#http-request}

`HttpRequest` 实体具有以下属性：

| 属性                                | 类型  | 默认值      | 描述                  |
| --------------------------------- | --- | -------- | ------------------- |
| `Httpversion` (继承自 `HttpMessage`) | 字符串 | HTTP/1.1 | 协议版本。 您几乎总是可以忽略这个值。 |
| `Uri`                             | 字符串 | 空的       | 传入请求的完整URI，包括查询参数。  |
| `内容` (继承自 `HttpMessage`)          | 字符串 | 空的       | 2. 请求的正文。           |

您可以通过 `HttpHeaders` 关联检索请求头部。

## 3 HttpResponse {#http-response}

`HttpResponse` 实体具有以下属性：

| 属性                                | 类型  | 默认值      | 描述                  |
| --------------------------------- | --- | -------- | ------------------- |
| `Httpversion` (继承自 `HttpMessage`) | 字符串 | HTTP/1.1 | 协议版本。 您几乎总是可以忽略这个值。 |
| `StatusCode`                      | 整数  | 200      | 服务器返回的 HTTP 状态代码。   |
| `ReasonPhrase`                    | 字符串 | 好的       | `状态代码` 的文本表示.       |
| `内容`                              | 字符串 | 空的       | 答复的正文。              |

欲了解更多关于HTTP状态码的信息，请参阅 [W3C Status Code定义规格](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)。

您可以通过 `HttpHeaders` 关联获取或创建响应头部。

一个重要的 `HttpResponse` 头是 `Content-Type`, 它表明了如何解释内容。 关于此标题的更多信息，请参阅 [W3C Content-Type](https://www.w3.org/Protocols/rfc1341/4_Content-Type.html) 的规格。
