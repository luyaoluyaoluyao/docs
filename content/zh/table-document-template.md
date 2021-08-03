---
title: "表 (文档模板)"
parent: "文档模板"
aliases:
  - /refguide8/table-(document-template).html
  - /refguide8/Table+(document+template.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/table-document-template.pdf)。
{{% /报警 %}}

## 1 导言

表格可以用来更改表单的布局。 它们有若干行和栏目，两者的交点被称为一个间。 每个单元格可以包含部件。 单元格可以横向和纵向合并，允许非对称布局。

表格可以在数据视图内外或模板类部件使用。

{{% alert type="info" %}}

![](attachments/document-templates/918134.png)

本表有四行和三栏。 最后一行包含另一个表的数据视图。

{{% /报警 %}}

## 2 个组件

### 2.1 列

表中的一栏。

### 2.2 行

表中的一行。 查看 [行 (文档模板)](row-document-template)。

## 3 外观属性

### 3.1 权重

列重量是以确定列宽度的半冒号隔开的百分比。 重量必须增加到 100\。 改变列宽度的另一种方法是拖动列之间的分隔线。

{{% alert type="info" %}}

在上面的屏幕截图中，表格的列权重是 `25;25;50`。

{{% /报警 %}}

### 3.2 单元格间距

单元格间距指定单元格间距。

### 3.3 Cell Padding

单元格填充指定单元格内容和单元格墙之间的空间。

### 3.4 样式

欲了解详情，请见 [样式](style)。

## 4 个公共属性

{{% snippet file="refguide8/name-property.md" %}}
