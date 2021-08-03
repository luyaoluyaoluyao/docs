---
title: "样式"
parent: "文档模板"
tags:
  - "studio pro"
---

## 1 导言

在大多数文档模板部件和组件以及顶级文档中，可以定义样式。 此样式是在连铸样式表(CSS)中设计的。 然而，许多比较常见的样式属性可以使用样式编辑器进行调整。 取决于您的小部件类型，您将在样式编辑器中看到不同的选项。 您也可以完全自定义标签“自定义样式”中的样式。

## 2 Tab Pages

### 2.1 Font

字体标签页面可见的部件/组件：

*   文档模板
*   数据网格
*   数据网格单元格
*   动态标签
*   标题
*   静态标签
*   表

{{% alert type="info" %}}

![](attachments/core/2018-03-01_14-27-27.png)

样式编辑器中的字体标签页。

{{% /报警 %}}

如果您想以阿拉伯语或泰语等不常见字符的语言显示文本， 请确保您在样式编辑器中选择支持这些字符的字体。

### 2.2 单元格样式

单元格样式标签页可见的部件/组件：

*   数据网格
*   数据网格单元格
*   标题
*   表
*   表格单元格

{{% alert type="info" %}}

![](attachments/core/2018-03-01_14-29-13.png)

样式编辑器中的单元格样式标签页。

{{% /报警 %}}

### 2.3 Custom Styles

自定义样式选项卡页面总是对允许搭配的部件/组件可见。

{{% alert type="info" %}}

![](attachments/core/2018-03-01_14-33-46.png)

样式编辑器中的自定义样式标签页。

{{% /报警 %}}

## PDF 文档的3个自定义字体 {#custom-fonts}

You can include custom fonts in your generated documents by simply using a custom style, for example you'd include _font-family: Verdana;_ in your style to make the text appear in Verdana font. 然而，要生成PDF文件，需要做一些额外工作。 下面的章节将教你如何做到这一点。

PDF 生成器可以通过编辑负责生成 PDF 文件的库的配置文件来设置自定义字体。 您可以在子文件夹/runtime/lib中的 Mendix 安装文件夹中找到此文件。 文件名为 fop.xconf。 为了让您更容易更新您的 Mendix 版本或部署您的应用程序，强烈建议您不要直接编辑此文件，而是将其复制到您的应用资源文件夹。 当此文件存在于您的资源文件夹中，运行时将自动访问它，而不是默认文件。

当你有围栏时。 conf 文件和资源文件夹中的所有字体，您可以将您想要使用的字体添加到文件夹中。 接下来，在文本编辑器中打开 fop.xconf 文件。 配置文件使用XML格式。

若要添加您自己，请使用以下设置：

```java

<font kerning="yes" embed-url="mycustomfont.ttf">
    <font-triplet name="myfont" style="normal" weight="normal"/>
</font>
```

嵌入网址是库可以找到字体文件的地方。 字体名称是您在自定义css样式中使用的名称。 您自己的自定义字体的名称必须是小写的。

如果您想要使用斜体或粗体字，您也需要指定它。 例如：

```java
<font kerning="yes" embed-url="mycustomfontinbold.ttf">
   <font-triplet name="myfont" style="normal" weight="bold"/>
</font>

<font kerning="yes" embed-url="mycustomfontinitalic.ttf">
   <font-triplet name="myfont" style="italic" weight="normal"/>
</font>

<font kerning="yes" embed-url="mycustomfontinboldanditalic.ttf">
   <font-triplet name="myfont" style="italic" weight="bold"/>
</font>
```

最后，您的设置应该看起来像这样：

* *fop.xconf* 文件，您的自定义字体和6个默认字体应该在您的应用资源文件夹中
* *fop.xconf* 文件应该包含一个对您自定义字体的引用
