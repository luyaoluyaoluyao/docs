---
title: "更改列表"
parent: "列表活动"
menu_order: 2
tags:
  - "studio pro"
  - "列表"
---

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。

请注意，这种功能在微流中的工作方式与它在纳米流中的工作方式之间存在着微小的差别。
{{% /报警 %}}

## 1 导言

**更改列表** 活动允许您通过向列表中添加对象和从列表中移除对象来更改列表。 活动直接适用于所提供的列表，这与 [列表操作](list-operation) 活动形成对比。

## 2 属性

下面的图像显示了更改列表属性的示例：

![更改列表属性](attachments/list-activities/change-list-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

更改列表属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 名单

要更改的列表名称。

### 3.2 Type

定义适用于列表的更改类型。

| 选项        | 描述                                                               |
| --------- | ---------------------------------------------------------------- |
| 添加 *(默认)* | 值属性中的对象被添加到列表中。 更多信息请参阅下面的 [笔记](#notes)                          |
| 删除        | 值属性中的对象已从列表中删除。 如果列表中存在重复的对象，那么只有一个将被删除。 如果您要求删除一个不在列表中的对象，没有错误。 |
| 清空        | 列表已清空。                                                           |
| 替换        | 列表已清空，值属性中的对象已添加到列表中。                                            |

#### 3.2.1 使用添加类型{#notes}

如果您不想在您的 (microflow) 列表中重复，您可以先删除对象(s)。 或使用 **包含** [列表操作](list-operation) 在添加对象之前检查列表。

{{% alert type="warning" %}}
目前，这种方法在 **纳米调节** 和 **微流** 中的作用不同。 In a **nanoflow** objects will *not* be added if they are already in the list whereas, in a **microflow**, the same object can be added multiple times.
{{% /报警 %}}

### 3.3 价值

值定义了用于更改列表的对象。 值是使用 [表达式](expressions) 输入的。 该表达式必须产生一个对象或与输入列表相同类型的 [实体](entities) 的对象列表。

## 4 通用部分{#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}
