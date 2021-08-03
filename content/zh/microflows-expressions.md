---
title: "微流程表达式"
category: "微型流动"
menu_order: 40
description: "描述Mendix Studio中可用的微流表达式。"
tags:
  - "工作室"
  - "微流"
  - "设置值"
  - "变量"
---

## 1 导言

本文档描述Mendix Studio中的微流程表达式。 表达式可以用来创建或更改基于逻辑的对象或变量。

**表达式** 标签对于微流程中的以下活动是可用的：

*  [结束事件](/refguide/end-event)
*  [决 定](microflows-decision)
*  [创建对象](/refguide/create-object)
*  [更改对象](/refguide/change-object)
*  [创建变量](/refguide/create-variable)
*  [更改变量](/refguide/change-variable)

![](attachments/microflows-expressions/expression-tab.png)

更多关于微流活动的设置和改变价值的信息 查看 [如何设置 & 更改微流中不同活动的值](microflows-setting-and-changing-value)。

## 2 正在写入表达式

有两种写表达式的方式：

* 使用建议
* 手动写入表达式

如果表达式中出现错误，则会显示含有解释的提示。

{{% image_container width="350" %}}![](attachments/microflows-expressions/expression-error.png)
{{% /image_container %}}

### 2.1 使用建议书写表达式

当您开始输入您的表达式时，建议列表似乎分为以下类别：

* **来自您微流程的建议** - 您在微流程中创建或检索的变量或属性
* **枚举值** - 可用于表达式的 [枚举类型属性](domain-models-enumeration) 的值
* **关键字** -- 您可以在表达式中使用的关键词或单词
* **布尔值** -- 真或假表达式
* **运算符** - 执行逻辑操作或数学操作的代码元素。 您可以使用布尔值或关系表达式(详细信息，参见下面 [表达式类型](#expression-types) 部分)

![](attachments/microflows-expressions/expressions-list.png)

要使用建议书写表达式，请执行以下操作：

1. 浏览建议列表并用鼠标或键盘选择表达式的元素。
2. 从列表中选择一个元素。
4. 当表达式完成时点击 **添加**。

{{% alert type="info" %}}

要调用建议清单，请按 <kbd>Ctrl</kbd> + <kbd>空格</kbd>

{{% /报警 %}}

### 2.2 手动写入表达式

如果您想手动写下表达式，请注意：

* 微流中的变量可以通过在变量名称之后插入美元符号来调用表达式。 例如， *$Customer* 提到了变量 *客户*
* 使用斜线访问对象变量的属性和关联性。 例如， *$Customer/name*, *$Customer/级别* 指实体客户的属性名称和等级
* Unit, Boolean, and relational types of expressions are available in Studio (for more information, see [Expression type](#expression-types) section)

## 3 表达式示例

下面有两个例子说明如何使用表达方式。

### 3.1 例1

您有一个 **[Decision](microflows-decision)** 并且您想要写一个表达式来检查客户等级是否为黄金和订单价格是否超过 100 (您可以在 **Decision** 之后配置折扣，如果此表达式为真的话：

![](attachments/microflows-expressions/example-decision.png)

表达式将显示如下方式：

![](attachments/microflows-expressions/expression-decision.png)

### 3.2 例2

您添加了一个 **[Decision](microflows-decision)** 来检查对象是否存在(下面的示例是 *客户*) 您还要检查客户的名字是否与某个特定的名字相符(在下面的例子中，客户的名字是 *Mendix*)。 表达式将显示如下方式：

![](attachments/microflows-expressions/customer-empty-and-name-example.png)

## 4 个表达式类型 {#expression-types}

您可以在Studio中使用表达式的操作员列表如下：

### 4.1 关系表达式

* [小于 ( <)](/refguide/relational-expressions)
* [大于 ( >)](/refguide/relational-expressions)
* [小于或等于 ( <= )](/refguide/relational-expressions)
* [大于或等于 ( >= )](/refguide/relational-expressions)
* [等于 ( = )](/refguide/relational-expressions)
* [不等于 ( != )](/refguide/relational-expressions)

### 4.2 布尔表达式

* [和](/refguide/boolean-expressions)
* [或](/refguide/boolean-expressions)

## 5 阅读更多

* [微型流动](微流)
* [设置 & 更改微流中不同活动的值](microflows-setting-and-changing-value)
