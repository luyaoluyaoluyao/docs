---
title: "事件处理"
parent: "实体"
menu_order: 50
tags:
  - "域模型"
  - "实体"
  - "事件处理程序"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/event-handlers.pdf)。
{{% /报警 %}}

## 1 导言

事件处理程序定义了处理与实体相关事件的微流。 根据选择的时间和类型，微流在创建、提交、删除或回滚对象之前或之后执行。

事件处理程序应适度使用，因为每次事件发生时都会触发事件， 所以他们必须是为了你想要永远发生的事情。 如果你只想在某个页面发生某件事情， 您可以在那里使用微流程(例如，在自定义的 **上保存** 按钮)。

{{% alert type="warning" %}}
事件处理程序不会在特定的顺序中触发。 因此，确保事件不以任何方式相互关联(也不涉及一般事件和专业事件)。

当事件从微流触发时，您可以选择绕过微流动作中的事件处理程序。
{{% /报警 %}}

{{% alert type="info" %}}
如果特定事件被应用于对象列表 (if, 您正在提交对象列表), 处理程序将首先触发所有对象，然后事件将应用到列表中。 在给定的例子中，处理程序将先运行在所有对象上，然后将执行列表中的所有对象。

如果您的处理程序依赖于已经应用于列表中的另一个对象的事件。 您应该从列表中循环，然后依次对每个对象应用事件。
{{% /报警 %}}

例如，说您的 **客户** 实体有 **邮政编码** 属性，您想要检查这是否始终有效。 If there are multiple places where this can be changed, you can add a *Before Commit* event which calls a microflow **BCo_Customer_Postcode** which checks that the postcode is valid every time a Customer object is committed and prevents the object being committed if the postcode is invalid.

![向客户实体提交事件处理前添加一个实例](attachments/domain-model/customer-event-handlers.png)

关于使用事件处理程序进行数据验证的更多信息，请参阅 [如何设置数据验证](/howto8/data-models/setting-up-data-validation)。

## 2 属性

您可以从 [实体对话框](entities#dialog-box) 添加和编辑实体的事件处理程序。

事件处理属性的示例在下面的图像中表示：

![](attachments/domain-model/event-handler-properties.png)

事件处理属性由以下部分组成：

* [时间](#when)
* [什么](#what)

### 2.1 节时 {#when}

#### 2.1.1 时间 {#moment}

**Moment** specifies whether the microflow is executed **Before** or **After** the specified event occurs.

#### 2.1.2 事件{#event}

**事件** 指定了触发执行微流程的事件。

| 值        | 描述                                                                                                                                  |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 创建       | 当创建此实体的对象时，将执行微流。 当用户点击 **在网格上创建** 或者当对象创建在微流程时就会发生这种情况。 在 [在微流程中创建](create-object) 动作， 在创建操作后，以属性的默认值初始化对象后执行 但在操作中指定的任何更改项目被应用之前。 |
| 提交       | 当该实体的对象被承诺时，将执行微流。 当用户在页面上点击 **保存** 或当对象在微流程中被提交时就会发生这种情况。                                                                          |
| 删除       | 当此实体的对象被删除时，将执行微流。 当用户在网格中点击 **删除** 或者当一个对象在微流程中被删除时就会发生这种情况。                                                                       |
| Rollback | 当此实体的对象回滚时执行微流。 当用户在页面上点击 **取消** 或当对象在微流程中回滚时发生这种情况。                                                                                |

### 2.2 什么部分{#what}

#### 2.2.1 通过事件对象

此选项指定此事件的微流程(见下面 **微流程** )是否将与事件相关联的对象作为参数。 例如，如果您想要在您的事件处理器中对正在提交的对象进行一些验证检查，这是有用的。

如果您将其设置为 **没有**，您只能指定一个没有参数的微流。

#### 2.2.2 微流

此属性定义了为指定事件执行的微流。 微流必须有与事件处理器的时间和事件一致的参数和返回类型：

* 除了 **以外，所有事件处理器的微流都可以在创建** 之前获得事件发生的对象作为参数。
* 在</em> 事件之前执行了 _的微流应该返回一个布尔值，指定事件应该继续(true)还是被取消(false)。 当多个微流处理同一事件时，当一个微流返回假时，它将立即被取消。 在这种情况下，可能根本不会进行一些微流。 您可以使用此功能，例如当某个条件未满足时取消对对象的承诺。</li> </ul>

| [瞬时](#moment) | [事件](#event) | 可以获取对象作为参数 | 返回布尔值 |
| ------------- | ------------ | ---------- | ----- |
| 前             | 创建           | 否          | 否     |
| 之后            | 创建           | 否          | 否     |
| 前             | 提交           | 否          | 否     |
| 之后            | 提交           | 否          | 否     |
| 前             | 删除           | 否          | 否     |
| 之后            | 删除           | 否          | 否     |
| 前             | Rollback     | 否          | 否     |
| 之后            | Rollback     | 否          | 否     |

#### 2.2.3 微流返回错误时出错

This is only relevant if the [Moment](#moment) is set as **Before**.

如果启用此选项，当microflow 返回 false时，事件处理程序会引起一个错误。 然后您可以使用错误处理来检测事件处理程序是否返回了false。

例如，这可以在提交</strong> 事件处理之前以与本机验证相同的方式使用 **。 如果此选项设置为 **没有**， a 在提交之前，事件处理程序可以停止提交，但其余微流仍将执行。</p>

默认： *是*

## 3 阅读更多

* [如何去除数据以提高性能](/howto8/data-models/denormalize-data-to-improve-performance)
* [如何设置数据验证](/howto8/data-models/setting-up-data-validation)
