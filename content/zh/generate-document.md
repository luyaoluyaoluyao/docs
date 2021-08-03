---
title: "生成文档"
parent: "活动"
menu_order: 80
description: "描述从微流程生成文档。"
tags:
  - "PDF"
  - "文档"
  - "文档模板"
  - "HTML"
  - "Microsoft Word"
  - "ODT"
  - "studio pro"
  - "生成文档"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/generate-document.pdf)。
{{% /报警 %}}

{{% alert type="warning" %}}
此活动只能在 **微流** 中使用。
{{% /报警 %}}

## 1 导言

**生成文档** 活动用于将文档写入到文件中，基于 [文档模板](document-templates)。

![生成文档](attachments/generate-document/generate-document.png)

关于哪些类型的文档可以创建的更多信息，见 [文档类型](#document-type)。

## 2 属性

该活动有两组属性。 左侧对话框中的人，以及右侧属性窗格中的人：

![生成文档属性](attachments/generate-document/generate-document-properties.png)

**生成文档** 属性窗格由以下部分组成：

* [行 动](#action)
* [常用的](#common)

## 3 行动科 {#action}

属性窗格的 **动作** 部分显示与此活动相关的动作。

您可以打开一个对话框，通过点击操作旁边的椭圆(**…**)来配置此动作。

You can also open the dialog box by double-clicking the activity in the microflow or right-clicking the activity and selecting **Properties**.

### 3.1 档案

包含生成文档的文件名称。 它应该是实体 *System.FileDocument* 或其专业化的对象。

### 3.2 语文

文件标题和标签所用的语言载于下表：

| 选项          | 描述                                      |
| ----------- | --------------------------------------- |
| 当前用户 *(默认)* | 使用当前用户的语言。                              |
| 项目默认        | 使用 [工程设置](project-settings) 中指定的默认语言。   |
| 变量          | 使用所选对象中存储的语言，语言类型必须是 *System.Language*。 |

### 3.3 文档类型{#document-type}

文档类型指定生成的文档类型。

| 选项        | 描述                          |
| --------- | --------------------------- |
| HTML      | 以 HTML 格式生成文档。              |
| PDF       | 以 PDF 格式生成文档。               |
| 2007年Word | 用2007年格式生成文件。               |
| 2003年词    | 生成一个 Word 2003 格式的文档。       |
| 富文本格式     | 生成一个 Rich-text 格式的文档。       |
| ODT       | 以 Open Office (ODT) 格式生成文档。 |

### 3.4 覆盖边距

**覆盖边距** 允许您设置自定义边距。 通过使用变量，这些变量可以在运行时定义。

### 3.5 模板

模板定义了用于生成文件的 [文档模板](document-templates)。 根据所选文档模板，需要指定一个或多个 [参数](#argument)。

### 3.6 参数

根据选定的文档，您将在表格中看到其参数列表。 参数将数据传递到活动中。

#### 3.5.1 部件

文档模板中需要传递参数的小部件名称。 此属性是只读的。

#### 3.5.2 Type

文档模板中使用的只读参数类型。

#### 3.5.3 参数 {#argument}

**编辑参数** 按钮允许您编辑参数值。  一个参数是您要传递到文档模板的输入数据。 对于每个文档模板参数(对于每个非嵌套数据视图和数据网格)，您必须提供一个相同类型的参数。 参数的值使用 [表达式](expressions) 表达。

## 4 共同部分 {#common}

{{% snipet file="refguide8/microflow-common-section-link.md" %}}