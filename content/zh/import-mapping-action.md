---
title: "使用映射导入"
parent: "一体化活动"
tags:
  - "studio pro"
  - "导入 xml"
  - "导入映射文件"
  - "导入映射"
  - "集成活动"
menu_order: 30
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/import-mapping-action.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

使用 **导入映射** 活动允许您将存储在 XML 或 JSON 文档中的数据导入到 [域模型](domain-model) 实体。

## 2 属性

具有映射属性的导入示例显示在下面的图像中：

![带映射属性导入](attachments/integration-activities/import-with-mapping-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

带映射属性窗格的导入由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

![](attachments/integration-activities/import-mapping-action.png)

### 3.1 变量

输入变量可以是字符串变量的名称、文件文档、 [HttpRequest](http-request-and-response-entities#http-request)或 [HttpRequest](http-request-and-response-entities#http-response)。 文件文档、HttpRequest或 HttpResponse 应该是 XML 或 JSON 。

### 3.2 映射

[导入映射](import-mappings) 定义如何将XML 或 JSON 转换为对象。

### 3.3 输入内容类型

如果导入映射基于一个 [消息定义](message-definitions)，它可以导入 XML 和 JSON 。 选择输入对象是否包含 XML 或 JSON

### 3.4 输入包含

如果导入映射基于一个 [消息定义](message-definitions), 它可以导入单个对象和列表。 选择输入是单个对象还是对象列表。

### 3.5 如果没有找到对象

You can indicate what should happen **if no object was found** when the import mapping has checked the box **decide this at the place where the mapping gets used**.

### 3.6 参数

如果选中的映射需要一个参数，您可以在此选择它。

### 3.7 Range

 如果映射返回一个列表, 您可以选择一个范围来确定多少对象被映射并返回.

| Range | 含义                                     |
| ----- | -------------------------------------- |
| 所有的   | 映射并返回所有对象。                             |
| 第一页   | 映射并只返回第一个对象。 该动作的结果将是单个对象而不是列表。        |
| 自定义   | 映射并返回给定数量的对象(限制)。 限制是一个微流程表达式，应产生一个数字。 |

### 3.8 承诺 {#commit}

指示是否应将所产生的对象投入数据库，以及是否应触发事件处理程序。

| 选项      | 描述                                                     |
| ------- | ------------------------------------------------------ |
| 否       | 对象已保存在数据库中，触发了 [事件处理程序](event-handlers)。               |
| 是的，没有事件 | 对象已保存在数据库中，但 [事件处理程序](event-handlers) 未触发(默认)。         |
| 否       | 对象创建时没有保存到数据库中。 您将需要 [提交操作](committing-objects) 来保存它们。 |

### 3.9 校验反对Schema

{{% alert type="info" %}}

验证属性仅适用于从XML中选择基于 [XML schema](xml-schemas) 或 [消费网络服务的地图的导入映射](consumed-web-service)

{{% /报警 %}}

确定导入动作是否应该根据 [XML schema](xml-schemas) 验证传入的 XML 模式。

设置为 _是了_ 可以影响性能！

默认： *否*

### 3.10 存储在变量中

选择是否存储导入结果。

### 3.11 类型

结果类型。

### 3.12 名称

导入结果的名称。

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}
