---
title: "投射对象"
parent: "对象活动"
menu_order: 10
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/cast-object.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

投射对象活动是在一个 [对象类型决定](object-type-decision) 之后的微流程中使用的，目的是将对象类型从一般对象类型转换为路径的专门对象类型，从对象类型决定中转换为路径。

要阅读更多关于专业化和一般化的信息，请参阅 [实体](entities)。

## 2 属性

投射对象属性的示例显示在下面的图像中：

![投射对象属性](attachments/object-activities/cast-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

投射对象属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 对象名称

这是投影结果的名称。 它可以用于这项活动之后的所有活动。

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 个示例

例如， **个问题** 对象有三个专业。 只有特殊类型 **多选题** 的对象需要对其执行一些特殊操作。 这些将在子微流中完成，子微流的输入类型 **多重选择问题**。 既然类型为 **的对象，问题** 无法传递到子微流程， 对象首先需要投射到对象类型 **多重选择问题**

![微流中的投影示例](attachments/object-activities/cast-example.png)