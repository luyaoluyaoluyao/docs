---
title: "数据网格 (文档模板)"
parent: "文档模板"
tags:
  - "studio pro"
aliases:
  - /refguide8/Data+Grid+(document+template).html
  - /refguide8/data-grid-(document-template).html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/data-grid-document-template.pdf)。
{{% /报警 %}}

## 1 导言

数据网格显示一个网格中的对象列表。 例如，数据网格可以显示客户发出的所有订单。

{{% alert type="info" %}}

![](attachments/document-templates/918138.png)

显示带有描述和被引用的客户名称的订单列表的数据表。

{{% /报警 %}}

## 2 个组件

### 2.1 列

查看 [列 (文档模板)](columns-document-template)。

### 2.2 排序条

查看 [排序条](sort-bar)。

## 3 外观属性

### 3.1 列权重

列重量是以确定列宽度的半冒号隔开的百分比。 重量必须增加到 100\。 改变列宽度的另一种方法是拖动列之间的分隔线。

{{% alert type="info" %}}
列加权数在屏幕上方的截图中为50;25;25。
{{% /报警 %}}

### 3.2 单元格间距

单元格间距指定单元格间距

### 3.3 Cell Padding

单元格填充指定单元格内容和单元格墙之间的空间

### 3.4 启用 Striping

使用条纹启用后，您可以单独设置甚至不均衡的数据网格行的属性。 这种方式你可以为两个不同行风格以不同的颜色创建一个切片效果。

### 3.5 样式

查看 [样式](style)

## 4 个公共属性

### 4.1 名称

部件的内部名称。 你可以使用这个给小部件提供合理的名称。 名称属性也出现在生成的 HTML：小部件DOM 元素自动包含类 '`mx-name-{NAME}`', 可以用于 [Selenium 测试](/howto8/integration/selenium-support)

## 5 数据源属性

数据源属性决定哪些对象将显示在数据网格中。 数据网上的对象清单受到下列机制的限制：

1.  对于顶层数据网格，显示调用文档导出操作的微流程中传递的对象。
2.  对于嵌套的数据网格，如果使用实体路径，只显示从包含对象的路径可以访问的对象。
3.  对于嵌套的数据网格，如果使用微流，则显示微流返回的对象。

### 5.1 实体(路径)

实体(路径)属性指定将在数据网格中显示哪些实体实例。 顶级数据网格总是连接到实体的。 嵌套的数据网格可以连接到一个实体，也可以连接到从包含数据视图的实体开始的实体路径。 实体路径可以跟随社团，而不论其类型和所有权。

### 5.2 微流

当嵌套的数据网格连接到模板时，需要微流才能检索数据。 这些微流的输入参数总是包含数据视图的对象，输出是嵌套数据网格类型的对象列表。
