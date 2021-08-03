---
title: "循环"
category: "微型流动"
menu_order: 30
description: "在 Mendix Studio 中描述一个循环。"
tags:
  - "工作室"
  - "微流"
  - "循环"
  - "循环"
---

## 1 导言

当构建 [微流](microflows) 时，循环用于在对象列表上进行迭代并对列表中的每个项目进行操作。 例如，您可以从数据库检索订单清单，然后循环到这个列表并标记已处理的订单。 欲了解更多详情，请见第 [3 循环示例](#loop-example) 部分。

循环被视为一个帧。 循环中的流程是为每个对象执行的。 这意味着，如果您将多个活动添加到循环中，那么每个项目都会执行完整的流程。 例如，您可以添加一个循环，防止在客户被阻止时处理订单。

![](attachments/microflows-loop/loop.png)

循环可以包含微流其他部分使用的所有类型元素，但启动和停止事件除外。 此外，只有循环可以包含 [中断事件](/refguide/break-event) 和 [继续事件](/refguide/continue-event)。 休息活动只用于循环中停止在对象列表上的迭代，然后在微流中继续其它流程。 继续事件仅用于停止当前的迭代和开始下一个对象的迭代。

## 2 循环属性

循环属性由 **数据源** 部分组成，描述如下：

* **环绕** — 一个变量是你将循环的项目列表

*  **循环变量名称** — — 指目前正在处理的列表项的名称

    {{% image_container width="350" %}}![循环的数据源属性](attachments/microflows-loop/loop-properties.png)
    {{% /image_container %}}

## 3 个循环示例 {#loop-example}

让我们研究一个直截了当的使用案例，在这个案例中，您从数据库中检索了一个订单列表。 在这个列表上循环，并将订单标记为处理结果。

![循环示例](attachments/microflows-loop/loop-example.png)

请确保您有以下前提条件：

1. [在您的域模型中创建一个实体](domain-models#adding-new-entities) 并命名它 *订单*。
2. [为这个实体创建布尔类型的属性](domain-models#adding-new-attributes) ，以表明订单状态并命名此属性 *已处理*。
3. [创建微流](microflows#creating-new-microflow)。

要开始使用情况，请做以下操作：

1. 打开您想要添加循环的微流程。

2. 首先，我们需要获得我们将循环的订单清单。 执行以下操作： <br />

    a. 在 **工具箱**, 选择 **检索**, 拖放它到微流程。 <br />

    b. 会议文件。 在 **属性** > 中， **数据源** 部分 从数据库中选择 ****, 并设置 *订单* 为此活动的实体。 ( **范围** 属性已设置为 **默认所有** 属性)<br />

    {{% image_container width="350" %}}![检索对象属性](attachments/microflows-loop/retrieve-properties.png)
    {{% /image_container %}}

3. 随着我们检索了我们可以处理的订单清单，我们将为此创造一个循环和逻辑。 执行以下操作： <br />

    a. 在 **工具箱**, 选择 **循环**, 拖放它到微流程。 <br />

    ![循环已添加](attachments/microflows-loop/loop-added.png)<br />

    b. 会议文件。 在 **属性**, 将 **订单列表** 设置为 **循环** (**循环变量名称** 自动设置)。 我们已经选择了该实体，并将在其对象列表上循环. <br />

    {{% image_container width="350" %}}![在示例中循环属性](attachments/microflows-loop/loop-properties-in-example.png)
     {{% /image_container %}}

4. 现在我们可以添加将每个订单状态更改为 *处理过* 的活动。 这意味着您在循环中添加的活动将在每个对象上执行(每个订单)。 执行以下操作：<br />

    a. 在 **Toolbox**中，选择 **更改对象**，拖放到循环中。<br />

    b. 会议文件。 在 **属性** > 中， **数据源** 部分 **更改对象** 活动 将 **对象** 设置为 **订单**。<br/>

    b. 会议文件。 当 **更改成员** 选项出现时，点击 **添加新值**。<br />

    ![更改循环示例中的对象属性](attachments/microflows-loop/change-object-properties.png)

5. 在 **更改对话窗口值** 中，执行以下操作：<br />

    a. 将 **选择一个属性或关联** 到 **已处理的 (布尔)**.<br />

    b. 会议文件。 在 **表达式** 标签页中，通过输入 *true* 设置此属性的 **新值** <br />

    ![变化价值对话窗口示例](attachments/microflows-loop/change-value-dialogue-example.png)

    b. 会议文件。 点击 **添加** 保存更改。

查看视频并配置上面的示例：

<video width="768" height="432" controls src="attachments/microflows-loop/loop-example-video.mp4">视频</video>

因此，我们有一个从微流中检索到的订单清单和一个循环，它们在这个列表上反复。 循环中的活动设置每个订单的状态。

## 4 阅读更多

* [微型流动](微流)
