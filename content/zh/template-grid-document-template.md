---
title: "模板网格(文档模板)"
parent: "文档模板"
tags:
  - "studio pro"
aliases:
  - /refguide8/Template+Grid+(document+template).html
  - /refguide8/template-grid-(document-template).html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/template-grid-document-template.pdf)。
{{% /报警 %}}

## 1 导言

模板网格在磁贴视图中显示对象列表。 例如，模板网格可以显示产品列表。 模板网格与数据网格有很多共同之处。 主要的区别是对象显示在模板中(某种小数据视图)而不是行中。

{{% alert type="info" %}}

![](attachments/document-templates/918137.png)

显示商品名称、描述和图像的模板网格。

{{% /报警 %}}

## 2 个组件

### 2.1 排序条

查看 [排序条](sort-bar)。

## 3 外观属性

### 3.1 启用条纹功能

启用整条后，您可以单独设置偶数和不均衡的模板网格行的内容。 这种方式你可以为两个不同行风格以不同的颜色创建一个切片效果。

### 3.2 栏数

这定义了模板网格将包含的列数。

## 4 个公共属性

{{% snippet file="refguide8/name-property.md" %}}

## 5 数据源属性

数据源属性决定哪些对象将显示在模板网格中。 模板网格中的对象列表受下列机制的限制：

1.  对于顶级模板网格，将显示在调用文档导出操作的微流程中传递的对象。
2.  对于嵌套的模板网格，如果使用实体路径，只显示从包含对象的路径可以访问的对象。
3.  对于嵌套的模板网格，如果使用微流，则显示微流返回的对象。

### 5.1 实体(路径)

实体(路径)属性指定了哪些实体实例将显示在模板网格中。 顶级模板网格总是连接到实体的。 嵌套的模板网格可以连接到一个实体或从包含数据视图的实体开始的实体路径。 实体路径可以跟随社团，而不论其类型和所有权。

### 5.2 微流

当嵌套模板网格连接到实体时，需要微流才能检索数据。 这些微流的输入参数总是包含数据视图的对象，输出是包含嵌套模板网格类型的对象列表。
