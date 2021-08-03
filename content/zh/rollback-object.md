---
title: "回滚对象"
parent: "对象活动"
menu_order: 70
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/rollback-object.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

回滚对象动作可以用来撤销在活动前的流量中对物体所作的更改(未发生)。 此外，它删除已创建但从未承诺的对象。

{{% alert type="info" %}}
当回滚对象动在子微流中执行时，它会回滚其父微流和子微流中的变化。
{{% /报警 %}}

## 2 属性

下面的图像显示了回滚对象属性的示例：

![回滚对象属性](attachments/object-activities/rollback-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

回滚对象属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 动作{#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 对象

**对象** 定义了需要回滚的对象。

### 3.2 在客户端刷新

此设置定义了如何在向最终用户展示的页面中反映变化。

默认： *否*

{{% alert type="info" %}}
为了提高Mendix 应用页面的效率，许多小部件显示的值来自缓存在页面上的对象属性。 使用缓存数据的小部件中的属性在客户端中总是 *反映在* 中，即使它们没有被提交，也不论客户端</strong>中的 **刷新值如何。</p>

如果小部件仅在加载 [数据源](data-sources) 时更新， 然后只会看到回滚。 **客户端** 中的刷新设置为 *是*

测试您的应用时，请确保您选择的小部件显示所需的数据。
{{% /报警 %}}

#### 3.2.1 在线应用程序中从客户端调用微流

如果客户端</strong> 中的 **刷新设置为 *no*, 回退不会反映在客户端中。</p>

如果设置为 *是*, 则对象会在客户端上刷新, 包括重新加载相关的 [数据源](data-sources)。

#### 3.2.2 微流在离线、非或混合应用程序

在从离线、本机或混合应用程序调用的微流程内， 客户端</strong> 选项中的 **刷新被忽略，其功能仿佛设置为 **否**。</p>

For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.

#### 3.2.3 处于纳诺夫低下的行动

在 [nanoflow](nanoflows)内， 回滚对象动作重新加载 [数据源](data-sources) 似乎客户端 **刷新** 已设置为 *是*

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 回滚怎么办？

按下 **取消** 按钮或触发回滚活动将会启动回滚事件。 这些动作不会因错误而回滚时触发。

* 事件：事件发生之前和之后的全部事件，如果事前回滚事件返回错误，可以抛出异常
    * 如果在事件中发生异常，所有应用更改都将恢复为默认错误处理
    * 回滚之前所作的更改将被保留
* 数据库：此事件期间没有数据库通讯，除非在事前或事后创建事件中指定
* 结果：具有状态 **实例化** 的对象将被删除 和任何其他状态的对象将被还原到它在上次提交时拥有的值

![](attachments/object-activities/18582170.png)
