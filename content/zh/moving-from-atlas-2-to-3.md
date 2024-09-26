---
title: "从Atlas2迁移到Atlas3"
parent: "从 8-9 移动"
menu_order: 6
tags:
  - "Atlas系统"
  - "UI"
  - "UX"
  - "用户体验"
  - "设计"
---

## 1 导言

Atlas3给门迪克斯的风格带来了新的力量和复杂程度。 要从Atlas2升级到Atlas3，请参阅下面 [从Atlas2升级到Atlas3](#upgrade) 部分。 要查看Atlas3带到Mendix的更改摘要，请参阅 [Atlas 3更改摘要参考指南](/refguide/atlas3-change-summary)。

要从Atlas2升级到Atlas3，您必须完成下面的 [升级，从Atlas2升级到Atlas3](#upgrade) 部分。 **If you have not added custom styling into your Atlas**, completing these subsections of *Upgrading from Atlas 2 to Atlas 3* is all you need to do:

* [升级您的主题目录](#upgrade-theme-directory)
* [迁移您的界面内容](#upgrade-ui-content)
* [迁移您的 Web 样式](#upgrade-web-styling)
* [迁移您的原生样式](#upgrade-native-styling)
* [迁移自定义设计属性](#upgrade-design-properties)

升级指示后的章节参考了已知的问题和升级到Atlas3时可能出现的一些问题。 **您可能只需要咨询才能将自定义样式引入您的图集**:

* [升级到Atlas3后的预期问题](#expected-issues)
* [升级到Atlas3后的边缘案例问题](#edge-cases)
* [故障排除通用图集问题](#troubleshoot)

## 2 从Atlas2升级到Atlas3。 {#upgrade}

升级前，请注意，在Atlas3中，由于Mendix 9中不推荐混合配置文件，所有混合内容都被删除。 如果您的应用需要混合内容，我们建议不要升级到Atlas3，除非您已经创建了您自己的混合内容与Atlas分离。

在您开始升级之前。 如果您通过阅读 [文件和文件夹结构](/howto/front-end/customize-styling-new#file-and-folder) *中的</a>部分来咨询Atlas3中引入的文件夹结构更改，*可能会有帮助。

### 2.1 升级您的主题目录 {#upgrade-theme-directory}

要将您的主题目录升级到Atlas3规格，请完成以下步骤：

1.  重命名您的 Atlas 2 **主题** 目录。 我们建议将其命名为 *theme_atlas2*：

    ![阿特拉斯2 文件夹](attachments/atlas-mig/atlas2-themefolder.png)

1.  下载Atlas 3 [**theme.zip**](https://www.dropbox.com/s/guffms4u5idx3us/theme.zip?dl=1) 并将其提取到您的 Mendix 应用程序文件夹的根目录中。 文件夹结构应类似于下面的示例。 **Mendix 应用根**, 然后 **主题**, 然后 **web** 和 **本机**:

    ![阿特拉斯3文件夹](attachments/atlas-mig/atlas3-themefolder.png)

### 2.2 迁移界面内容 {#upgrade-ui-content}

**Atlas 3** 分发以前在 Atlas_UI_Resources中发现的 UI 内容。 在 3 个独立模块中： **Atlas Core**, **Atlas Web Content** and **Atlas Native Content**.

* [**阿特拉斯核心**](https://marketplace.mendix.com/link/component/117187) - 包含阿特拉斯核心样式和布局
* [**阿特拉斯网页内容**](https://marketplace.mendix.com/link/component/117183) - 包含阿特拉斯网页模板和建筑块
* [**阿特拉斯原生内容**](https://marketplace.mendix.com/link/component/117175) - 包含阿特拉斯的原生页面模板和建筑块

#### 2.2.1 将Atlas用户界面资源升级为阿特拉斯核心资源

1. 如果您修改了 **Atlas UI 资源** 中发现的Atlas UI 内容，例如： 创建模块、页面模板或布局，建议将您修改过的界面内容移动到您的应用程序中的另一个用户定义模块。 **如果您没有修改Atlas UI的内容，请跳过此步骤**。
1.  Rename the **Atlas_UI_Resources** module to **Atlas_Core** in Studio Pro by right-clicking the module then clicking **Rename**:

    ![](attachments/atlas-mig/2-rename.png)

1.  从市场下载 **[Atlas Core](https://marketplace.mendix.com/link/component/117187)** 替换已有的 ***Atlas_UI_Resources*** 重命名为 ***Atlas_Core***

    ![](attachments/atlas-mig/3-import.png)

#### 2.2.2 将Atlas网页内容添加到您的应用

1.  从市场下载 **[Atlas 网页内容](https://marketplace.mendix.com/link/component/117183)**

    ![Atlas网上内容](attachments/atlas-mig/atlas-web-content-marketplace.png)

1.  **Atlas网页内容** 将作为一个新模块出现在 **市场模块**

    ![Atlas网页内容文件夹](attachments/atlas-mig/atlas-web-content-folder-structure.png)

#### 2.2.3 将Atlas本地内容添加到您的应用

1.  从市场下载 **[Atlas土著内容](https://marketplace.mendix.com/link/component/117175)**

    ![阿特拉斯本地内容](attachments/atlas-mig/atlas-native-content-marketplace.png)

1.  **阿特拉斯原生内容** 将作为一个新模块出现在 **市场模块** 中：

    ![阿特拉斯本地内容文件夹](attachments/atlas-mig/atlas-native-content-folder.png)

### 2.3 迁移您的 Web 样式 {#upgrade-web-styling}

对 **Atlas 2 web 主题** 的修改包括以下内容：

* 自定义变量的变化
* 添加您自己的自定义样式
* 设计属性的更改
* 更改到 *Login.html* 和 *index.html*

如果您做了上述任何修改，请遵循以下步骤。 这些步骤分为五节：

* [Web 自定义变量](#web-custom-variables)
* [Web 自定义样式](#web-custom-styling)
* [Web 插件自定义样式](#web-additional-custom-styling)
* [网页设计属性](#web-design-properties)
* [Web 资源](#web-resources)

#### 2.3.1 Web 自定义变量 {#web-custom-variables}

本节涉及您对 **个自定义变量** *.scss* 文件的 **Atlas 2 主题** 所作的修改：

```
theme_atlas2/styles/web/sass/app/_custom-variables.scss
```

要将您的自定义变量修改移动到 **Atlas 3**, 有两个选项：

**选项 1** — 如果自定义变量适用于应用级别 然后修改应该移动到 **自定义变量** 的 **Atlas 3 主题的 SCSS 文件** 目录：

```
主题/web/自定义变量.scss
```

**选项 2** — 如果你想要将变量提取为一个可重复使用的模块， 将它们移动到 **自定义变量** 您在 **主题创建的模块的 SCSS 文件** 目录：

```
主题/您的模块/web/custom-variables.scss
```

#### 2.3.2 Web 自定义样式 {#web-custom-styling}

This section concerns modifications you have made to the **custom** SCSS file of your **Atlas 2 theme**:

```
theme_atlas2/styles/web/sass/app/_custom.scss
```

要将您的自定义样式修改移动到 **Atlas 3**, 有两个选项：

**选项 1** — 如果自定义样式适用于应用级别 然后修改应该移动到 **** 的 **Atlas 3 主题的SCSS 文件** 目录：

```
主题/web/main.scss
```

**选项 2** — 如果你想要提取自定义样式到一个可重复使用的模块， 将它们移动到 **主** 你在 **主题资源** 目录中创建的模块的 SCSS 文件：

```
主题/您的模块/web/main.scss
```

#### 2.3.3 Web 附加自定义样式 {#web-additional-custom-styling}

This section concerns modifications you have made to the **app** folder of your **Atlas 2 theme** and any additional SCSS stylesheets that you might have added:

```
theme_atlasl2/styles/web/sass/app/_
```

要将您添加到这里的额外样式表移动到 **Atlas 3**，有两个选项：

**选项 1** — 如果附加样式表适用于应用级别 这些更改应该移动到 **web** **Atlas 3 主题的目录**

```
主题/web/_
```

记得在 ***主题/web/main.scss*** 中包含 `@import <file name>` 以便将您的附加文件纳入SCS系统的编译中。

**选项 2** — 如果你想要提取额外的样式表到一个可重复使用的模块， 将它们移动到您在 **主题创建的模块**:

```
主题/您的模块/web/_
```

Remember to include `@import<file name>` in ***themesource/your-module/web/main.scss*** to include your additional files in the compilation of the SCSS.

#### 2.3.4 网页设计属性 {#web-design-properties}

This section concerns modifications you have made to the **settings.json file** of your **Atlas 2 theme**:

```
theme_atlas2/settings.json
```

自定义您已添加到 **设置的设计属性。 son** 需要移动到网页的 **设计属性** 您在 **主题创建的模块的 JSON 文件** 目录：

```
主题/你的模块/web/design-properties.json*
```

不要添加到模块 **Atlas Core** 或 **Atlas Web Content**。

如果您有用户定义的平台支持或社区支持的部件的设计属性，请按照下面的两个场景。

#### 2.3.5 网络资源 {#web-resources}

本节涉及您对文档 *login.html* 和 *索引的修改。 tml*以及额外的静态资源，如字体库、图像等等。

任何自定义 *index.html* 或 *登录。 tml* 您在 **Atlas 2 主题中创建的页面** 需要移动到 **网页** **Atlas 3 主题的目录**

```
主题/web/login.html
```

这同样适用于您可能创建的额外的 HTML 文档。

Additional static resources such as images or font libraries need to be moved to the **resources** directory of **web** in the **Atlas 3 theme**:

```
主题/网络/资源
```

### 2.4 迁移你的原生样式 {#upgrade-native-styling}

This section can be skipped if you have not made any modifications to the **native** section of your **Atlas 2 theme** and you can continue to the section **migrating your UI content** {#upgrade-ui-content}.

对 **Atlas 2 主题** 的修改包括以下内容：

* 自定义变量的变化
* 添加其他自定义样式
* 设计属性的更改

如果您做出了上述任何修改，请遵循以下步骤。 这些步骤分为四节：

* [原生自定义变量](#native-custom-variables)
* [本地自定义样式](#native-custom-styling)
* [本机插件自定义样式](#native-additional-custom-styling)
* [本地设计属性](#native-design-properties)

#### 2.4.1 本地自定义变量 {#native-custom-variables}

本节涉及您对 **Atlas 2 主题的 **个性变量** js 文件的修改**

```
theme_atlasl2/styles/native/sass/app/custom-variables.js
```

要将您的自定义变量修改移动到 **Atlas 3**, 有两个选项：

**选项1** - 如果自定义变量适用于应用级别 然后修改应移动到 **Atlas 3 主题** 目录的 **自定义变量** scss 文件。

```
主题/本地/自定义变量.js
```

**选项 2** - 如果你想要将变量提取到一个可重复使用的模块， 将它们移动到 **自定义变量** 您在 **主题创建的模块的 scss 文件** 目录。

```
主题/你的模块/本地/自定义变量.js
```

#### 2.4.2 本地自定义样式 {#native-custom-styling}

本节涉及您对您 **Atlas 2 主题的 **个自定义** js 文件** 的修改。

```
theme_atlasl2/styles/native/sass/app/_custom.js
```

要将您的自定义样式修改移动到 **Atlas 3**, 有两个选项：

**选项 1** - 如果自定义样式适用于应用级别 然后修改应该移动到 **Atlas 3 theme** 目录的 **主** js 文件。

```
主题/本地/main.js
```

**Option 2** - If you want to extract the custom styling into a reusable module, move them into the **main** js file of a module you have created in the **themesource** directory.

```
主题/你的模块/本地/main.js
```

#### 2.4.3 原生的成份自定义样式 {#native-additional-custom-styling}

本节涉及您对 **Atlas 2 主题的 **应用程序** 文件夹以及您可能添加的任何额外的 js 样式表** 所作的修改。

```
theme_atlasl2/styles/native/sass/app/_
```

要将您添加到这里的额外样式表移动到 **Atlas 3**，有两个选项：

**选项 1** - 如果附加样式表适用于应用级别 这些更改应该移动到 **web** **Atlas 3 主题的目录**

```
主题/本地/_
```

记得使用 JavaScript `导入` 语法导入 *theme/native/main.js* 并导出导入文件所暴露的变量。

**选项 2** - 如果你想要提取额外的样式表到一个可重复使用的模块， 将它们移动到您在 **主题创建的模块** 中。

```
主题/你的模块/本地/_
```

记住使用JavaScript导入文件 `导入` 语法在 *主题/你的模块/本地/main.js* 并导出导入文件所暴露的变量。

#### 2.4.4 本地设计属性 {#native-design-properties}

This section concerns modifications you have made to the **settings-native.json file** of your **Atlas 2 theme**.

```
theme_atlas2/settings-native.json
```

自定义 **设计属性** ，您已添加到 **设置。 儿子**需要移动到原生的 **设计属性** json 文件中您在 **主题创建的模块** 目录中。

```
主题/你的模块/web/design-properties.json*
```

不要添加到模块 **Atlas Core** 或 **Atlas Native Content**。

如果您有自定义的平台支持或社区支持小部件的设计属性，请参阅下面 [迁移自定义设计属性](#upgrade-design-properties) 部分。

### 2.5 迁移自定义设计属性 {#upgrade-design-properties}

#### 2.5.1 为平台支持的部件添加设计属性

如果您已经扩展了一个或多个支持小部件的设计属性，类似于下面的例子。

您已经扩展了 **个容器部件** 带有设计属性 **边框** 将边框添加到容器的实例中。 注意，对于设计属性来说， `元素` 名称叫做 `离子容器`。

```
{
 "pageTemplates": "WebModeler",
 "cssFiles": ["styles/web/css/main.css"],
 "designProperties": {
  "DivContainer": [
    {
        "name": "Align content",
        "type": "Dropdown",
        "description": "Align content of this element left, right or center it. Align elements                  inside the container as a row or as a column.",
        "options": [
                {
                    "name": "Left align as a row",
                    "oldNames": ["Left align as row"],
                    "class": "row-left"
                },
                {
                    "name": "Center align as a row",
                    "oldNames": ["Center align as row"],
                    "class": "row-center"
                },
                {
                    "name": "Right align as a row",
                    "oldNames": ["Right align as row"],
                    "class": "row-right"
                }
        ]
   },
   {
    "name": "Border", // custom design property targeting the platform's DivContainer
    "type": "Toggle",
    "description": "Add a border.",
    "class": "div-container-border"
   }
  ]
 }
}
```

在上面的示例中，我们有两个设计属性： **对齐内容** 和 **边框**。 对齐内容是Atlas3定义的设计属性，而边界则是自定义的设计属性。 To avoid conflicts with the Atlas 3 defined design properties, its recommended to export only your custom-defined design properties to the web's **design-property** json file of a module you have created in the **themesource** directory. 产生于与下面例子类似的东西。

```
主席:
 "DivContainer": [
  }
   "name": "边框",
   "类型": "切换",
   "描述": "添加边框 ,
   "class": "div-container-border"
  }

}
```

#### 2.5.2 为社区支持的部件添加设计属性

如果您在应用中定义了自己的设计属性为社区支持的小部件设计，类似于下面的示例，请遵循这些步骤。

您在 **Atlas 2** 中为 MyCustomWidget添加了一个设计属性 `“不透明度”`。 如下文在 **settings.json** 文件中所示。

```
{
 "pageTemplates": "WebModeler",
 "cssFiles": ["styles/web/css/main.css"],
 "designProperties": {
  "MyCustomWidget": [
   {
    "name": "Opacity",
    "type": "Dropdown",
    "description": "Emphasize the visual-importance via opacity.",
    "options": [
     {
      "name": "Light",
      "class": "opacity-light"
     },
     {
      "name": "Normal",
      "class": "opacity-normal"
     }
    ]
   }
  ]
 }
}
```

因为这是一个自定义的设计属性， 这需要添加到您在 **主题** 目录中创建的模块的 **设计属性** json 文件。 产生于与下面例子类似的东西。

```
{
 "MyCustomWidget": [
  {
   "name": "Opacity",
   "type": "Dropdown",
   "description": "Emphasize the visual-importance via opacity.",
   "options": [
    {
     "name": "Light",
     "class": "opacity-light"
    },
    {
     "name": "Normal",
     "class": "opacity-normal"
    }
   ]
  }
 ]
}
```

#### 2.5.3 设计属性合并选项

设计属性选项也可以合并到主题模块中。 欲了解更多信息，请参阅 **Design Properties API 文档中其他模块</a> 部分的
扩展或覆盖设计属性</strong>。</p> 



## 3 升级到Atlas后的预期问题 3 {#expected-issues}

当您完成上面的班级时，您的错误列表中可能有错误：

*  对于与重命名的设计属性有关的错误，右键单击一个相关错误并点击 **更新项目中所有重命名的设计属性**：
  
  ![错误](attachments/atlas-mig/4-errors.png)

* 对于关于 **Phone** 或 **平板电脑** 导航配置文件不再存在， 右键单击错误并选择 **转到** 将导航您到指向缺失手机或平板个人资料的小部件 — 使用这些方法之一解决错误：
  
      * 删除布局
    * 删除布局中的部件
    * 将 **电话网页** 或 **平板电脑网页** 导航配置文件添加到您的 Mendix 应用程序
    * 在小部件的属性窗格中，将 **配置文件** 更改为已经存在的配置文件，例如 **响应式网页**
      
      请注意，Mendix 9中的导航配置文件已经改变。 更多信息请参阅 [Mendix 9 版本说明](/releasenotes/studio-pro/9.0)。
      
      ![](attachments/atlas-mig/5-nav.png)

*  如果您正在使用混合电话配置文件， 请点击 **更改您导航配置文件中的配置文件类型** 来确保您将它们更改为对应的 web 配置文件:
  
      * 混合平板电脑离线应用 → 平板电脑离线版
    * 混合平板电脑在线应用 → 平板电脑网络
    * 混合手机应用程序离线→ 手机网关
    * 混合手机应用在线版 → 手机网络
![](attachments/atlas-mig/6-hybrid-phone.png)

*  如果您正在使用徽章、进度圈、进度条或地图部件， 请确保您更新小部件的定义并重新配置每个小部件添加的新属性：
  
  ![](attachments/atlas-mig/7-errors.png)

*  如果您有 **您的主题不支持设计属性X** 错误， 它或是指在Atlas3中删除了一个设计属性，或是您需要按照指示将自己的设计属性添加到新的文件结构中 [迁移自定义的设计属性](#upgrade-design-properties) 上面的部分。 若要抑制错误，请右键单击错误，然后选择 **移除属性**。 要检查如何扩展您的设计属性，请按照 [来扩展设计属性](/howto/front-end/extend-design-properties)。
  
  ![](attachments/atlas-mig/8-errors-background.png)

* 如果您有错误，表示 **未知的设计属性选项X**， 这意味着在Atlas3中删除了设计属性选项。 使用以下方法之一解决错误：
  
      * 将设计属性设置为默认选项：右键单击错误，然后选择 **将属性设置为默认值**
    * 在 *theme_atlas2/settings.json* 网页版和 *theme_atlas2/settings-natic 中搜索设计属性选项的 CSS 类。 儿子* 为本地，然后将其添加到适用的 [部件的样式属性](common-widget-properties#style)
      
      ![](attachments/atlas-mig/9-set-prop.png)

* 如果您说 **Nanoflow commons/Native mobile resources 不兼容** 从 **Marketplace** 获取新的主要版本。



## 4 升级到Atlas后的边缘案例问题 3 {#edge-cases}

在 Mendix 9 中，混合配置文件已废弃。 在Atlas3中，所有混合内容都被删除。 从Atlas2升级到Atlas3时， 您可能会在混合配置文件的默认主页中出现错误：

![](attachments/atlas-mig/10-edge.png)

要解决这个问题，请右键点击错误，然后选择 **转到导航配置文件“HybridPhone”** 并更改默认主页：

![](attachments/atlas-mig/set-hybrid-nav.png)



## 5 故障排除通用Atlas问题 {#troubleshoot}

为了排除常见的图集问题，请做以下操作：

* 如果您有 **布局X 不再存在** 个错误，右键点击错误，然后转到发生错误的页面。 在页面属性中，选择一个新的、适当的布局。
* 如果您有 **则选中的图像 X 不再存在** 个错误， 右键单击错误并转到它发生的页面并选择一个新图像。 根据您的应用，您可能想要下载 **Atlas_NativeMobile_Content** 模块并使用来自模块的图像。
* 如果您有 **所选的占位符 X 不再存在** 个错误， 右键单击错误并转到其发生的页面。然后您有其他选项来纠正错误： 
      * 调整页面使用的布局以包含匹配名称的占位符。
    * 在页面上，将内容移出占位符。



## 6 阅读更多

* [Atlas3 网站](https://www.mendix.com/atlas/)
* [Atlas设计系统应用](https://atlasdesignsystem.mendixcloud.com/)
* [Atlas3 更改摘要](/refguide/atlas3-change-summary)
* [Studio Pro 9 发布笔记](/releasenotes/studio-pro/9.0)
