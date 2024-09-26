---
title: "数据源"
parent: "数据部件"
tags:
  - "studio pro"
  - "数据源"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/data-sources.pdf)。
{{% /报警 %}}

## 1 导言

显示存储在实体中的信息的小部件要求您分配获取相关数据的方法。 这种方法被统称为数据来源。 需要数据源的小部件包括所有 [数据小部件](data-widgets) 和 [输入小部件](input-widgets)。 [插件](/apidocs-mxsdk/apidocs/pluggable-widgets) 也可以使用数据源。

在本文件中，我们描述了数据部件的数据来源。

## 2 个数据视图

数据视图支持以下数据来源：

*   [Context](context-source) - 数据视图从上下文获取对象：或者从页面参数或者从周围的数据容器
*   [Microflow](microflow-source) - 数据视图对象是由调用选定的微流程结果决定的。 微流可以在上下文中将对象作为参数，并且需要返回单个物体。
*   [Nanoflow](nanoflow-source) — — 检索到的对象是通过调用选定的纳诺夫低的结果来决定的。 nanoflow 可以在上下文中将对象作为参数，并且需要返回单个对象。
*   [聆听小部件](listen-to-grid-source) - 数据视图对象取决于列表小部件中的选择(数据网格, 模板网格或列表视图)

{{% alert type="info" %}}

离线应用程序不支持 **Microflow** 源，因为它意味着要拨打服务器。

{{% /报警 %}}

## 3 列表部件 {#list-widgets}

数据网格、模板网格和列表视图是列表部件。 另外，一些 [插件](/apidocs-mxsdk/apidocs/pluggable-widgets) 可能会作为列表小部件并使用数据源。 支持的数据来源如下：

*   [数据库](database-source) - 从数据库中检索对象；数据库约束可以用来限制显示哪些对象。
*   [XPath](xpath-source) - 从数据库中检索对象；XPath 约束可以用来约束显示哪些对象。
*   [Microflow](microflow-source) — — 检索到的对象由调用选定的微流程的结果决定。 微流可以将对象作为参数，并且需要返回对象列表。
*   [Nanoflow](nanoflow-source) — — 检索到的对象是通过调用选定的纳诺夫低的结果来决定的。 nanoflow 可以在上下文中将对象作为参数，并且需要返回对象列表。 Nanoflow 数据源仅适用于数据视图和列表视图。
*   [关联](association-source) - 通过关注对象上下文中的关联从内存中获取物体。 因此，这个数据源只有当一个部件嵌套在另一个数据容器中时才可用。

 数据源还决定该部件的哪些功能已启用。 例如，只有具有数据库或 XPath 数据源的小部件可以包含 [搜索栏](search-bar)。

{{% alert type="info" %}}

数据库和纳米数据源是唯一支持离线的数据源。 如果列表小部件在离线应用程序中有数据库数据源， 数据将来自设备上的数据库。 这个数据库可以与创建一个新对象的 [按钮](button-properties) 小部件。

{{% /报警 %}}

## 4 阅读更多

* [数据部件](data-widgets)
