---
title: "Nanoflow 源"
parent: "数据来源"
tags:
  - "studio pro"
  - "nanoflow 源"
  - "数据源"
menu_order: 50
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/nanoflow-source.pdf)。
{{% /报警 %}}

## 1 导言

**Nanoflow** 数据源用于 [数据视图](data-view) 和 [列表视图](list-view)。

在大多数情况下，您可以使用 *数据库*， *关联* 或 *XPath* 数据源来填写 [数据部件](data-widgets)。 然而，有时目标必须遵守非常具体的标准。 或者不同的对象在无法被 [XPath](xpath-constraints) 处理的不同环境下显示。 在这些情况下，可能需要一个 *nanoflow 数据源*。 欲了解更多关于纳米流量及其优势的信息，请参阅 [Nanoflows](nanoflows)。

当一个带有nanoflow 数据源的数据部件显示或刷新时， 它运行指定的 nanoflow 并显示返回值。 天体的获取方式完全取决于您。 它允许对要返回的对象进行无限控制。

nanoflow 数据源忽略了所有上下文. 它执行nanoflow描述的动作，别的动作。 例如，嵌套数据小部件含有nanoflow 数据源不会自动创建或调用关联到封装数据小部件。

## 2 个Nanoflow 数据源示例

例如，您有一个列表需要显示基于订单类型的潜在订单列表：

![Nanoflow 源](attachments/data-widgets/nanoflow-source.png) 如果 *订单的 *订单类型** 实体已设置为 *汽车*然后，数据网格应该显示所有 *产品* 的布尔值 *摩托化* 设置为 true。 如果 *订单类型* 是 *自行车* 只显示 *摩托化* 的对象为false。 如果 *订单类型* 为空，数据网格应保持为空。

![实体示例](attachments/data-widgets/entities-example.jpg) 由于属性类型不匹配，这不能被 XPath 约束，需要一个 nanoflow 数据源。

使用案例的nanoflow 应该看起来像这样：

![Nanoflow 示例](attachments/data-widgets/microflow-nanoflow-example.jpg) 这种纳米效果如下：

1. 它通过了作为参数的附文数据视图的 *顺序*。

2. 然后在 *orderType* 属性上拆分并检索每个枚举值的不同产品集。

3. nanoflow 返回产品列表，并且每个终端事件都被配置为返回列表。

    {{% alert type="info" %}}The *empty* path also requires a value, where `empty` is also a value.
    {{% /报警 %}}

## 3 属性

### 3.1 纳诺夫low

定义用于装入部件的 nanoflow 。 当小部件被加载到浏览器或刷新时，这个nanoflow 将会运行。 nanoflow 必须有对象或对象列表的返回值，这取决于正在使用的部件。

## 4 阅读更多

* [纳诺夫拉](nanoflows)
* [数据部件](data-widgets)