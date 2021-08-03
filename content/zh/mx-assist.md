---
title: "Mendix 助手"
category: "微型流动"
menu_order: 10
description: "描述Mendix Studio中的 Mendix 助手。"
tags:
  - "工作室"
  - "mendix 帮助"
  - "AI"
  - "助理"
---

## 1 导言

Mendix Assist是一种人工智能驱动的代理，帮助您在 Mendix Studio 中配置微流。 它就如何根据微流中已经存在的活动、参数和事件配置微流的下一步提出了没有经验的用户建议。

Mendix Assist是使用机器学习分析构建的，其中包括与Mendix建立的1 200多万个匿名应用程序流量。 Mendix 利用深度学习来检测微流中的最佳做法模式。 基于这些模式 Mendix Assists 预测微流中下一个活动的最佳选择。 此外，Mendix Assist通过分析正在建立的新微流来不断学习。

## 2 Mendix 辅助概述

Mendix Assist默认启用，并在一个 [微流程](microflows) 流中显示为蓝色点。 当你悬停在点上时，一只弓挂在点上。

![](attachments/mx-assist/mendix-assist-icon.png)

{{% alert type="info" %}}

可以不使用 Mendix Assistance 定期添加活动。

{{% /报警 %}}

点击机器人连接查看Mendix Assist建议。

{{% image_container width="350" %}}![](attachments/mx-assist/mx-assist-recommendations.png)
{{% /image_container %}}

Mendix Assists列出了特定微流中最有可能到不太可能的五项建议。 点击建议继续执行并将其插入微流。 欲了解更多信息，请参阅 [添加活动和元素的 Mendix Assist](#add-activities) 部分。

{{% alert type="info" %}}

一些活动仍然需要在 **属性** 中配置才能正常运行。 这关系到诸如 **创建对象**等活动，当你需要手动设置实体和属性值时。

{{% /报警 %}}

一旦您选择了一个活动或事件来插入到微流使用 Mendix Assist， 此活动/事件的 信息对话框在流程上方显示。

![](attachments/mx-assist/info-dialog.png)

以下选项可在信息对话框中使用：

* **不再显示** - 禁用信息对话框(当您插入其他活动时不会再显示)
* **Lean More** - 打开微流程活动文档
* **谢谢，我明白** — — 开启当前信息对话框

## 3 个设置

要打开Mendix Assist设置，请点击信息对话框右上角的装备图标。

![](attachments/mx-assist/settings-mx-assist.png)

Mendix Assist可用的设置如下表所示：

| 设置          | 描述                                                     |
| ----------- | ------------------------------------------------------ |
| 菜单辅助功能开启/关闭 | 切换设置功能/禁用工具。                                           |
| 信息对话是否开启/关闭 | 切换设置功能/禁用信息对话框。 **注意** 如果Mendix Assists 被关闭，信息对话框将被禁用。 |

您也可以通过单击Mendix Studies顶部菜单栏中的信息图标启用/禁用 Mendix Assist：

{{% image_container width="300" %}}![](attachments/mx-assist/info-icon-setting.png)
{{% /image_container %}}

{{% alert type="info" %}}
如果您禁用Mendix Assist, 信息对话框也将被禁用。 当您重新启用 Mendix Assist, 信息对话框也会被重新启用。
{{% /报警 %}}

## 将活动和元素添加到Mendix Assistant {#add-activities}

您可以使用 Mendix Assistant 添加各种活动。 视微流的复杂性和元素/活动而定。 它可以立即插入，或者您需要向Mendix Assist提供更多信息。 例如，如果您正在添加检查，您需要指定将选中的对象或变量， 和什么条件将被检查：如果对象存在或对象是真实的。 欲了解更多信息，请参阅 [添加检查](#add-check) 部分。

### 4.1 增加活动

要添加活动 (例如 **更改对象**, **显示页面**, **创建对象**, 等), 执行以下操作：

1. 在微流程中点击蓝色Mendix Assistt 点.

2. 浏览建议并选择您需要的活动。

3.  点击选中的活动添加到流程中。

    {{% image_container width="350" %}}![](attachments/mx-assist/mx-assist-list.png)
    {{% /image_container %}}

该活动添加到流程中。

### 4.2 添加检查 {#add-check}

添加检查意味着您将添加带有布尔属性类型的 **Decision** ：您的流程将被分割成一个标签 *true* 的流程，另一个标签为 *false* 欲了解更多信息，请参阅 [Decision](microflows-decision)。

{{% image_container width="300" %}}![](attachments/mx-assist/check-added.png)
{{% /image_container %}}

{{% alert type="info" %}}

If you do not have a variable or/and the attributes of the Boolean type, this option will not be listed in the suggestions.

{{% /报警 %}}

要添加支票，请执行以下操作：

1. 在微流程中点击蓝色Mendix Assistt 点.

2.  查找 **在建议中添加一个检查**。

    {{% image_container width="350" %}}![](attachments/mx-assist/adding-check.png)
    {{% /image_container %}}

3. 检查选项的数量将被打开，选择您想要添加的检查并单击它。

这一决定被添加到微流中。

{{% alert type="info" %}}

检查选项的数量取决于您微流中布尔类型变量的数量和域模型中布尔类型属性的数量。 欲了解更多信息，请参阅 [域模型](domain-models) and [属性](domain-models-attributes)。 您还可以添加一个对象是否存在微流程。

{{% /报警 %}}

### 4.3 作出决定

当您通过Mendix Assist添加决定时，这意味着您在microflow中添加具有枚举类型属性的决定。 欲了解更多信息，请参阅 [Decision](microflows-decision) and [属性](domain-models-attributes)。 这意味着，如果您没有具有枚举数据类型的参数， **添加决定** 将不会出现在建议中。

为了增加这一决定，请做以下工作：

1. 在微流程中点击蓝色Mendix Assistt 点.

2. 查找 **在建议中添加决定** 并选择它。

    {{% image_container width="350" %}}![](attachments/mx-assist/adding-decision.png)
    {{% /image_container %}}

这一决定被添加到微流中。

{{% alert type="info" %}}

**添加决定** 的选项数量取决于您微流程中枚举数据类型的参数数量。 欲了解更多信息，请查看工作室中的 [域模型](domain-models) 和 [属性](domain-models-attributes)。

{{% /报警 %}}

## 5 阅读更多

* [常规信息](general)
* [微型流动](微流)
* [决 定](microflows-decision)
