---
title: "自定义认证微流程参数"
parent: "已发布的技术详细信息"
menu_order: 40
description: "已发布的REST 服务的参数传递到自定义身份验证微流"
tags:
  - "已发布 REST"
  - "自定义身份验证"
  - "微流"
  - "参数"
  - "参数"
  - "查询"
  - "标题"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-authentication-parameter.pdf)。
{{% /报警 %}}

## 1 导言

当客户端调用一个操作时，将执行已发布REST 服务的自定义身份验证微流。 客户端的请求包含标题，可能包含查询参数，这些参数可以传递给身份验证微流。

当您点击认证微流程旁边的 **参数** 按钮时， **认证微流程参数** 对话框将出现。 在这个对话框中，您可以设置参数。

## 2 个参数

下面的信息为您提供了微流参数的概览，并解释了其值从哪里取出。 点击 **添加** 以添加参数， **编辑** 以更改参数。

请确保在这里添加所有微流参数。

### 2.1 参数类型

指定参数来自何处。 可能的值是

* **查询** - 当请求包含像 `这样的查询字符串时？ ame=John&年龄=42`, 你可以通过添加查询参数传递到微流程。 欲了解更多信息，见 [已发布REST 查询参数](published-rest-query-parameters)。

* **标头** — — 页眉参数的值从 (第一个)请求标题带有该名称的值。

### 2.2 姓名

参数的名称。 对于标题参数，这应该是请求标题的名称。

### 2.3 数据类型

指定参数类型。 只支持原始类型。

### 2.4 微流程参数

指定将用此操作参数的值填充的微流参数。 您应该始终选择一个。
