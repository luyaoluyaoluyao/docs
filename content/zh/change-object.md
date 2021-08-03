---
title: "更改对象"
parent: "对象活动"
menu_order: 20
tags:
  - "studio pro"
---

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

更改对象活动可以用于更改对象的成员。 无论有无承诺，也无论有无事可做。

## 2 属性

更改对象属性的例子在下面的图像中表示：

![更改对象属性](attachments/object-activities/change-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

更改对象属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 对象

**对象** 定义被更改的对象。

### 3.2 承诺

**提交** 定义对象的承诺方式。 请参阅 [部分“提交对象如何工作](committing-objects#how-commits-work) *提交对象”* 以获取更多关于提交的信息。

| 选项         | 描述                                         |
| ---------- | ------------------------------------------ |
| 是的，有事件处理程序 | 对象已保存在数据库中，触发了 [事件处理程序](event-handlers)    |
| 是的，没有事件处理  | 对象已保存在数据库中，但 [事件处理程序](event-handlers) 未被触发 |
| 没有 *(默认)*  | 对象被更改而不被保存到数据库                             |

#### 3.2.1 使用案例设置提交

如果一个流是从数据视图中触发的(例如文本字段的“随时更改”)，您往往不想对数据视图对象进行修改。 最终用户可以按保存或取消按钮来提交或回滚更改。

然而，仍然存在着这种情况。 如果流是从数据网格按钮触发的，只需在选区中执行操作，您将想要提交更改以避免丢失。

#### 3.2.2 Nanoflow

Nanoflow 不支持在没有事件的情况下进行更改。 在运行在线应用程序时承诺，将提交请求发送到Mendix Runtime 并运行事件。 如果在离线应用中使用更改对象动作，更改将被承诺到离线数据库。

### 3.3 刷新客户端{#refresh-in-client}

此设置定义数据源是否在数据被输入数据库后重新运行。

默认： *否*

{{% alert type="info" %}}
为了提高Mendix 应用页面的效率，许多小部件显示的值来自缓存在页面上的对象属性。 使用缓存数据的小部件中的属性在客户端中总是 *反映在* 中，即使它们没有被提交，也不论客户端</strong>中的 **刷新值如何。</p>

如果小部件仅在加载 [数据源](data-sources) 时更新， 然后才会看到更改。 **客户端** 中的刷新设置为 *是*

测试您的应用时，请确保您选择的小部件显示所需的数据。
{{% /报警 %}}

#### 3.3.1 在线应用程序中从客户端呼叫微流

如果客户端</strong> 中的 **更新设置为 *no*, 此更改不会反映在客户端中。</p>

如果设置为 *是*, 则对象会在客户端上刷新, 包括重新加载相关的 [数据源](data-sources)。

#### 3.3.2 微流在离线、非或混合应用程序

在从离线、本机或混合应用程序调用的微流程内， 客户端</strong> 选项中的 **刷新被忽略，其功能仿佛设置为 **否**。</p>

For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.

#### 3.3.3 行动处于纳诺夫洛夫状态

当更改对象在 [nanoflow](nanoflows) 中使用时，客户端</strong> 选项中的 **刷新不可用。 在这种情况下，刷新行为取决于 **提交类型** 选项。 它总是反映客户端中已更改的属性值，包括 [可见性](common-widget-properties#visibility-properties)。</p>

If **Commit type** is set to *Yes*, the object is refreshed across the client as if **Refresh in client** was set to *Yes*.

### 3.4 更替成员

您可以指定要应用于对象的更改列表。 成员的值使用 [表达式](expressions) 指定并且必须与成员的类型相同。

对于参考集社团，也可以添加和删除一个社团(而不是仅设置社团成员)。 对于 **添加**, 对象或对象列表可以添加到当前关联的对象中。 对于 **删除**，可以从当前关联的对象中删除对象或对象列表。

## 4 通用部分{#common}

{{% snippet file="refguide/microflow-common-section-link.md" %}}
