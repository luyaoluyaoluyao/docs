---
title: "已发布REST 查询参数"
parent: "已发布的rest-service"
menu_order: 40
description: "已发布REST 查询的参数"
tags:
  - "已发布 REST"
  - "查询"
  - "参数"
  - "日期和时间格式"
---

{{% alert type="info" %}}

**已发布的REST service** 功能已引入7.10.0版本。

{{% /报警 %}}

[已发布的REST 操作](published-rest-operation) 的规格包括实现操作的微流程。 这个微流可能需要来自请求的查询字符串的参数。

查询参数只能有原始类型(Boolean、日期和时间、小数、枚举、整数/长或字符串)。

查询参数被添加到路径末尾的格式为 `?name=John&年龄=42` 的提问标记。 这显示在操作的 [示例位置](published-rest-operation#example-location) 中。

这些是一些关于查询参数的附加注释：

* 查询参数是区分大小写
* 日期和时间参数应以 [ISO-8601](https://www.w3schools.com/xml/schema_dtypes_date.asp) 格式输入(例如， `2018-12-31T09:00:00`)
* 当客户端调用操作而没有指定查询参数时， 它在微流程中将有值 `空` (除非它有布尔类型) 这 `false` 默认情况下)
