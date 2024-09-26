---
title: "纳诺夫拉"
parent: "应用逻辑："
menu_order: 20
description: "展示所有可用于纳米的元素的概述。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/nanoflows.pdf)。
{{% /报警 %}}

## 1 导言

Nanoflow 类似于 [microflow](microflows)，因为它们允许您表达您应用程序的逻辑。 然而，它们确实有一些具体的好处（例如，它们直接在浏览器/设备上运行，可用于离线应用）。 此外，大多数操作都直接在设备上， 因此对于不需要访问服务器的逻辑也有速度上的好处。

{{% alert type="info" %}}
此页概述了所有可用于纳米的元素。 对于纳米光本身的属性，请参阅 [Nanoflow Properties](nanoflow)。
{{% /报警 %}}

## 2 何时使用 Nanoflow

### 2.1 离线移动应用

Nanoflow 是用离线第一应用程序设计的，因为它们允许您在离线应用中模拟应用程序逻辑。 由于所有与数据库相关的行动都将在本地离线数据库中执行，离线应用的nanoflow 将很快。

### 2.2 无需连接的逻辑值

Nanoflow也为在线应用程序提供了很大的价值(例如，UI逻辑、验证、计算和导航)。 然而，请记住，当您执行与数据库相关的操作时，每个操作都会创建一个单独的 Mendix Runtime。

以下行动与数据库相互作用：

* 创建
* 提交
* 获取
* Rollback

因此，最佳做法是在不包含上述行动的情况下，在网上应用程序中使用nanofows。

{{% alert type="info" %}}
更改对象而不提交并不是一个与数据库相关的动作，因为更改应用于设备或浏览器。
{{% /报警 %}}

#### 2.2.1 其他案件

尽管在没有使用与数据库相关的行动的情况下，nanoflows在在线应用程序中的表现最佳， 而且这些通常是最好的例子，最多包含一个与数据库有关的行动的纳米调节也仍然可以做得很好。 由于这种纳米技术只需要一个网络电话，它们既能进行微流程，也能进行微流。 这种使用案例的一个例子是对对象执行验证逻辑并将对象承诺于同一纳米。

## 3 与微流量的差异

纳米流量和微流量之间有五个主要差异：

1. 当通过其动作采取nanoflow步骤时，客户端的动作将直接执行。 例如，打开页面操作会立即打开一个页面，而不是在nanoflow的末尾。 这不同于微流程中的客户动作，微流程只有在客户收到微流程结果时才能运行。
2. 当在 nanoflow 活动中使用时，表达式不支持以下对象和变量： `$latestSoapFault`， `$latestHttpResponse`, `$currentSession`, , `$currentUser`, `$currentDeviceType`.
3. Nanoflow 不会在交易中运行，因此如果在nanoflow 中发生错误，它不会回滚以前的任何更改。
4. 纳诺夫低流量和微流量并不提供同样的行动。 微流中的某些活动在纳米粒子中不可用，反之亦然。
5. 因为nanoflow使用JavaScript库和microflow使用Java 库，有时在表达式的执行方式上会有轻微的差异。

## 4 标记 & 类别

nanoflow的图形缩写基于 [业务流程模型和注释](https://en.wikipedia.org/wiki/Business_Process_Model_and_Notation) (BPMN)。 BPMN是在工作流程中绘制业务流程的标准化图形标记。

纳米材料由元素组成。 使用了以下类别：

* [事件](#events) 代表一个循环中的纳米和特殊操作的起始点和终点
* [流动](#flows) 形成元素之间的连接
* [决策](#decisions) 涉及做出选择并再次合并不同的路径
* [活动](#activities) 是指在 nanoflow 中执行的操作
* [循环](loop) 用于在对象列表上迭代。
* [参数](#parameter) 是作为微流程输入的数据。
* [注释](#annotation) 是一个可以用来将注释放入微流程的元素。

### 4.1 事件 {#events}

事件代表一个循环中的纳米和特殊操作的起始点和终点。

| 图形                                                                                 | 名称                     | 描述                                                                              |
| ---------------------------------------------------------------------------------- | ---------------------- | ------------------------------------------------------------------------------- |
| [![开始事件](attachments/microflows-and-nanoflows/start-event.png)](start-event)       | [开始活动](start-event)    | nanoflow的起始点。 nanoflow 只能有一个开始事件。                                               |
| [![结束事件](attachments/microflows-and-nanoflows/end-event.png)](end-event)           | [结束事件](end-event)      | 定义nanoflow 将停止的位置。 根据纳米低的返回类型，在某些情况下必须指定一个值。 可以有多个结束事件。                         |
| ![](attachments/microflows-and-nanoflows/error-event.png)                          | [错误事件](error-event)    | 一个错误事件定义了一个 nanoflow 将停止并抛出一个之前发生的错误的位置。 如果你叫nanoflow，你可能想知道是否在nanoflow中发生任何错误。 |
| [![继续事件](attachments/microflows-and-nanoflows/continue-event.png)](continue-event) | [继续事件](continue-event) | 用于停止循环的当前迭代并继续下次迭代。 继续事件只能在 [循环](loop) 中使用。                                     |
| [![休息事件](attachments/microflows-and-nanoflows/break-event.png)](break-event)       | [中断事件](break-event)    | 用于停止对对象列表的迭代并继续循环后的其余流程。 断开事件只能在 [循环](loop) 中使用。                                |

### 4.2 资金流动 {#flows}

流程形成元素之间的连接。

| 图形                                                                                          | 名称                                 | 描述                                         |
| ------------------------------------------------------------------------------------------- | ---------------------------------- | ------------------------------------------ |
| [![](attachments/microflows-and-nanoflows/sequence-flow.png)](sequence-flow)                | [序列流](sequence-flow)               | 一个将事件、活动、决定和合并彼此联系起来的箭头。 它们共同确定了在纳米内的执行顺序。 |
| [![](attachments/microflows-and-nanoflows/annotation-flow.png)](annotation#annotation-flow) | [批注流程](annotation#annotation-flow) | 可用来将注解连接到另一个元素的连接。                         |

### 4.3 决定 {#decisions}

决策涉及作出选择和合并不同的道路。

| 图形                                                               | 名称         | 描述                                                          |
| ---------------------------------------------------------------- | ---------- | ----------------------------------------------------------- |
| [![决 定](attachments/microflows-and-nanoflows/decision.png)](决 定) | [决 定](决 定) | 根据一种条件做出决定，并遵循一种而且只是一种外流流量。 **注意**: nanoflows没有并行执行.        |
| [![合并](attachments/microflows-and-nanoflows/merge.png)](合并)      | [合并](合并)   | 可以用来将多个序列流合并为一个。 如果是以纳米材料做出选择，然后需要做一些共同的工作。 您可以合并两个(或更多)路径。 |

### 4.4 活动{#activities}

[活动](activities) 是在 nanoflow 中执行的动作：

![活动](attachments/microflows-and-nanoflows/activity.png)

### 4.5 循环 {#loop}

[循环](loop) 用于在对象列表上迭代：

![循环](attachments/microflows-and-nanoflows/loop.png)

对于每个对象，循环内的流程都会被执行。 循环活动可以包含所有在 nanoflow中使用的元素，但启动和结束事件除外。

### 4.6 参数 {#parameter}

一个 [参数](parameter) 是用于为 nanoflow 输入的数据。

![参数](attachments/microflows-and-nanoflows/parameter.png)

参数填写在触发纳米波的地点。

### 4.7 说明 {#annotation}

[注释](annotation) 是一个可以用来在微流程中发表评论的元素：

![批注](attachments/microflows-and-nanoflows/annotation.png)

### 4.8 项目使用

Studio Pro 可视化了选定元素使用哪些项目。 通过在蓝色背景上显示白色文本中使用过的物品来做到这一点。 反之，使用选定元素返回的物品的元素在绿色背景上用白色文本中的“使用”标记。

在下面的示例中，参数 **账户密码数据** 被高亮，因为它被用于选定的活动(**检索账户**)。 活动 **保存密码** 有一个 **用法** 标签，因为它使用的对象是 **检索帐户**。

![](attachments/microflows-and-nanoflows/microflow-nanoflow-example.png)

## 5 个键盘支持

nanoflow 编辑器提供键盘支持导航和操纵nanoflow。 下表显示可以使用的密钥。

| Key(s)                                    | 效果                         |
| ----------------------------------------- | -------------------------- |
| 箭头键                                       | 向箭头方向选择附近的元素(活动、事件、循环或参数)。 |
| <kbd>输入</kbd>                             | 编辑选中元素的属性。                 |
| <kbd>F2</kbd>                             | 重命名选中元素返回的物品。              |
| <kbd>Shift</kbd> + <kbd>F2</kbd> 或只是开始输入  | 编辑选中元素的标题。                 |
| <kbd>Ctrl</kbd> + 箭头键                     | 向箭头方向移动选中的元素。              |
| <kbd>Tab</kbd>                            | 如果选择循环，循环中的第一个元素将被选中。      |
| <kbd>Shift</kbd> + <kbd>Tab</kbd>         | 如果选择循环中的元素，循环本身将被选中。       |
| <kbd>首页</kbd>                             | 选择开始事件。                    |
| <kbd>结束</kbd>                             | 循环到结束事件。                   |
| 上下文菜单键或 <kbd>Shift</kbd> + <kbd>F10</kbd> | 打开当前选中元素的上下文菜单。            |

## 6 Nanoflow 调试

尚不支持逐步调试. 现在，我们建议使用日志消息活动，它会显示在Studio Pro的控制台日志中。

## 7 个安全

Nanoflow 是在当前用户的情况下执行的。 用户未经授权的任何操作都将失败。 例如，当天体在nanoflow 中被检索时，只返回当前用户已读取的对象。 只有当当前用户有对所有更改的写权限时，才能提交对象。