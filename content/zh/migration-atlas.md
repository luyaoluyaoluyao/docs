---
title: "Atlas UI更改故障排除问题"
parent: "从 7-8 移动"
menu_order: 20
description: "本文档解释了如何在将项目从 Mendix 7 迁移到 Mendix 8 时修复您的样式。"
tags:
  - "小部件"
  - "主题"
  - "班级"
  - "Atlas系统"
  - "Atlas界面"
  - "样式"
  - "萨瑟文"
  - "CSS"
---

## 1 导言

当你升级到Mendix 8时，你的部件的DOM结构将被更改。 这意味着关联飞船搭配将不会像预期的那样发挥作用。 此文档将允许您的主题与 Mendix 8 兼容。

Each section in this document could apply to your app, but some sections may *not* apply. 如果一个部分不适用于您的情况，您可以跳过它。

{{% alert type="warning" %}}If you have added any content in the **Atlas_UI_Resource module**, you have to move that content out of the module. 如果您不这样做，它将被覆盖。{%/提醒 %}}

当您的应用使用未经修改的 Atlas UI 资源时，将您的应用升级到 Mendix 8 将自动更新您的 Atlas UI 资源到版本 2.1。 如果您没有在自定义文件夹中做任何更改，您很高兴去，您可以跳过本指南的其余部分。

如果您正在使用未经修改的 Atlas UI 资源，但您对自定义文件夹作了更改， 这些改动得到保留，并将用于新的Atlas界面版本。 在这种情况下，您会看到一致性错误。 继续使用 [描述的步骤来处理下面的修改自定义文件夹](#modified) 部分来解决这个错误。

如果您正在使用经修改的Atlas界面资源版本，Mendix 无法自动更新。 在这种情况下，您会看到一致性错误。 为了解决您的主题问题，您需要自己更新地图集。

按照下面的步骤开始升级您的 Atlas UI 资源模块：

1. 下载最新的 [Atlas UI 资源](/appstore/modules/atlas-ui-resources) 模块 (v2.0.0 或更高).
2. 导入此模块到您的应用并替换旧的资源模块。 这将覆盖资源模块内的布局、页面模板和建筑块。 与您旧资源模块相关的 **主题** 文件夹将被移动到 **theme_old** 中。 您将获得一个新的 **主题** 文件夹，包含最新的更改。 从这里您必须根据您是否有自定义样式选择以下之一：<br />
    * 如果您没有在旧的 **主题文件夹中做任何更改** 您可以安全地删除 **theme_old** 并保留其他一切。 您的样式将会起作用，您可以先查阅此文档。 <br />
    * 如果您在旧的 **主题** 文件夹中做了任何更改，您将需要做一些手动工作来调整您的搭配。 请参考下面的信息来决定根据您的需要做什么。

## 2 将旧主题文件夹整合到新主题文件夹

When migrating from Mendix 7 to Mendix 8, you must integrate **theme_old** into **theme** while adhering to several guidelines. 您必须遵循哪条准则根据您的特定项目而有所不同。 请参考以下小节根据您独特的情况进行说明。

{{% alert type="info" %}}If you customized any widget where the DOM structure has changed, consult [Troubleshoot DOM Changes when Migrating to Mendix 8](migration-dom-issues) to ensure your custom styling works.{{% /alert %}}

### 2.1 使用 HTML 文件

如果您修改了您的 HTML 文件，请参阅下面的说明。 如果你没有，你可以忽略这个小节。

如果您更改了任何 **索引\*.html** 文件，请确保做以下工作：

* 将你在旧文件中做的相同的更改应用到新的 HTML 文件
* 请确认 **bootstrap.min.css**, **bootstrap-rtl.min.css**, 和 **mxui.css** 导入不存在
* 请确保您不再导入 **风格/css/lib.css**
* 请确保您在 `<head></head>` 标签内放置了 `<link rel="stylesheet" type="text/css" href="styles/web/css/main.css?{{cachebust}}">` 或 `{{themecss}}`

如果您更改了任何 **登录\*.html** 文件，完成以下操作：

* 将你在旧文件中做的相同的更改应用到新的 HTML 文件
* 确认 **bootstrap.min.css** and **mxui.css** 导入已经成功(如果他们没有导入，删除他们)
* 请确保您不再导入 `风格/css/lib.css`
* 将 `<link*rel*="stylesheet" *type*="text/css" *href*="styles/web/css/main.css?{{cachebust}}">` 或 `{{themecss}}` 放入 `<head></head>` 标签

### 2.2 使用 JSON 文件

如果您修改了 *settings.json* 或 *components.json* 文件，请参阅下面的说明。 如果你没有，你可以忽略这个小节。

#### 2.2.1 设计属性

如果您改变了主题中的设计属性，您必须手动将它们整合到新的 Atlas UI 中。

设计属性存储在 *settings.json* 文件的 `设计属性` 部分。

如果您有未被移动到新的 Atlas UI 主题的自定义设计属性， 您将会看到一致性错误(错误代码 **CE6083**) 将会通知您项目缺失的设计属性。

请将您的自定义设计属性移动到新的 Atlas UI 主题的 *settings.json* 文件。

### 2.2.2 额外的 CSS 文件

{{% alert type="warning" %}}
不建议更改 `cssFiles`。 请考虑将自定义的 CSS 文件移动到您的 *主题/样式/web/sass/app/_custom.scss* 文件。
{{% /报警 %}}

如果您在 *settings.json*中更改了 `cssFiles` ，您必须将您的更改整合到新的 *settings.json* 文件。

默认情况下，Atlas界面版本1包含两个文件：

```javascript
"cssFiles": [
    "styles/css/lib/lib.css",
    "styles/css/custom/custom.css"
],
```

但Atlas2.1.0使用单一文件：

```javascript
"cssFiles": [
    "styles/web/css/main.css"

```

如果您的 `cssFiles` 部分添加了更多文件，您必须将它们包含在您的新主题 *settings.json* 文件中。

如果您在 *components.json*中更改了混合移动应用导入，请确保做以下事情：

* 手动整合您旧的 *components.json* 到新文件夹
* 确认 *bootstrap.min.css*, *bootstrap-rtl.min.css*, 和 *mxui.css* 导入已经完成(如果他们没有被删除)
* 确认 *styly/css/lib/css* 更改为 *styles/web/css/main.css*

### 2.3 使用自定义文件夹文件

如果您更改了自定义文件夹，请参阅下面的说明。 如果你没有，你可以忽略这个小节。

如果您在自定义文件夹中添加、删除或更改了自定义变量，请从 *theme_old/styles/sass/custom/_custom-variables.scss* 复制到 *theme/styles/web/sass/app/_custom-variables.scss* 复制您的内容。

如果您在自定义文件夹中添加或更改自定义样式，将您的内容或文件从 *theme_old/styles/sass/custom/* 复制到 *theme/styles/web/sass/app/*
* 在这种情况下，还请确保您旧的 *custom.scss* 文件重命名为 *_custom.scss*

### 2.4 处理Lib 文件夹文件

如果您更改了您的 *样式/sass/lib* 文件夹，请参阅下面的说明。 如果你没有，你可以忽略这个小节。

如果您在 *样式/sass/lib* 文件夹中更改了任何文件，请完成下面的操作：

* 如果您更改了文件的内容或名称， 您必须在新文件和新主题文件夹中手动做出相同的更改(同时保留Mendix 8 [DOM更改](migration-dom-issues))
* 如果您删除了一个文件，无需操作

如果您将一个文件添加到 *lib/base* 文件夹中，复制来自 *theme_old/styles/sass/lib/base/* 到 *theme/styles/web/sass/core/base/* 的文件。 您还必须完成以下操作：

* 导入文件到 *主题/样式/web/sass/main.scss* 在 `基础下` 组按字母顺序排序

如果您添加了一个文件到 *lib/component* 文件夹，则从 *theme_old/styles/sass/lib/components/* 复制该文件到 *theme/styles/web/sass/core/widgets/*。 您还必须完成以下操作：

1. 导入文件到 *主题/样式/web/sass/main.scss* 按 `小部件` 组按字母顺序排序
2. 从您的文件中剪切所有设计属性和额外类(稍后粘贴)，只留下默认样式
3. 在 *主题/样式/web/sass/core/helpers/* 中创建一个具有相同名称的新文件
4. 将这些设计属性和额外类粘贴到这个新文件
5. 导入文件到 *theme/styles/web/sass/main.scss*

如果您添加了一个文件到 *lib/customwidgets* 文件夹，请将您的内容从 *theme_old/styles/sass/lib/customwidgets/* 复制到 *主题/styles/web/sass/core/widgetscustom/* 您还必须完成以下操作：

* 将文件导入到 *主题/样式/web/sass/main.scss* 按 `自定义小部件` 组按字母顺序排序

如果您添加了一个文件到 *lib/buildingblock* 文件夹，则从 *theme_old/styles/sass/lib/buildingblocks/* 复制到 *theme/styles/web/sass/resources/atlas_resources_default/buildingblocks* 复制该文件。 您还必须完成以下操作：

* 将文件导入到 *主题/样式/web/sass/main.scss* 下 `Building Blocks` 分组按字母顺序排序

如果您添加了一个文件到 *lib/layouts* 文件夹，则从 *theme_old/styles/sass/lib/layouts/* 复制该文件到 *theme/styles/web/sass/resources/atlas_resources_default/layouts*。 您还必须完成以下操作：

* 导入文件到 *主题/样式/web/sass/main.scss* 按 `布局` 组按字母顺序排序

请确保任何自定义或添加的 Sass文件都会被导入到 *styles/web/sass/main.scss* 或 *styles/web/sass/app/_custom.scss* 中。

在通过上述指南解决问题后，完成以下步骤来测试您的迁移应用：

### 2.5 使用修改后的自定义文件夹 {#modified}

1. 重新编译您的照片到CSS。
2. 测试您的应用以查看一切是否正常。
3. 删除 *theme_old*。

## 3 阅读更多

* [疑难解答DOM 更改](migration-dom-issues)
* [Atlas界面](/howto8/front-end/atlas-ui)
