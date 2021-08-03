---
title: "发布的REST 操作的 JSON 方案"
parent: "已发布的技术详细信息"
menu_order: 20
description: "对于操作请求机构和操作结果描述JSON方案"
tags:
  - "已发布 REST"
  - "JSON"
  - "图案"
  - "操作"
  - "请求内容"
  - "结果"
  - "消息定义"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/published-rest-service-json-schema.pdf)。
{{% /报警 %}}

## 1 导言

当您 [发布休息服务](published-rest-services), 为 [OpenApi (Swagger) 文档页面](published-rest-services#interactive-documentation) 生成它。 它包括关于服务能够接收和返回的信息结构的说明。 这个结构是使用 JSON 方案描述的。

对进出口绘图进行定义的操作将生成此种图案， 但仅适用于基于 [消息定义](message-definitions) 的映射。

JSON模式是根据这里记录的规则生成的。

## 2 定义

OpenApi schema包含实体参数和返回类型的定义。 如果已配置的导入或导出映射基于消息定义，就会有一个定义。

### 2.1 电文的定义

```json
"#definition_name#": ~ 
  "type": "object",
  "properties": [
     #attribute_name#: #attribute_schema#
  ]
}
```

默认情况下，定义名称是映射所基于的消息定义的名称。 您可以通过设置映射的 _公开名称_ 来选择您自己的定义名称。

### 2.2 属性

属性的模式取决于属性类型：

| 属性类型       | 属性模式                                             |
| ---------- | ------------------------------------------------ |
| Autonumber | `• “type”：“整数”、“格式”：“int64”}`                    |
| 二进制文件      | `• “type”: "string", "格式": "binary" }`           |
| Boolean    | `{ "type": "boolean" }`                          |
| 日期和时间      | `• “type”: "string", "格式": "date-time" }`        |
| 小数         | `· "type": "number" }`                           |
| 枚举数        | `● "type": "string", "enum": ["男性", "Female"] }` |
| 哈希字符串      | `欧共体：“type”：“string”}`                           |
| 整数         | `• “type”：“整数”、“格式”：“int32”}`                    |
| 长          | `• “type”：“整数”、“格式”：“int64”}`                    |
| 字符串        | `欧共体：“type”：“string”}`                           |

## 用于操作请求体的 3 JSON 方案

当操作有一个实体参数时，它有一个模式。 此schema是指当您根据消息定义选择导入映射时的定义。

如果参数是对象：

```json
• "$ref": "#/definitions/#definition_name#"}
```

如果参数是列表：

```json
主席: 
  "type": "array",
  "items": [}"$ref": "#/definitions/#definition_name#"}"
}
```

如果没有导入映射，或者映射不是基于消息定义的：

```json
· "type": "file" }
```

## 用于操作结果的 JSON 方案

操作结果也有一个方案。 格式取决于结果的类型。

当没有导出映射或者导出映射不是基于消息定义的：

```json
· "type": "file" }
```

当微流程返回对象时：

```json
• "$ref": "#/definitions/#definition_name#"}
```

当微流程返回列表时：

```json
主席: 
  "type": "array",
  "items": [}"$ref": "#/definitions/#definition_name#"}"
}
```

当微流程返回原始时，模式取决于类型：

| 微流程结果   | 图案                      |
| ------- | ----------------------- |
| 无       | (无)                     |
| 二进制文件   | `· "type": "file" }`    |
| Boolean | `{ "type": "boolean" }` |
| 日期和时间   | `· "type": "file" }`    |
| 小数      | `· "type": "number" }`  |
| 枚举数     | `· "type": "file" }`    |
| 整数/经度   | `· "type": "整数" }`      |
| 字符串     | `· "type": "file" }`    |
