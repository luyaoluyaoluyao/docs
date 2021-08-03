---
title: "构建块"
parent: "页面"
---

## 1 导言

{{% alert type="info" %}}

编辑和管理自定义建筑块的选项已添加到 Mendix 7.9.0。

{{% /报警 %}}

建筑块是可以用来简化页面创建过程的组件。 通过预配置和样式构建块，用户可以轻松地点击接口，而不必担心样式指南或用户体验的细节。

建筑块存储在项目的 [UI 资源包](ui-resources-package) 中。 这将使它们与项目主题同步，并提供一个便捷的场所来合并所有与设计相关的数据。

要创建一个建筑块，只需右键点击你项目中任何位置的桌面模式模组，并选择 **创建建筑块**。 小部件及其内容将作为一个新的建筑块添加。 The building block will now automatically appear in the **Building blocks** tab of the **Toolbox**.

由于构件的目的是便利设计而不是便利功能，因此构件应不提及其他文件。 这是为了防止用户在其页面中使用建筑块时遇到混淆的错误。 它还可以减少从另一个项目导入构件块时出现错误的可能性。

## 2 公共属性

{{% snippet file="refguide7/Document+Name+Property.md" %}}

{{% snippet file="refguide7/Documentation+Property.md" %}}

## 3 设计师属性

{{% snippet file="refguide7/Canvas+Width+Property.md" %}}

{{% snippet file="refguide7/Canvas+Hight+Property.md" %}}

## 4 个一般属性

### 4.1 显示名称

显示名称决定将出现在工具箱中的建筑块名称。

### 4.2 图像

选中的图像将会出现在 **Building Blocks** 标签上 Web Modeler **Toolbox** 中。 选择一个具有代表性的图像将使用户能够轻松区分不同的构件。 如果留空，Web Modeler将显示一个通用默认图像。 所选图像将缩放到 200x200 像素。

### 4.3 文件网址

<div class="alert alert-info">
此功能已添加到桌面Moderr 版本7.17。
</div>

文档URL可以用来链接到构建块的文档页面。 这些链接将会出现在 Web Modeler的 **Building Blocks** 标签页 **Toolbox** 中。
