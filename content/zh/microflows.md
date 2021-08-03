---
title: "微型流动"
parent: "应用逻辑："
menu_order: 10
description: "显示可用于微流的所有元素的概述。"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/microflows.pdf)。
{{% /报警 %}}

## 1 导言

Microflow允许您表达应用程序的逻辑。 微流可以执行创建和更新对象、显示页面和选择等操作。 这是一种直观的表达传统的文本程序代码的方式。

Microflow在运行时服务器中运行，因此无法用于离线应用。 关于离线应用中的应用逻辑，请参阅 [Nanoflows](nanoflows)。

本页概述了构成微观流的要素以及它们在微观流中的视觉表现。 它还包括编辑微流时的 [键盘支持](#keyboard)。

{{% alert type="info" %}}
对于微流程本身的属性，请参阅 [微流程属性](microflow)。
{{% /报警 %}}

## 2 微流标记

微流的图形缩写基于 [业务流程模型和符号](https://en.wikipedia.org/wiki/Business_Process_Model_and_Notation) (BPMN)。 BPMN是在工作流程中绘制业务流程的标准化图形标记。

微流由元素组成。 下面是所有要素的分类概述。 使用了以下类别：

*   [事件](#events) 代表了一个循环中微流和特殊操作的起始点和终点。
*   [流动](#flows) 形成元素之间的连接。
*   [决策](#decisions) 涉及做出选择并重新合并不同的路径。
*   [活动](#activities) 是在微流程中执行的动作。
*   [循环](loop) 用于在对象列表上迭代。
*   [参数](#parameter) 是作为微流程输入的数据。
*   [注释](#annotation) 是一个可以用来将注释放入微流程的元素。

### 2.1 事件{#events}

事件代表微流和特殊操作在循环中的起始点和终点。

| 图形                                                                             | 名称                     | 描述                                                     |
| ------------------------------------------------------------------------------ | ---------------------- | ------------------------------------------------------ |
| [![](attachments/microflows-and-nanoflows/start-event.png)](start-event)       | [开始事件](start-event)    | 开始活动是微流的起点。 微流只能有一个起始事件。                               |
| [![](attachments/microflows-and-nanoflows/end-event.png)](end-event)           | [结束事件](end-event)      | 终端事件定义了微流将停止的位置。 根据微流的返回类型，在某些情况下必须指定一个值。 可以有多个结束事件。   |
| [![](attachments/microflows-and-nanoflows/error-event.png)](error-event)       | [错误事件](error-event)    | 一个错误事件定义了微流停止并抛出之前发生的错误的位置。 如果您调用微流，您可能想知道微流中是否发生任何错误。 |
| [![](attachments/microflows-and-nanoflows/continue-event.png)](continue-event) | [继续事件](continue-event) | 持续事件用于停止当前循环的迭代并继续下一次迭代。 继续事件只能在 [循环](loop) 中使用。       |
| [![](attachments/microflows-and-nanoflows/break-event.png)](break-event)       | [中断事件](break-event)    | 休息活动用于停止对对象列表的迭代，继续循环后的其余流程。 中断事件只能在 [循环](loop) 中使用。   |

### 2.2 流动{#flows}

流程形成元素之间的连接。

| 图形                                                                                          | 名称                                 | 描述                                         |
| ------------------------------------------------------------------------------------------- | ---------------------------------- | ------------------------------------------ |
| [![](attachments/microflows-and-nanoflows/sequence-flow.png)](sequence-flow)                | [序列流](sequence-flow)               | 序列流程是指将事件、活动、决策和合并相互连接的箭头。 它们共同决定微流中的执行顺序。 |
| [![](attachments/microflows-and-nanoflows/annotation-flow.png)](annotation#annotation-flow) | [批注流程](annotation#annotation-flow) | 关联是可用来将注解连接到另一个元素的连接。                      |

### 2.3 决 定 {#decisions}

决策涉及作出选择和再次合并不同的道路。

| 图形                                                                                         | 名称                             | 描述                                                                              |
| ------------------------------------------------------------------------------------------ | ------------------------------ | ------------------------------------------------------------------------------- |
| [![](attachments/microflows-and-nanoflows/decision.png)](决 定)                              | [决 定](决 定)                     | 一项决定是根据一项条件作出的，并且只遵循一项外流量中的一项。 微流中没有并行的施行。                                      |
| [![](attachments/microflows-and-nanoflows/object-type-decision.png)](object-type-decision) | [对象类型决定](object-type-decision) | 对象类型决定是一个基于所选对象的 [专业](entities) 做出选择的元素。 您可以使用 [投射对象](cast-object) 动作给专门对象一个名字。 |
| [![](attachments/microflows-and-nanoflows/merge.png)](合并)                                  | [合并](合并)                       | 合并可以用来将多个序列流合并为一个。 如果在微流中作出选择，然后需要做一些共同的工作。 您可以合并两个(或更多)路径。                     |

### 2.4 活动{#activities}

[活动](activities) 是指在微流中执行的动作：

![活动](attachments/microflows-and-nanoflows/activity.png)

### 2.5 循环 {#loop}

[循环](loop) 用于在对象列表上迭代：

![循环](attachments/microflows-and-nanoflows/loop.png)

对于每个对象，循环内的流程都会被执行。 循环活动可以包含微流中使用的所有元素，但开始和结束活动除外。

### 2.6 参数 {#parameter}

一个 [参数](parameter) 是作为微流程输入的数据。

![参数](attachments/microflows-and-nanoflows/parameter.png)

参数填写在触发微流的地点。

### 2.7 说明 {#annotation}

[注释](annotation) 是一个可以用来在微流程中发表评论的元素：

![批注](attachments/microflows-and-nanoflows/annotation.png)

### 2.6 物品使用情况

Studio Pro 可视化了选定元素使用哪些项目。 通过在蓝色背景上显示白色文本中使用过的物品来做到这一点。 反之，使用选定元素返回的物品的元素在绿色背景上用白色文本中的“使用”标记。

在下面的示例中，参数 **账户密码数据** 被高亮，因为它被用于选定的活动(**检索账户**)。 活动 **保存密码** 有一个 **用法** 标签，因为它使用的对象是 **检索帐户**。

![](attachments/microflows-and-nanoflows/microflow-nanoflow-example.png)

## 3 个键盘支持{#keyboard}

微流程编辑器提供键盘支持导航和操作微流。 下表显示可以使用的密钥。

| 关键字                                       | 效果                         |
| ----------------------------------------- | -------------------------- |
| 箭头键                                       | 在箭头方向选择附近的元素(活动、事件、循环或参数)。 |
| <kbd>输入</kbd>                             | 编辑选中元素的属性。                 |
| <kbd>F2</kbd>                             | 重命名选中元素返回的项目。              |
| <kbd>Shift</kbd> + <kbd>F2</kbd> 或只是开始输入  | 编辑选中元素的标题。                 |
| <kbd>Ctrl</kbd> + 箭头键                     | 向箭头方向移动选中的元素。              |
| <kbd>Tab</kbd>                            | 如果选择循环，循环中的第一个元素将被选中。      |
| <kbd>Shift</kbd> + <kbd>Tab</kbd>         | 如果选择循环中的元素，循环本身将被选中。       |
| <kbd>首页</kbd>                             | 选择开始事件。                    |
| <kbd>结束</kbd>                             | 循环到结束事件。                   |
| 上下文菜单键或 <kbd>Shift</kbd> + <kbd>F10</kbd> | 打开当前选中元素的上下文菜单。            |

## 4 微流程调试

如果您想要看到微流执行时发生什么，您可以使用微流调试器。 看看下面的办法：

*   [调试微流](/howto8/monitoring-troubleshooting/debug-microflows)
*   [远程调试微流](/howto8/monitoring-troubleshooting/debug-microflows-remotely)
