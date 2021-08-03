---
title: "微型流动"
description: "描述Mendix Studio中的微流。"
menu_order: 50
tags:
  - "工作室"
  - "微流"
---

## 1 导言

Mendix Studio 有许多内置逻辑可以用在方框之外(例如按钮)。 但如果你想添加自定义逻辑，你需要创建微流。

*Microflow* 是表达文本程序代码的一种视觉方式。  微流可以执行诸如创建和更改对象、显示页面和作出选择等操作。

您需要为以下情况使用微流：

*  要更改/扩展按钮的标准行为
* 添加自定义逻辑到您的应用程序
* 与其他系统、数据库、网络服务等集成。

使用微流的例子如下：

*  您检查最终用户输入的值，您要么向最终用户显示错误消息，要么显示其他页面
*  您正在创建待办事宜列表，并且您想在列表中某个项目的状态发生变化时使用自定义逻辑。

若要在工作室查看您的应用的微流，请点击左侧菜单栏中的 **微流** 图标：

{{% image_container width="250" %}}![微流程图标](attachments/microflows/micflows-icon.png)
{{% /image_container %}}

## 2 概念和定义

微流程看起来像一个流程图。 在新的微流中，默认情况下创建了 *起始事件* (一个由 *绿色* 点表示的微流的起始点) 和 *终结事件* (一个由 *红色* 点表示的微流的终结点)。

开始和结束事件由 *序列流程* (与箭头的直线)，您可以在那里添加新的事件和活动。 欲了解更多信息，请参阅 [创建新的 Microflow](#creating-new-microflow) 部分。 如果 [Mendix Assists](mx-assist) 已开启。 它将在中间显示一个蓝色点(更多关于Mendix Assist是什么的信息)。 见 [Mendix Assistment](mx-assist)。

![新建微流](attachments/microflows/new-microflow-created.png)

在您开始配置微流之前，您熟悉微流编辑器使用的概念和概念：

| 概念 | 描述                                                                                                                                                                                               |
| -- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 活动 | 活动执行不同的功能，显示为蓝箱。 例如，在某项活动的帮助下，您可以向最终用户展示一个主页。 关于活动的更多信息，请参阅第 [工具箱](#microflows-toolbox) 部分。                                                                                                      |
| 流动 | 流量显示为连接微流事件和活动的箭头。 欲了解更多关于流量的信息，请参阅 [流动](#flows) 部分。                                                                                                                                             |
| 事件 | 事件是一个流程中的所有其他元素，不是活动物(而不是蓝箱)。 [Decision](microflows-decision) 是一个事件的例子。 欲了解更多事件信息，请参阅 [常规](#microflow-general-section) 部分。                                                                       |
| 变量 | 变量是数据的临时存储。 变量用于存储信息并在需要时参考它。 为此目的，变量应有一个唯一的名称。 <br />在微流中，您可以添加一个变量，分配一个值，然后在微流活动或事件中使用它。 如有必要，您可以稍后更改此值。 例如，您可以创建变量 **$Discount** 并分配一个值 0.5，并使用它来计算客户的价格。 <br />您只能在创建的微流程中使用该变量。 |
| 参数 | 参数包含全局变量，这意味着您可以在不同的微流中使用相同的参数。                                                                                                                                                                  |

## 3 创建新的微流 {#creating-new-microflow}

要创建一个新的微流并开始构建自定义逻辑，请执行以下操作：

1. 点击左侧菜单栏中的 **微流程** 图标。
2.  在 **微流** 侧面板上点击 **新**。

    {{% image_container width="300" %}}![添加新的微流](attachments/microflows/new-microflow.png)
    {{% /image_container %}}

3.  在弹出式对话框中填写微流名称并点击 **创建**。

    ![创建新的微流程对话框](attachments/microflows/new-microflow-dialog.png)

新的微流程已创建，您现在可以使用事件和活动添加逻辑。

## 4 复制微流 {#duplicate}

若要复制微流，请执行以下操作：

1. 点击左侧菜单栏中的 **微流** 图标。

2.  在侧面板中，单击椭圆图标并在下拉菜单中选择 **重复**

    {{% image_container width="350" %}}![Duplication a Microflow](attachments/microflows/duplicate-microflow.png){{% /image_container %}}

微流是重复的。

## 5 复制并粘贴微流

若要复制和粘贴微流，请做以下操作：

1. 点击左侧菜单栏中的 **微流** 图标。

2.  在侧面板中，单击椭圆图标并在下拉菜单中选择 **复制到剪贴板**：

    {{% image_container width="350" %}}
![复制微流](attachments/microflows/copy-microflow.png)
{{% /image_container %}}

3. 打开工作室应用程序以粘贴微流程并按 <kbd>Ctrl</kbd> +<kbd>V</kbd> 或 <kbd>Cmd</kbd> +<kbd>V</kbd>。

您的微流程已粘贴。 欲了解工作室中复制/粘贴函数的更多信息，请在 *常规信息* 中查看 [复制/粘贴页面、微流和枚举](general#copy-paste-documents) 部分。

## 6 正在删除微流

若要删除工作室中的微流，请执行以下操作之一：

1. 打开您想要删除的微流程并遵循以下步骤：

    1. 打开 **属性** 选项卡。

    2. 点击 **在 **属性底部删除**** 标签。

2. 点击左侧菜单栏中的 **微流** 图标并执行以下操作：

    1. 在侧面板中，单击椭圆图标并在下拉菜单中选择 **删除**

        {{% image_container width="350" %}}
![删除微流](attachments/microflows/delete-microflow.png)
{{% /image_container %}}

## 7 添加新事件或活动 {#adding-activity-to-microflow}

若要在微流中添加新的活动或事件，请执行以下操作：

1. 打开您想要添加事件或活动的微流程。
2. 打开 **工具箱** 标签页。
3. 在 **常规**中选择事件或活动。 **对象活动** 或 **客户端活动** 部分。
4. 拖放微流中的事件或活动。

## 8 工具箱 {#microflows-toolbox}

**工具箱** 标签包含以下部分：

* [A. 概况](#microflow-general-section)
* [对象活动](#microflow-object-activities)
* [客户活动](#microflow-client-activities)

### 8.1 概况 {#microflow-general-section}

**常规** 部分包含各种元素，例如参数和结束事件：

{{% image_container width="300" %}}![微流程常规属性](attachments/microflows/microflows-general-properties.png)
{{% /image_container %}}

Elements available in the **General** section are described in the table below.

| 元素                         | 描述                                                                                                                                                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 批注                         | 注解是一个可以用来将注释放入微流程的元素。                                                                                                                                                                                        |
| 中断事件                       | 休息活动只用于循环中停止在对象列表上的迭代，然后继续微流中的其余流量。 欲了解关于中断事件的更多信息，请参阅 *Studio Pro Guide* 中的 [中断事件](/refguide8/break-event)。                                                                                                 |
| 继续事件                       | 继续事件仅用于停止当前的迭代和开始下一个对象的迭代。 For more information on the continue event, see [Continue Event](/refguide8/continue-event) in the *Studio Pro Guide*.                                                            |
| 结束事件                       | 终端事件定义了微流将停止的位置。 可能会有多个结束事件，如在微流程中使用 [Decision](microflows-decision) 时。 因此，结束活动的次数取决于微观流动可能产生的结果的数目。 For more information on the end event, see [End Event](/refguide8/end-event) in the *Studio Pro Guide*. |
| [决 定](microflows-decision) | 决定分割流，如果你想要添加条件，应该使用它。 例如，如果您想为不同级别的客户显示不同的订单表格。 <br />此元素基于一个条件，并将导致几次流出流量，每次可能的结果都是如此。 微流控制条件并跟随其中一种流量。 欲了解决策及其属性的更多信息，请参阅 [Decision](microflows-decision)。                                          |
| [循环](microflows-loop)      | 循环用于在对象列表上进行迭代并对列表中的每个项目进行操作。 例如，您可以从数据库检索订单清单，然后循环到这个列表并标记已处理的订单。 关于循环及其属性的更多信息，请参阅 [循环](microflows-loop)。                                                                                                  |
| 合并                         | 合并可以用来将流量合并成一个流量。  如果您先前拆分微流流流(例如) 对于这些分开的流量，需要执行一项和相同的行动， 您可以合并两个(或更多)路径。 欲了解更多信息，请见 [合并](/refguide8/merge) 在 *Studio Pro 指南* 中。                                                                            |
| 参数                         | 参数是微流的输入数据，可以用于微流中的任何活动。 欲了解更多关于参数的信息，请参阅 *Studio Pro Guide* 中的 [参数](/refguide8/parameter)。                                                                                                                  |

### 8.2 对象活动 {#microflow-object-activities}

**对象活动** 部分包含与对象或对象交互的活动(关于对象是什么的更多信息)。 查看 [域模型](domain-models)：

{{% image_container width="350" %}}![微流程对象活动](attachments/microflows/object-activities.png)
{{% /image_container %}}



下面的表格描述了 **对象活动**。

| 活动   | 描述                                                                                                                                                       |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 聚合列表 | **合计清单** 可以用于计算合计值，例如最大值， 数据对象列表上的最小、总和平均数和天体总数。 For more information, see [Aggregate List](/refguide8/aggregate-list) in the *Studio Pro Guide*.        |
| 更改对象 | **更改对象** 可以用于更改此对象的现有数据对象或属性。 For more information, see [Change Object](/refguide8/change-object) in the *Studio Pro Guide*.                             |
| 提交   | **提交** 保存您尚未保存到数据库中的更改。 欲了解更多信息，请访问 [在 *Studio Pro 指南* 中提交](/refguide8/committing-objects)。                                                              |
| 创建对象 | **创建对象** 可以用于创建数据对象。 欲了解更多信息，请见 [在 *Studio Pro 指南* 中创建对象](/refguide8/create-object)。                                                                     |
| 删除   | **删除对象** 可以用于删除一个数据对象或对象列表。 For more information, see [Delete](/refguide8/deleting-objects) in the *Studio Pro Guide*.                                   |
| 获取   | **检索** 可以用来获取一个或多个物体。 通过通过 [关联](domain-models-association-properties)获取另一个对象，或通过从数据库检索对象来获取对象。 欲了解更多信息，请访问 [在 *Studio Pro 指南* 中获取](/refguide8/retrieve)。 |

### 8.3 客户活动科 {#microflow-client-activities}

**客户端活动** 在客户端中执行活动，例如打开一个页面或显示一条消息：

![微流程客户端活动](attachments/microflows/client-activities.png)

下面的表格描述了 **客户活动**。

| 活动   | 描述                                                                                                                                                             |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 关闭页面 | **关闭页面** 活动关闭当前打开的页面。 欲了解更多信息，见 [关闭页面](/refguide8/close-page) 在 *Studio Pro 指南* 中。                                                                             |
| 显示主页 | **显示主页** 动作导航到主页。 它与最终用户在签署并尊重以角色为基础的主页后走到同一页。 欲了解更多信息，见 [在 *Studio Pro 指南* 中显示主页](/refguide8/show-home-page)。 <br />关于设置主页的详细信息，请参阅 [导航文档](navigation)。 |
| 显示消息 | 使用 **显示消息** 动作，您可以向最终用户显示屏蔽或非屏蔽消息。 (无屏蔽消息允许用户在弹出窗口打开时继续在应用中工作。) 当屏蔽消息不允许用户继续工作，直到弹出窗口关闭。 欲了解更多信息，请见 [在 *Studio Pro 指南* 中显示信件](/refguide8/show-message)。        |
| 显示页面 | 使用 **显示页面** 您可以向最终用户显示一个页面。 欲了解更多信息，见 [在 *Studio Pro 指南* 中显示页面](/refguide8/show-page)。                                                                         |

### 8.4 可变活动

**变量活动** 部分包含操作变量的活动：

![微流程变量活动](attachments/microflows/variable-activities.png)

下表介绍了 **种可变活动**：

| 活动   | 描述                                                                                                                            |
| ---- | ----------------------------------------------------------------------------------------------------------------------------- |
| 更改变量 | **更改变量** 更改当前微流中现有变量的值。 欲了解更多信息，请见 [在 *Studio Pro 指南* 中更改变量](/refguide8/change-variable)。                                     |
| 创建变量 | 使用 **创建变量** 活动，您可以创建一个变量并赋予它一个值。 该变量可以用于存储、改变和在微流活动中重新使用一个值。 欲了解更多信息，见 [在 *Studio Pro 指南* 中创建变量](/refguide8/create-variable)。 |

例如，您可以先创建一个变量，名为 *折扣* 到微流程， 然后根据客户级别的类型更改变量折扣。 您可以给客户以金银级折扣。

{{% image_container width="400" %}}![示例微流](attachments/microflows/example-of-using-var-activities.png)
{{% /image_container %}}

## 9 流 {#flows}

流量是连接元素的直线。 您可以在下表中找到流量描述：

| 流   | 图片                                                 | 描述                                                                                                                      |
| --- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 序列流 | ![序列流](attachments/microflows/sequence-flow.png)   | 序列流程是指将事件、活动、决策和合并相互连接的箭头。 因此，它确定了执行的顺序。 流量总是向一个方向流动，元素被逐个执行。 这意味着微型流动不能同时进行两次流动。 即使您有 **决定** 将一个流分割成几个流，微流也只会跟随其中一个流量。 |
| 注释流 | ![注释流](attachments/microflows/annotation-flow.png) | 注流是一种连接，可用来将注解链接到流元素(s)。                                                                                                |

## 10 个活动图标

配置微流活动时，您会注意到上面或下面活动的图标。 您可以在下表中找到图标描述：

| 名称      | 图像示例                                                              | 描述                                                                                                                       |
| ------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 实体      | ![实体图标](attachments/microflows/entity-icon.png)                   | 表示活动的数据来源是一个实体。                                                                                                          |
| 值       | ![值图标](attachments/microflows/simple-value-icon.png)              | 表示该活动的数据源是一个简单的值，例如小数点数、小数点数、小数点数、日期和时间。                                                                                 |
| 提交      | ![提交图标](attachments/microflows/commit-icon.png)                   | 表示对象将被提交。 *提交* 意味着更改将保存在数据库中。 例如，当你想要一个对象 *新客户* 被保存并更新到数据库时，这可能是有用的。                                                     |
| 无事件提交   | ![无事件提交图标](attachments/microflows/commit-with-no-events-icon.png) | 表示对象将被投入，但没有事件。 这意味着对象将被保存到数据库中，但事件处理程序将不会被触发。 欲了解更多关于事件处理器的信息，请在 *Studio Pro 指南* 中查看 [事件处理器](/refguide8/event-handlers) |
| 在客户端中刷新 | ![在客户端图标中刷新](attachments/microflows/refresh-in-client-icon.png)   | 表示活动的结果将显示给最终用户。                                                                                                         |

## 此类别中的主要文件

* [Mendix Assists](mx-assist) -- 描述一种帮助您配置微流的人工智能驱动代理
* [Decision](microflows-decision) - 解释决定是什么并描述其属性
* [循环](microflows-loop) - 解释一个循环是什么，并描述它的属性
* [微流程表达式](microflows-expressions) - 解释如何使用微流程表达式
* [设置 & 更改微流中不同活动的值](microflows-setting-and-changing-value) - 解释如何设置或/并更改微流活动的值
