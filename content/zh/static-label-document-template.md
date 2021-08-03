---
title: "静态标签 (文档模板)"
parent: "文档模板"
tags:
  - "studio pro"
aliases:
  - /refguide8/Static+label+(document+template).html
  - /refguide8/static-label-(document-template).html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/static-label-document-template.pdf)。
{{% /报警 %}}

## 1 导言

静态标签显示一行静态文本。 您可以使用它来将自定义文本放入数据视图，模板网格或表中。

例如，带有文本“客户名称”的标签将看起来像这样：

![](attachments/document-templates/918130.png)

如果您想在文档中插入当前页码或总页码， 您可以在静态标签中使用令牌(仅在静态标签中使用)。

For example, static label content `Page [%pageNumber%] of [%totalPageCount%]` will print **Page 2 of 4**.

## 2 公共属性

{{% snippet file="refguide8/name-property.md" %}}

## 3 外观属性

### 3.1 标题

这是将显示在文档中的值。

### 3.2 风格

欲了解详情，请见 [样式](style)。
