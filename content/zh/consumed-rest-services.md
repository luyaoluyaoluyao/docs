---
title: "已消耗的REST 服务"
parent: "集成"
description: "在Mendix中显示消费的 REST 服务和JSON 概述。"
menu_order: 15
tags:
  - "studio pro"
---

## 1 个REST

国家代表权转移是一种消耗或暴露资源的做法。 由于数据的简单性，它已经受到欢迎，因为不需要在终点之间传输数据的广泛计划或合同。 它采用以下方法：

* 要定位资源的 HTTP URL
* 认证和指定内容类型的HTTP头文件 (例如XML 或 JSON)
* 确定资源操作的 HTTP 方法，例如GET (检索数据) 或 POST (发送数据)

缺少合约和方案可以让您轻松地开始使用 REST 。 然而，许多REST 端点返回了复杂的数据。

[JSON结构](json-structures) 文档有助于为 JSON 数据提供结构：来自示例 JSON 代码片段 在 [Mapping 文档](mapping-documents) 中使用的轻量模式被提取。 [导入映射](import-mappings) 文档将 JSON (or XML) 转换为 Mendix 对象。 和 [导出映射](export-mappings) 文档序列化Mendix 对象到 JSON (或XML)。

## 2 JSON

JavaScript 对象符号(JSON) 是数据的轻量表示方式。

```js
主席:
    "name": "John Smith",
    "age": 23,
    "address": 

        "street": "Dopeylane 14",
        "city": "Worchestire"
    }
}
```

除此之外，对象 `个人` 被描述为属性 `名称`的对应值 `年龄`, 和提及对象 `地址`.
