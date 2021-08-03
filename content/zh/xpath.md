---
title: "XPath"
category: "应用程序模型"
menu_order: 90
description: "描述在 Mendix 中如何使用的 XPath 查询语言，通过介绍函数和示例。"
tags:
  - "studio pro"
---

## 1 导言

Mendix XPath 是用于检索数据的 Mendix 查询语言之一。 XPath 使用路径表达式选择Mendix 对象及其属性或关联的数据。

XPath 查询可以同时写入 Studio Pro， 例如，当您想要指定在检索微流程活动中检索到的数据时， 并且直接在 *中的代码。 您的 Java 操作的* 文件。 请注意，并非所有运营商都被 Studio Pro支持，您查询的语法可能在 Studio Pro 和 Java 环境中不同。

XPath 查询的示例是：

*   `//销售.客户` 检索所有客户。
*   `//Sales.Customer[name='Jansen']` 检索所有名为 'Jansen' 的客户
*   `avg(//Sales.Order[IsPaid = true()]/TotalPrice` 检索所有支付订单总价格的平均值。

{{% alert type="warning" %}}
在 Studio Pro，您不会写完整的查询，仅限限制。 实体是由上下文隐含地确定的。 因此，取代 `//Sales.Customer[Name='Jansen'`, 你只需要在客户上写 `[Name='Jansen' ]`。 在 Java 中，您确实需要写整个查询，包括双斜线 (`//`) 和实体名称。
{{% /报警 %}}

## 2 XPath 元素

常见的 Mendix XPath 查询由几个元素组成。

| A        | B           | C                | D           |
| -------- | ----------- | ---------------- | ----------- |
| 聚合函数(可选) | 要检索的实体 (必须) | 约束(可选)           | 要检索的属性 (可选) |
| 八克       | //Sales.订单  | [Isaid = true()] | / 总价格       |

要件B说明每个查询的核心，并包括被检索对象的说明。 此段总是以两个转向斜线“//”开头，并包含您想访问的实体的名称，前面包含一个期间隔开的实体模块。 例如： //Sales.客户将返回模块“销售”中的所有实体“客户”的对象。

查询的元素C是可选的，包含一个或多个限制因素来限制检索数据。

请考虑以下查询：

`//Sales.Customer[name='Jansen']`

约束在方括号之间明显可见，并限制检索到属性“名称”等于'Jansen'的对象。 除Jansen以外的任何其他名称的对象都被排除在列表之外。 单个查询可能受到的限制数量是无限的。 关于如何添加和操纵这些制约因素的更多信息，请参阅 [XPath 制约](xpath-constraints)。

查询的元素D是可选的，并指定被检索实体的属性。 此选项在Studio Pro本身中很少使用，因为所有数据都存储在物件中。 使单一属性列表变得繁琐和不必要的复杂。 但是，各种爪哇行动都使用这种清单。 而且，这一功能可以与A部分一起使用，以容易地创建某些属性的总合。

查询的元素A是可选的，并指定了一个聚合。 元素A可以是以下函数之一： [avg](xpath-avg), [count](xpath-count), [最大](xpath-max), [分钟](xpath-min) 和 [金额](xpath-sum) 除“计数”外，每个函数都要求元素D中指定一个特定属性。

## 3 个令牌

欲了解详情，请参阅 [XPath Tokens](xpath-tokens)。

## 4 个运算符

欲了解详情，请参阅 [XPath 操作员](xpath-operators)。

## 5 职能

以下XPath 功能可用：

* [XPath 函数](xpath-query-functions):
    * [八克](xpath-avg)
    * [计数](xpath-count)
    * [最大值](xpath-max)
    * [分钟](xpath-min)
    * [sum](xpath-sum)
* [约束函数](xpath-constraint-functions):
    * [包含](xpath-contains)
    * [开始于](xpath-starts-with)
    * [结束于](xpath-ends-with)
    * [不是](xpath-not)
    * [true](xpath-true)
    * [false](xpath-false)

## 6 个示例

**如何找到正确的 XPath 路径**

{{% alert type="info" %}}
此视频是用 [Studio Pro 8](/refguide8/)完成的，但概念仍然适用。
{{% /报警 %}}

{{% youtube sdabUY-w4ZU %}}
