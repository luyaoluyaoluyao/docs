---
title: "创建对象"
parent: "对象活动"
menu_order: 40
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/create-object.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动可以同时用于 **微流** and **Nanoflows**。
{{% /报警 %}}

## 1 导言

创建对象活动可以用于创建对象。

## 2 属性

创建对象属性的实例在下面的图像中表示：

![创建对象属性](attachments/object-activities/create-properties.png)

该活动有两组属性。 那些在左边的对话框中的人，以及那些在属性中在右边的人。

创建对象属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 实体

您想要创建对象的实体。

### 3.2 承诺

**提交** 定义对象的承诺方式。 请参阅 [部分“提交对象如何工作](committing-objects#how-commits-work) *提交对象”* 以获取更多关于提交的信息。

| 选项         | 描述                                       |
| ---------- | ---------------------------------------- |
| 是的，有事件处理程序 | 对象已保存在数据库中，触发了 [事件处理程序](event-handlers)。 |
| 是的，没有事件处理  | 对象已保存到数据库，但未触发 [事件处理程序](event-handlers)。 |
| 没有 *(默认)*  | 此对象被更改，没有保存到数据库中。                        |

#### 3.2.1 Nanoflow

Nanoflow 不支持在没有事件的情况下进行更改。 在运行在线应用程序时承诺，将提交请求发送到Mendix Runtime 并运行事件。 如果在离线应用中使用更改对象动作，更改将被承诺到离线数据库。

### 3.3 客户端刷新

此设置定义了如何在向最终用户展示的页面中反映变化。

默认： *否*

#### 3.3.1 在线应用程序中从客户端调用微流

如果客户端</strong> 中的 **更新设置为 *no*, 此更改不会反映在客户端的任何小部件中。</p>

如果 **提交** and **刷新客户端** 都设置为 *是* [数据源](data-sources) 已重新加载，新对象的值显示在相关的部件中。

#### 3.3.2 微流在离线、非或混合应用程序

在从离线、本机或混合应用程序调用的微流程内， 客户端</strong> 选项中的 **刷新被忽略，其功能仿佛设置为 **否**。</p>

For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.

#### 3.3.4 处于纳诺夫低下的行动

在 nanoflow, 创建对象动作会重新加载 [数据源](data-sources) , 仿佛客户端刷新设置为 *是*.

### 3.4 更替成员

您可以设置新创建的对象的成员 (属性和关联) 的值与 [entity](entities) 的默认值不同。 成员的值使用 [表达式](expressions) 指定并且必须与成员的类型相同。

### 3.5 对象名称

这是所有跟随此活动的活动可以使用的结果对象的名称。

## 4 通用部分{#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}

## 5 在创建过程中什么样的帽子？

任何对象初始化的地方，所有事件总是被执行的。 默认 **创建** 按钮，微流程中的创建活动，以及网络服务将始终遵循下面图像描述的步骤。

* 事件：事件发生之前和之后的全部事件，如果任何事先创建事件返回错误，可以抛出异常
    * 如果在事件中发生异常，所有更改都会以默认错误处理行为还原。
* 数据库：此事件期间没有数据库通讯，除非在事前或事后创建事件中指定
* 结果：在这些触发器后有一个新对象
    * 对象将有 **实例化** 状态
    * 这影响到其他对象动作中的行为

![](attachments/object-activities/18582173.png)
