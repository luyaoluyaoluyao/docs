---
title: "静态标签 (文档模板)"
parent: "文档模板"
aliases:
  - /refguide7/Static+label+(document+template).html
  - /refguide7/static-label-(document-template).html
---


静态标签显示一行静态文本。 您可以使用它来将自定义文本放入数据视图，模板网格或表中。

{{% alert type="info" %}}

![](attachments/819203/918130.png)] 一个带文本“客户名称”的标签。

{{% /报警 %}}

如果您想在文档中插入当前页码或总页码， 您可以在静态标签中使用令牌(仅在静态标签中使用)。 在版本 2.5.4 之前，空格会自动插入到令牌的两边。 情况已经不再如此。

{{% alert type="info" %}}

静态标签内容： [%totalPageCount%]页面 [%pageNumber%] 将打印：4 页中的页 2

{{% /报警 %}}

## 公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

## 外观属性

### 标题

这是将显示在文档中的值。

### 样式

查看 [样式](style)
