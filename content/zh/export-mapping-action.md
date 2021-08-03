---
title: "使用映射导出"
parent: "一体化活动"
tags:
  - "studio pro"
  - "集成活动"
  - "导出映射操作"
  - "导出到 xml"
menu_order: 40
---

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}


## 1 导言

The **Export with mapping** activity allows you to export the data stored in [domain model](domain-model) entities into an XML document, JSON document, or string variable.

## 2 属性

导出映射属性的示例在下面的图像中显示：

![以映射属性导出](attachments/integration-activities/export-with-mapping-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

导出具有映射属性的窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 出口映射

[导出映射](export-mappings) 动作定义 [域模型](domain-model) 中的数据如何与 XML schema 或 JSON 结构相对应。

### 3.2 参数类型

如果 [导出映射](export-mappings) 需要输入，此字段显示输入的类型。

### 3.3 参数

如果 [导出映射](export-mappings) 需要输入，您可以选择正确类型的参数。

### 3.4 内容类型

如果 [导出映射](export-mappings) 基于消息定义，它可以导出XML 和 JSON 。 选择您想要的输出类型。

### 3.5 校验与Schema

{{% alert type="info" %}}

针对架构的验证仅适用于选择导出映射到XML的情况。

{{% /报警 %}}

这决定导出动作是否应该验证输出的 XML 与schema (XSD)对比。

设置为是，可以ipmact 性能！

默认： *否*

### 3.6 可选和可待定

方案中的元素可以是可选的 (`minOccurs=0`)和/或nillable。 当遇到一个元素的空值时， 服务器将检查schema以决定是排除元素 (可选) 还是发送带有nil 属性的元素 (不可以)。 如果遇到一个空值，但该元素不是可选的或不可嵌入的。 服务器会抛出一个例外，您需要在微流程中处理自己。 不管XML 验证设置，这都会发生。 建议确保正在出口的数据根据模式有效。

### 3.7 存储在

您可以选择是否将导出映射活动结果存储在“系统”对象中。 ileDocument'或该实体的专业化或字符串变量。

### 3.8 名称

活动结果的对象或字符串名称。

## 4 通用部分{#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}
