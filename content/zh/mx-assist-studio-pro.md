---
title: "MxAssist逻辑箱"
parent: "微流"
description: "在Mendix Studio Pro中描述MxAssist逻辑箱。"
tags:
  - "studio pro"
  - "mendix 帮助"
  - "AI"
  - "助理"
  - "mx 辅助逻辑bot"
  - "logic bot"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/mx-assist-studio-pro.pdf)。
{{% /报警 %}}

## 1 导言

MxAssist逻辑机器人是一个AI驱动的虚拟开发商机器人，帮助您在 Mendix Studio Pro中模拟和配置应用程序逻辑(microflows)。 它根据已经设计的活动、参数和其他与环境有关的信息，就微流中的下一个最佳活动提供了具体的建议。

MxAssist逻辑箱是使用机器学习分析来构建超过1 200万个匿名应用程序逻辑(微流)*—*是与Mendix*一起构建的，*以检测和学习微流中的最佳做法模式。

MxAssist逻辑箱的主要功能如下：

* **下一个最好的行动建议** - 它建议在40多个不同的选项中进行前五个最好的活动，精确度为95%。
* **自动配置** — — 它不仅提供下一个最佳操作，而且通过预先填充此操作的参数使开发进一步自动化。
* **上下文建议** - 它以不同方式产生上下文. 包括在微流程中左和右边的“查找”，当开发者插入新的活动或决定中流时； 并通过使用它所来自的页面推断上下文.
* **精确度高** - 模型的不断改进和训练使精度水平从95%提高到较高水平。

## 2 MxAssist逻辑箱设置

要访问MxAssist逻辑箱的设置，请打开 **编辑** > **首选项** > **MxAssist逻辑箱** 部分。 欲了解更多信息，请参阅 [首选项](preferences-dialog)。

在 **MxAssist逻辑箱** 部分中，您可以设置以下内容：

* **启用 MxAssist逻辑箱** - 开启或关闭MxAssist逻辑箱。

* **为系统变量显示建议** - 启用后，MxAssist逻辑机器人将为系统对象提出建议(例如： 它可以建议您更改这些对象，如 **当前用户** 或 **当前会话**：

  ![系统变量建议](attachments/mx-assist-studio-pro/mx-assist-system-variables.png)

欲了解更多关于首选项的信息，请参阅 [首选项](preferences-dialog)。

## 使用MxAssist逻辑箱构建微流

MxAssist逻辑箱默认启用，并在 [微流程](/refguide8/microflows) 的流中显示为蓝色点。 当你悬停在点上时出现了一只弓箭头：

{{% image_container width="350" %}}![Logic Bot Icon](attachments/mx-assist-studio-pro/mendix-assist-icon.png){{% /image_container %}}

但是可以在不使用 MxAssist逻辑箱的情况下定期将元素添加到微流中。 MxAssist逻辑箱帮助您更快地添加元素到微流中，因为它提供了一个最相关活动的简短列表。

若要使用 MxAssist逻辑机器人，请执行以下操作：

1. 点击bow-tie 查看下一个最佳行动建议：

    {{% image_container width="350" %}}![Logic Bot Recommendations](attachments/mx-assist-studio-pro/mx-assist-recommendations.png){{% /image_container %}}

2. 点击推荐活动之一将其插入微流。

3. 在 **属性** 对话框中，配置选定的活动/事件。

活动/事件已添加到您的微流程中。

如果您没有在五个建议列表中看到所需的活动或元素。 您可以点击 **添加其他元素** 并选择一个活动、循环、决定、合并或对象类型决定。

## 4 阅读更多

* [微型流动](微流)