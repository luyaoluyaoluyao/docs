---
title: "下载文件"
parent: "客户活动"
menu_order: 20
tags:
  - "studio pro"
  - "下载文件"
  - "客户活动"
aliases:
  - /refguid8/Download+File.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/download-file.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

{{% alert type="warning" %}}
这个动作被忽略，当从离线、本地或混合应用调用微流时不起作用。 For more information, see the [Microflows](offline-first#microflows) section of the *Offline-First Reference Guide*.
{{% /报警 %}}

## 1 导言

**下载文件** 活动可以用于启用浏览器下载特定文件。 最终用户要么看到下载弹出窗口，要么在浏览器中直接显示文件。

{{% image_container width="300" %}}
![下载文件示例](attachments/client-activities/download-file.png)
{{% /image_container %}}

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![下载文件属性](attachments/client-activities/download-file-properties.png)

**下载文件** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 文件

文件文件指定要下载的文件。 文件数据存储在实体的 System.FileDocument 或该实体的专业化中。

### 3.2 在浏览器中显示文件

**在浏览器中显示文件** 定义文件是下载到最终用户指定的位置还是直接显示在浏览器中。

| 选项 | 描述                               |
| -- | -------------------------------- |
| 真的 | 文件已下载到暂存互联网文件的位置，并显示在浏览器的一个新页面上。 |
| 错误 | 文件已下载到最终用户指定的位置。                 |

{{% alert type="info" %}}

移动设备文件总是显示在浏览器窗口中。

{{% /报警 %}}

许多浏览器实现弹出窗口阻止它们非主动打开，例如通过微流程。 对于移动设备，这意味着只有在禁用弹出窗口拦截器后才能从微流中触发下载。 您可以考虑使用 **文件管理器** 小部件来让用户手动启动下载。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}