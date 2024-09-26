---
title: "删除对象(s)"
parent: "对象活动"
menu_order: 50
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/deleting-objects.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

删除对象(s) 可以用来删除一个或多个对象。

## 2 属性

删除对象属性的例子在下面的图像中表示：

![删除对象属性](attachments/object-activities/delete-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

删除对象属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 目标或清单

将要删除的对象或对象列表的名称。 如果您选择一个列表，这个列表中的所有对象都将被删除。

### 3.2 在客户端刷新

此设置定义数据源是否在对象从数据库中删除后重新运行。

默认： *否*

{{% alert type="info" %}}
为了提高Mendix 应用页面的效率，许多小部件显示的值来自缓存在页面上的对象属性。 使用缓存数据的小部件中的属性在客户端中总是 *反映在* 中，即使它们没有被提交，也不论客户端</strong>中的 **刷新值如何。 当某个对象被删除时，它将显示任何属性为 null，但对象仍将被显示 (例如) 列表视图中删除对象的空白项) </p>

如果 **在客户端** 中刷新设置为 *是* ，那么所有小部件都将被更新， 包括仅在加载 [数据源](data-sources) 时更新的数据。

测试您的应用时，请确保您选择的小部件显示所需的数据。
{{% /报警 %}}

#### 3.2.1 微流程是从在线应用客户端呼叫的

如果 **在客户端** 中刷新设置为 *no*, 数据源未重新运行，需要重新加载数据的部件仍将显示对象 (s)。

如果设置为 *是*, 删除会反映在所有客户端, 包括重新加载相关的 [数据源](data-sources)。

#### 3.2.2 微流程被调用在离线、非或混合应用程序

在从离线、本机或混合应用程序调用的微流程内， 客户端</strong> 选项中的 **刷新被忽略，其功能仿佛设置为 **否**。</p>

For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 删除过程中会遇到什么样的问题？

点击删除按钮或触发删除活动将启动删除事件。 此外，当一个对象通过配置的删除行为被删除时，它将在事件之前和事件之后执行所有项目。

* 事件：事件发生之前和之后的全部事件，如果任何事先删除事件返回错误，则可以抛出异常
    * 如果在事件中发生异常，所有应用更改都将恢复为默认错误处理
    * 回滚之前所作的更改将被保留
* 数据库：如果对象有状态 **实例化**，将不需要数据库通信
    * 对于任何其他状态，在数据库中执行删除查询
* 结果：对象将从内存中删除，如果可以从数据库中删除
    * 所有删除关联的行为已被验证，任何关联的对象也已被删除

![](attachments/object-activities/18582171.png)
