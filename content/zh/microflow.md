---
title: "微流程属性"
parent: "微流"
tags:
  - "微流"
  - "实体访问"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/microflow.pdf)。
{{% /报警 %}}

## 1 导言

本文档描述微流的特性。 如果你想要看看什么是微流和它们包含什么元素，你可以检查 [微流](microflows)。

## 2 属性

下面的图像是微流程属性的示例：

{{% image_container width="250" %}}![微流程属性](attachments/microflows-and-nanoflows/microflow-properties.png)
{{% /image_container %}}

微流程属性由以下部分组成：

* [常用的](#common)
* [并行执行](#concurrent)
* [产出](#output)
* [安全](#security)
* [用法](#usage)

### 2.1 共同部分 {#common}

#### 2.1.1 姓名

**名称** 是微流程的内部名称。 当在应用中提及微流时，您将使用此名称。 它在模块中必须是唯一的，但你可以在不同模块中有两个具有相同名称的微流。 在提及微流时， 您通常将在模块名称前面填写，以确保唯一性，并允许您在其他模块中使用微流。

#### 2.1.2 文件

**文档** 允许您描述您的微流程，使人们更容易使用和修改它。

### 2.2 并行处决科 {#concurrent}

#### 2.2.1 不允许

**禁用** 属性允许您指定是否可以同时执行多次微流。 这适用于使用应用程序的所有最终用户，而不仅仅是在一个用户会话内。

如果微流程会干扰另一个运行中的实例（例如，不允许同时执行微流程可能是有用的 如果它访问全球资源)。

| 选项        | 描述                             |
| --------- | ------------------------------ |
| 没有 *(默认)* | 可以同时执行一次以上的微流。                 |
| 否         | 不可能同时执行一次以上的微流；用户收到消息或执行另一个微流。 |

#### 2.2.2 错误消息

**错误消息** 定义了当不允许并行执行以及用户试图在已经执行时启动微流程时用户获取的信息。 如果定义了 **错误的微流程** ，这将不会显示。

#### 2.2.3 微流错误

**错误 microflow** 定义了另一个要执行的微流，当不允许并行执行时，用户试图在已执行时启动微流。 设置后，将不会向用户显示更多消息。

### 2.3 产出部分 {#output}

#### 2.3.1 退货类型

返回类型定义了微流返回的信息。 调用微流的人会得到此类型的结果。 查看 [数据类型](data-types) 以获取可能的返回类型。

{{% alert type="info" %}}
为了表明是否应该承诺对象，您可以使用布尔作为微流程的返回类型。
{{% /报警 %}}

### 2.4 警卫科 {#security}

#### 2.4.1 应用实体访问

**应用实体访问** 表示基于当前用户的实体访问是否在对对象执行操作时适用。 设置为“是”，将从 [检索操作](retrieve) 中检索到的对象限制为只允许当前用户看到的对象。 同样，在阅读和撰写属性和关联时，适用当前用户的实体访问。 相反，如果不使用实体访问，则允许所有操作并检索所有对象。

| 选项         | 描述                         |
| ---------- | -------------------------- |
| 否          | 实体访问用于检索和操纵物体。 考虑到当前用户的权利。 |
| 没有  *(默认)* | 未应用实体访问权限。                 |

{{% alert type="info" %}}
默认的实体访问权限不被应用。 设置 **将实体访问** 应用到 **是,** 是, 如果您想要执行一些操作, 尊重当前用户的访问权限。
{{% /报警 %}}

{{% alert type="info" %}}
应用实体访问的微流在编辑器中有 **实体访问** 标签。
{{% /报警 %}}

#### 2.4.2 允许的角色

**允许的角色** 定义了用户必须能够执行microflow的 [模块角色](module-security#module-role)

{{% alert type="warning" %}}
这些角色仅在从客户端执行微流程时才会被检查。 微流总是允许调用另一个微流，当时不会检查这些角色。
{{% /报警 %}}

欲了解更多信息，请参阅 [Module Security](module-security)。

### 2.5 使用部分 {#usage}

#### 2.5.1 标记为已使用

You can search for unused items (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd>, then select **Unused items** in the **Search for** drop-down menu) in Studio Pro. 仅从 Java 代码调用的微流将被列为未使用，因为Studio Pro 无法在 Java 源代码中看到。

By setting the property **Mark as used** to **Yes**, you explicitly specify that the microflow is used and Studio Pro will no longer list it when searching for unused items.

默认： *否*

## 作为微流程曝光。

There is one other property which is accessible by right-clicking in the microflow and selecting **Properties**.

![显示为微流程激活](attachments/microflows-and-nanoflows/microflow-expose.png)

通过选择 **作为微流程操作**  ，您可以将微流程作为微流程曝光。 当您正在编辑您选择的类别中的微流时，暴露微流会使它出现在 **工具箱** 中。 当这个动作在微流程中使用时，它将显示提供的字幕和图标。

微流动作需要说明和类别，但图标是可选的。 当没有选择图标时，使用默认的微流程调用动作图标。 建议的图标大小为16x16像素。
