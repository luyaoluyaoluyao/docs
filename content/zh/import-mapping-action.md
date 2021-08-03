---
title: "导入映射操作"
parent: "微观流动活动"
---

{{% alert type="info" %}}
这种活动只能用于微流，而不能用于纳米流。
{{% /报警 %}}


## 1 导言

通过导入映射动作，您可以将存储在 XML 或 JSON 文档中的数据导入到 [域模型](domain-model) 实体。

![](attachments/import-mapping-action/import-mapping-action.png)

## 2 Input

### 2.1 变量

输入变量可以是字符串、文件文档、 [HttpRequest](http-request-and-response-entities#http-request)或 [HttpRequest](http-request-and-response-entities#http-response)。 文件文档、HttpRequest或 HttpResponse 应该是 XML 或 JSON 。

{{% alert type="info" %}}
支持HttpRequest 已添加到7.11.0版本。 早期版本需要一个包含HttpRequest 内容的字符串变量。
{{% /报警 %}}

{{% alert type="info" %}}
支持HttpResponse 已添加到版本7.22.0。 早期版本需要一个包含HttpResponse 内容的字符串变量。
{{% /报警 %}}

## 3 导入映射

### 3.1 映射

[导入映射](import-mappings) 定义如何将XML 或 JSON 转换为对象。

### 3.2 Input Content Type

{{% alert type="info" %}}

这个功能是在版本7.10.0中引入的。

{{% /报警 %}}

如果导入映射基于一个 [消息定义](message-definition)，它可以导入 XML 和 JSON 。 选择输入变量是否包含 XML 或 JSON

### 3.3 输入包含

{{% alert type="info" %}}

这个功能是在版本7.10.0中引入的。

{{% /报警 %}}

如果导入映射基于一个 [消息定义](message-definition)，它可以导入单个对象和列表。 选择输入变量是否包含单个对象或对象列表。

### 3.4 如果没有找到对象

{{% alert type="info" %}}

该功能是在7.17.0版本中引入的。

{{% /报警 %}}

You can indicate what should happen **if no object was found** when the import mapping has checked the box **decide this at the place where the mapping gets used**.

### 3.5 参数

如果选中的映射需要一个参数，您可以在此选择它。

### 3.6 范围 (如果映射返回一个列表)

范围决定有多少对象被映射并返回.

| Range | 含义                                     |
| ----- | -------------------------------------- |
| 所有的   | 映射并返回所有对象。                             |
| 第一页   | 映射并只返回第一个对象。 该动作的结果将是单个对象而不是列表。        |
| 自定义   | 映射并返回给定数量的对象(限制)。 限制是一个微流程表达式，应产生一个数字。 |

### 3.7 提交 {#commit}

指示是否应将所产生的对象投入数据库，以及是否应触发事件处理程序。

| 选项      | 描述                                                     |
| ------- | ------------------------------------------------------ |
| 否       | 对象已保存在数据库中，触发了 [事件处理程序](event-handlers)。               |
| 是的，没有事件 | 对象已保存在数据库中，但 [事件处理程序](event-handlers) 未触发(默认)。         |
| 否       | 对象创建时没有保存到数据库中。 您将需要 [提交操作](committing-objects) 来保存它们。 |

## 4 次验证

{{% alert type="info" %}}

验证属性仅适用于从XML中选择基于 [XML schema](xml-schemas) 或 [消费网络服务的地图的导入映射](consumed-web-service)

{{% /报警 %}}

### 4.1 校验反对方案

确定导入动作是否应该根据 [XML schema](xml-schemas) 验证传入的 XML 模式。

设置为 _是,_ 可以大大降低性能!

*默认值：* 否

## 5 个输出

### 5.1 存储在变量中

选择是否将导入结果存储在一个变量中。

### 5.2 类型

输出变量的类型。

### 5.3 姓名

持有导入结果的变量的名称。
