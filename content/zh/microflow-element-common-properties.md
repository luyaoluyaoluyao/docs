---
title: "公共属性"
parent: "微流和微流法"
menu_order: 110
tags:
  - "studio pro"
  - "共同属性"
  - "微流"
  - "nanoflow"
---

## 1 导言

本文档描述了在微流程编辑器中许多元素共享的共同属性。

{{% alert type="warning" %}}
并非微流或微流中的每个元素都具有所有这些特性。
{{% /报警 %}}

这些是微流和纳米粒子的常见特性：

{{% image_container width="30%" %}}
![属性窗格中的常见属性](attachments/microflows-and-nanoflows/microflow-element-common-properties.png)
{{% /image_container %}}


* [标题](#caption)
* [自动生成标题](#auto-generate-caption)
* [背景颜色](#color)
* [错误处理类型](#error-handling)

## 2 个标题 {#caption}

**标题** 描述了这个元素中发生的情况。 它显示在微流元素中，使微流更容易阅读和理解，而无需添加注释。 如果在这里输入值, [自动生成标题](#auto-generate-caption) 将自动设置为 **否**。

## 3 自动生成标题 {#auto-generate-caption}

**自动生成标题** 属性指定了是否根据活动类型自动生成标题。

| 选项        | 描述                         |
| --------- | -------------------------- |
| 是  *(默认)* | 活动的标题由 Studio Pro生成。       |
| 否         | 您可以自己编辑的 **标题** 属性中的值已被使用。 |

## 3 背景颜色 {#color}

**背景色** 属性允许您为每个活动单独选择背景颜色。 颜色不会影响执行；它们仅用于在流中快速发现元素。 例如，您可以使用 [错误处理程序](error-event#errorhandlers) 红色进行活动，因此您可以轻松地识别它们。

您也可以在 **App 设置** > [杂项](project-settings#miscellaneous) 中为特定类型的所有活动选择默认颜色。 The default color for all activities of a certain type can also be changed by right-clicking a microflow activity and selecting **Set as default color** from the context menu. 这将使当前活动的颜色成为所有活动类型的默认颜色。 如果您更改活动类型的默认颜色，并且应用程序中存在其他类型的活动，指定了不同的单独背景颜色， 您将被问及是否想用新的默认颜色覆盖这些个别颜色。

## 4 个错误处理类型 {#error-handling}

在 **中处理类型**时发生错误，您可以选择处理活动的错误类型。 关于可用选项及其效果的详细信息，请参阅 *Microflow* 中的 [错误处理器](error-event#errorhandlers) 部分。

## 5 阅读更多

* [微型流动](微流)
* [纳诺夫拉](nanoflows)
