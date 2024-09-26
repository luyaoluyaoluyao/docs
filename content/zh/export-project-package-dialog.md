---
title: "导出工程包"
parent: "文件菜单"
menu_order: 30
tags:
  - "studio pro"
  - "导出应用"
  - "导出项目包"
aliases:
  - /developerportal/support/export-a-project-package.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/export-project-package-dialog.pdf)。
{{% /报警 %}}

## 1 导言
您可以导出一个项目包(*)。 pk*) 从 Mendix Studio Pro 进行备份或与其他Mendix 开发者共享。 如果你想要给他人整个应用，或者如果你需要在提交工单时提供测试应用，这是有用的。

可以使用 [导入项目包](import-project-package-dialog) 导入项目包再次导入到新的应用中。

导出包裹。 打开 **文件** 菜单 > **导出项目包** 并在 **导出项目包** 对话框中选择相关的选项：

![导出工程包对话窗口](attachments/file-menu/export-project-package.png)

 关于您可以选择哪些选项的更多信息，请参阅下面的章节。

## 2 目标

您可以指定要导出包的文件夹。 默认位置是工程目录内名为 *软件包* 的文件夹。

## 3 导出数据

Mendix 工程包可以导出到 Mendix 软件包文件(*.mpk*)。  您可以选择导出内置部署数据库和上传文件，或者导出没有数据。 您可以选择以下选项之一：

* **没有数据** - 软件包将在没有数据的情况下导出。

* **现有快照** - 此选项将包括导出项目包中现有的数据库快照

    ●{% alert type="info" %}}此选项仅在快照已创建时有效。 如有必要，您可以通过 **版本控制** > **添加数据快照** 创建快照。
    {{% /报警 %}}

* **来自当前数据库的新快照** - 将从数据库创建一个新快照并将其包括在导出中

    {{% alert type="info" %}}This option is available after you run the app locally at least once, because a local database will be created when running the app for the first time.
    {{% /报警 %}}

## 4 阅读更多

* [导入工程包](import-project-package-dialog)
* [版本控制菜单](版本控制-菜单)
