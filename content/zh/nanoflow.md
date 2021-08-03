---
title: "Nanoflow 属性"
parent: "nanoflows"
tags:
  - "studio pro"
---

## 1 导言

此页面描述了nanoflows的属性。 关于使用纳米调节器和纳米调节器的详细信息，请参阅 [Nanoflows](nanoflows)。

## 2 属性

下面的图像是nanoflow 属性的示例：

{{% image_container width="250" %}}![Nanoflow 属性](attachments/microflows-and-nanoflows/nanoflow-properties.png)
{{% /image_container %}}

Nanoflow 属性由以下部分组成：

* [常用的](#common)
* [产出](#output)
* [安全](#security)
* [用法](#usage)

### 2.1 共同部分{#common}

#### 2.1.1 姓名

**名称** 是nanoflow的内部名称。 当在应用程序中使用 nanoflow 时，您将使用此名称。 它在模块中必须是唯一的，但是你可以在不同的模块中拥有两个同名的 nanoflow。 当提及纳米时， 您通常将在模块名称前面填写，以确保其唯一性，并允许您在其他模块中使用 nanoflow。

#### 2.1.2 文件

**文档** 允许你描述你的 nanoflow 以使人们更容易使用和修改它。

### 2.2 输出部分{#output}

#### 2.2.1 返回类型

返回类型定义了纳米返回的信息。 调用者会得到这种类型的结果。 关于可能的返回类型，请参阅 [数据类型](data-types)。

### 2.3 警卫科{#security}

#### 2.3.1 允许的角色

这些是用户必须能够执行 nanoflow的 [模块角色](module-security#module-role)。

欲了解更多信息，请参阅 [Module Security](module-security)。

### 2.4 使用部分 {#usage}

#### 2.4.1 标记为已使用

You can search for unused items (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd>, then select **Unused items** in the **Search for** drop-down menu) in Studio Pro. 仅从 JavaScript 代码调用的 Nanoflow 将被列为未被使用，因为Studio Pro 无法在源代码中查看。

By setting the property **Mark as used** to **Yes**, you explicitly specify that the nanoflow is used and Studio Pro will no longer list it when searching for unused items.

默认： *否*
