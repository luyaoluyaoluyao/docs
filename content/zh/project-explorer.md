---
title: "项目浏览器"
parent: 视图菜单
menu_order: 40
tags:
  - "studio pro"
  - "项目浏览器"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/project-explorer.pdf)。
{{% /报警 %}}

## 1 导言

**Project Explorer** 显示您项目的完整结构，包括模块中的所有文档：

{{% image_container width="250" %}}![](attachments/project-explorer/project-explorer.png)
{{% /image_container %}}

**Project Explorer** 包含以下内容：

* **项目** 文件夹 — 包含适用于您整个项目的设置和文档 (详情请参阅 [项目](project))
* **模块**  - 包含设置，域模型。 和 *适用于此模块的文档* (详情请参阅 [模块](modules))
  * **域模型** — — 一个以抽象方式描述您应用程序使用的信息(或 *数据*)的模型； 一个模块只能有一个域模型
  * **文档** - 一个单独的文件，例如一个 [页面](pages), [microflow](microflows), 或 [预定的事件](scheduled-events)。

## 2 执行基本函数

在 **工程资源管理器**中，您可以做以下工作：

* **筛选器** — — 输入一个模块的名称, 文件夹, 或 document into the **Filter** fields to filter the project 文档并高亮在 **Project Explorer** 中输入的文本。 当通过模块或文件夹名称过滤时，将显示所有匹配模块或文件夹的内容。 此外，在聚焦于 **筛选器** 字段时，可以这样做：
  * 浏览 **项目资源管理器** 使用 <kbd>Aven</kbd> 和 <kbd>Macro</kbd> 键
  * 按 <kbd>进入</kbd> 来展开文件夹或打开文档
  * 按 <kbd>Esc 清除过滤器查询</kbd>
* **打开文档** - 双击文档以打开它
* **选择活动文档** - 点击 **项目探索器的右上角的图标** 快速查看在 **项目资源管理器** 树木中的活动文档。 默认情况下，活动文档总是被选中的，所以您可以快速查看您正在编辑的文档位于哪里。 您可以在 **编辑** > **首选项** 对话框中更改此行为。
* **展开所有文档** - 点击左上角的加号图标 **Project Explorer** 以扩展所有文档并查看您项目的整个结构
* **折叠所有文档** - 点击左上角的减号图标 **项目资源管理器** 折叠所有文档
* **展开或折叠一个单独的文件夹** - 以在一个单独的文件夹中展开/折叠文档，单击附加/减小图标或双击文件夹。
* **执行选定文件夹中的特定动作** -- 右键点击选定的文件夹查看您可以执行的函数。 函数列表取决于文件夹。 当右键点击 **System** 模块时，您只能找到此模块的用法。 当右键点击 **MyFirstModule** 时，您可以添加一个页面，并添加一个微流程， 重命名模块，导出模块包，复制/粘贴文档等等。

## 3 阅读更多

* [项目](项目)
* [模块](模块)
* [安全](安全)
