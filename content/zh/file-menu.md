---
title: "文件菜单"
parent: "menus"
description: "在Studio Pro中描述文件菜单。"
menu_order: 5
tags:
  - "Studio Pro"
  - "文件菜单"
  - "文件"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/file-menu.pdf)。
{{% /报警 %}}

## 1 导言

**文件** 菜单允许您管理文件和项目，例如创建一个新项目或保存更改：

{{% image_container width="300" %}}![文件菜单](attachments/file-menu/file-menu.png)
{{% /image_container %}}

## 2 个菜单项概述 {#overview}

下面的表格描述了 **文件** 菜单项：

| 菜单项       | 描述                                                                                                                            | 快捷键                                               |
| --------- | ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| **新建文档**  | 在当前打开的应用程序中创建一个新文档。 您可以选择文档的名称、位置和类型。                                                                                         | <kbd>Ctrl</kbd> + <kbd>N</kbd>                    |
| **新建项目**  | 创建一个新的单开发者项目。 单一开发者项目只是一个文件(扩展名 *)。 pr* , 表示存储在本地文件系统中的“Mendix project”. 关于 **新项目** 菜单项及其设置的更多信息，请参阅 [新项目](new-project)。      | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>N</kbd> |
| **打开项目**  | 打开一个现有的单开发者项目 (*.mpr*) 或一个项目包 (*.mpk*)。 关于单开发者项目的信息，请参阅上面 **新项目**。 关于 **打开项目** 菜单项的更多信息，请参阅 [打开项目](open-app-dialog)。          | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>O</kbd> |
| **最近的项目** | 显示快速打开最近打开的项目列表。                                                                                                              |                                                   |
| **保存**    | 保存当前活动文档选项卡中的更改。                                                                                                              | <kbd>Ctrl</kbd> + <kbd>S</kbd>                    |
| **全部保存**  | 保存打开的所有文档中的更改。                                                                                                                | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd> |
| **关闭**    | 关闭当前文档。 您将被要求保存或放弃所需的更改。                                                                                                      | <kbd>Ctrl</kbd> + <kbd>W</kbd>                    |
| **全部关闭**  | 关闭所有文档标签。 您将被要求保存或放弃所需的更改。                                                                                                    | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>W</kbd> |
| **关闭项目**  | 关闭当前打开的项目并返回起始页面。                                                                                                             |                                                   |
| **导出为图像** | 导出当前文档为 *.png* 格式的图像。 以下文档类型可以导出为图像：microflow、域模型、文档模板和XML映射。                                                                 |                                                   |
| **导出工程包** | 导出当前应用到项目包 (*.mpk*) 文件。 例如，当你想要给他人整个应用程序时，这将是有用的， 或者提交工单时需要提供测试应用程序。 关于如何导出项目包的更多信息，见 [导出项目包](export-project-package-dialog)。 |                                                   |
| **导入工程包** | 导入一个使用 **导出项目包** 菜单项创建的项目包。 关于导入项目包的更多信息，请参阅 [导入项目包](import-project-package-dialog)。                                          |                                                   |
| **退出**    | 关闭工作室专业版                                                                                                                      |                                                   |

## 3 阅读更多

* [Studio Pro Overview](studio-pro-overview)
