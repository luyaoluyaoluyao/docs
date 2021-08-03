---
title: "提交对象(s)"
parent: "对象活动"
menu_order: 30
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/committing-objects.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

**提交** 活动可以提交一个或多个对象。 对于可持久的实体，这意味着该对象将被存储在数据库中。 承诺不可持续的实体在内存中存储当前属性值和关联值，这允许回滚回到这些值。 另见 [可持久性](persistability)。

## 2 属性

提交对象属性的示例在下面的图像中表示：

![提交对象(s)属性](attachments/object-activities/commit-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

提交对象属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动部分{#action}

属性窗格的动作部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 目标或清单

您想要提交的对象或对象列表。

### 3.2 与活动

{{% alert type="info" %}}
此属性仅用于微流。
{{% /报警 %}}

指示是否执行对象的提交事件处理程序。

默认： *是*

#### 3.2.1 纳诺夫洛夫事件

Nanoflow 没有这个财产。

如果在线应用中使用提交对象动作，它会向Mendix Runtime发送提交请求并总是运行事件。

如果提交对象行动在离线应用中使用，更改将被承诺到离线数据库中。 和事件处理程序在离线应用同步时运行。

### 3.3 刷新客户端{#refresh-in-client}

此设置定义了如何在向最终用户展示的页面中反映变化。

默认： *否*

{{% alert type="info" %}}
为了提高Mendix 应用页面的效率，许多小部件显示的值来自缓存在页面上的对象属性。 使用缓存数据的小部件中的属性 *在客户端更新或删除时始终反映在* 中，而不论客户端 **刷新值** 中。

如果小部件仅在加载 [数据源](data-sources) 时更新， 然后只有在 **在客户端** 中刷新设置为 *是* 时才会看到更改。

测试您的应用时，请确保您选择的小部件显示所需的数据。
{{% /报警 %}}

{{% alert type="warning" %}}
当提交大量对象时，我们建议您不要启用"刷新客户端"，因为它可以减慢速度。
{{% /报警 %}}

#### 3.3.1 在线应用程序中从客户端呼叫微流

如果客户端</strong> 中的 **更新设置为 *no*, 此更改不会反映在客户端中。</p>

如果设置为 *是*, 则对象会在客户端上刷新, 包括重新加载相关的 [数据源](data-sources)。

#### 3.3.2 微流在离线、非或混合应用程序

在从离线、本机或混合应用程序调用的微流程内， 客户端</strong> 选项中的 **刷新被忽略，其功能仿佛设置为 **否**。</p>

For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.

#### 3.3.3 行动处于纳诺夫洛夫状态

在 [nanoflow](nanoflows)内， 客户端更新对象，仿佛 **客户端刷新** 设置为 *是*

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 如何提交工作{#how-commits-work}

当一个对象通过默认的保存按钮、提交活动或网络服务进行时，它总是会触发提交事件。 平台还将评估所有相关对象。 为了保证数据的一致性，平台也可以自动提交相关的对象。

自动提交是指从平台自动提交的, 以保持域模型同步. 如果您的应用程序最终有自动提交的对象，那么您将有一个建模错误。 由于一个协会也是对象的成员，该协会也将存入数据库。 这意味着，如果您在订单内创建一个订单行，而订单线是联盟的父连线。 当您提交订单行时，订单将自动提交。

{{% alert type="warning" %}}
自动提交与明示提交不同！

如果一个回滚因任何原因而触发(例如，如果用户会话因关闭浏览器而终止)， 然后自动提交对象将从数据库中删除。 See [Persistability](/refguide8/persistability) for more information about how Mendix handles persistable objects.
{{% /报警 %}}

如果你最后有自动提交的对象，它总是由于建模错误。 在某个时候，一个协会被设置为一个新的对象，相关对象已经被承诺。 它的所有协会也承诺保持所有数据的一致性。

2. 在执行过程中将发生下列情况：

* 事件：对于 *在事件执行前后明确提交的* 个对象， 如果任何事先回滚事件返回错误，可以抛出异常。
    * 如果在事件中发生异常，所有应用更改都将恢复为默认错误处理
    * 在提交之前所作的更改将被保留
        {{% alert type="warning" %}}Before and after events are not executed for autocommitted objects.{{% /alert %}}
* 数据库：对于明确承诺的对象和自动提交的对象，都有一个输入或更新查询
    * 视对象状态而定。 平台将对状态 **实例化** 的对象进行插入，并对所有其他状态进行更新
* 结果: 一个具有状态实例化的对象将被插入数据库，并且一个具有任何其他状态的对象将被更新

![](attachments/object-activities/18582172.png)
