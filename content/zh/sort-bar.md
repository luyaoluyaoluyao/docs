---
title: "排序条"
parent: "格子"
menu_order: 50
tags:
  - "studio pro"
  - "排序栏"
  - "网格"
aliases:
  - /refguide/Sort+Bar.html
---

## 1 导言

一个排序条允许最终用户在 [数据网格](data-grid)中排序项目 [模板网格](template-grid) 或 [引用设置选择器](reference-set-selector)。

排序条包含排序项目。 每个排序项指定了哪个属性排序和方向(升序或降序)。 首先，格子的内容按第一个项目排列。 如果两行在这类项目上是相同的，将使用第二个项目，等等。 例如，如果你有按名称和年龄排序的项目，并且两个人有相同的名字，他们将按年龄排序。

如果您没有指定任何类型的项目，对象将会出现在创建对象的顺序中。

{{% alert type="info" %}}
有特殊情况可以排序行为。 欲了解更多详情，请参阅 [按行为排序](ordering-behavior)。
{{% /报警 %}}

## 2 次阅读更多

* [数据网格](数据网格)
* [模板网格](template-grid)
* [参考设置选择器](reference-set-selector)
