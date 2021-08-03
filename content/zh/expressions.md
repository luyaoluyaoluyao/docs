---
title: "表达式"
menu_order: 55
description: "描述Mendix Studio中可用的微流表达式。"
tags:
  - "工作室"
  - "微流"
  - "表达式"
  - "表达式"
  - "设置值"
  - "变量"
aliases:
  - /studio/microflows-expressions.html
---

## 1 导言

表达式会根据函数或函数组合改变一个值。

您可以对工作流、页面和微流使用表达式。 表达式通常用于设置某个活动或属性的条件 例如，微流程或工作流程中的决定条件。

您可以在工作流中使用以下元素的表达式：

* [决 定](workflows-general-activities)
* **到期日期** 属性为 [工作流程](workflow-properties) 和 [用户任务](workflows-user-task)

表达式可以在以下页面属性中使用：

* 部件的条件可编辑
* 部件的条件可见性
* **一个 [文本部件的内容</strong> 属性](page-editor-widgets-text)</li> </ul>

在微流中可以使用下列表达式：

*  更改对象
*  更改变量
*  创建对象
*  创建变量
*  [决 定](microflows-decision)
*  结束事件

更多关于微流活动的设置和改变价值的信息 查看 [设置 & 更改微流中不同活动的值](microflows-setting-and-changing-value)

## 2 正在写入表达式

在微流和工作流中命名的项目 (例如对象、列表和工作流) 可以在表达式中插入项目名称并添加一个美元标志(例如)  `$Customer` 可以引用名为 `客户` 的对象。

使用斜线访问对象的属性和关联性 (例如) 客户对象的 **名称** 属性被称为 `$Customer/名称`。

您可以使用括号来确定计算的优先级和关联性。 For example, the **SellingPrice** is being calculated based on the default **Price** and **Discount** attributes:

```
$CurrentPrice/Price - (($CurrentPrice/Price **div** 100) * $OrderLine/Discount)
```

此处合并了算术功能（减去、分割和乘数）。

您不能在表达式中输入纯文本，文本需要用单引号 (`'`)来写。 例如，如果你想要返回字符串 `Mendix`, 你需要把它写成 `'Mendix'`。

您可以使用建议列表来帮助您写一个表达式。 使用 <kbd>Ctrl</kbd> + <kbd>空格</kbd> 快捷键来显示此列表。 建议可分为以下几类：

* **变量及其属性** -- 在当前微流程、页面或工作流中可用的变量或属性
* **枚举值** - 可用于表达式的 [枚举类型属性](domain-models-enumeration) 的值
* **函数** - 您可以在表达式中使用的操作(详细信息，请参阅 [表达式类型](#expression-types) 下文部分)
* **关键字** -- 您可以在表达式中使用的关键词或单词 (例如，) `空` - 可用来检查变量是否为空的值
* **布尔值** -- 真或假关键字
* **运算符** - 执行逻辑或数学操作的代码元素； 您可以使用布尔值或关系表达式(详细信息，参见 [表达式类型](#expression-types) 下面部分)

如果表达式中存在错误，则错误发生地： 高亮显示红色，当你悬停在它时会显示错误消息。  在某些情况下，有快速解决问题的办法。

![](attachments/expressions/expression-error.png)


### 2.3 表达式实例

说明如何使用表达方式的例子如下。

#### 2.3.1 例1

您在微流中有一个 [Decision](microflows-decision) ，您想要写一个表达式来检查客户等级是否为黄金和订单价格是否超过 100 (您可以在 **Decision** 之后配置折扣，如果此表达式为真的话：

![](attachments/expressions/example-decision.png)

表达式将显示如下方式：

![](attachments/expressions/expression-decision.png)

#### 2.3.2 例2

您将 [决定](microflows-decision) 添加到微流程中，以检查对象是否存在(在下面的示例是 *客户*) 您还要检查客户的名字是否与某个特定的名字相符(在下面的例子中，客户的名字是 *Mendix*)。 表达式将显示如下方式：

![](attachments/expressions/customer-empty-and-name-example.png)

#### 2.3.3 例3

您在 Workflow 中有一个 [用户任务](workflows-user-task) ，并想添加 **到期日** 作为提醒，用户任务应在明天后一天完成。 您可以为它写下以下表达式：

![用户任务表达式](attachments/expressions/user-task-due-date.png)

## 3 个表达式类型 {#expression-types}

在工作室中使用最多的表达式列表如下所示。 关于可用表达式的完整列表, 见 [表达式](/refguide/expressions) 在 *Studio Pro 指南* 中。

### 3.1 异常表达式

* [Unary 减去( - )](/refguide/unary-expressions)

### 3.2 算术表达式

* [乘法( * )](/refguide/arithmetic-expressions)
* [Division ( div or : )](/refguide/arithmetic-expressions)
* [Modulo ( mod )](/refguide/arithmetic-expressions)
* [添加 ( + )](/refguide/arithmetic-expressions)
* [减法 ( - )](/refguide/arithmetic-expressions)

### 3.3 关系表达式

* [小于 ( <)](/refguide/relational-expressions)
* [大于 ( >)](/refguide/relational-expressions)
* [小于或等于 ( <= )](/refguide/relational-expressions)
* [大于或等于 ( >= )](/refguide/relational-expressions)
* [等于 ( = )](/refguide/relational-expressions)
* [不等于 ( != )](/refguide/relational-expressions)

### 3.5 布尔表达式

* [和](/refguide/boolean-expressions)
* [或](/refguide/boolean-expressions)
* [不是](/refguide/boolean-expressions)

### 3.6 数学函数调用

* [`最大`](/refguide/mathematical-function-calls) - 数字列表的最大值
* [`分钟`](/refguide/mathematical-function-calls) - 数字列表的最小值
* [``](/refguide/mathematical-function-calls) — — 一个数字回合到一定的精度
* [`随机`](/refguide/mathematical-function-calls) - 随机生成数字
* [`floor`](/refguide/mathematical-function-calls) - 下一个浮点数的四舍五入
* [`ceil`](/refguide/mathematical-function-calls) - 浮点数向上四舍五入
* [`pow`](/refguide/mathematical-function-calls) - 指数化
* [`abs`](/refguide/mathematical-function-calls) - 绝对值

### 3.7 字符串函数调用

* [`toUpperCase`](/refguide/string-function-calls) — — 将字符串转换为大写。
* [`toLowerCase`](/refguide/string-function-calls) — — 将字符串转换为小写
* [`长度`](/refguide/string-function-calls) - 字符串长度
* [`子字符串`](/refguide/string-function-calls) — — 获取字符串的一部分。
* [`查找`](/refguide/string-function-calls) - 获得一个子字符串位置
* [`查找最后`](/refguide/string-function-calls) — 获取最后一个子字符串位置
* [`包含`](/refguide/string-function-calls) — — 包含子字符串
* [`起点`](/refguide/string-function-calls)  - 决定字符串是否以指定的子字符串开始
* [`endsWithout`](/refguide/string-function-calls) - 决定一个字符串是否以指定的子字符串结束
* [`修剪`](/refguide/string-function-calls) - 删除前导和尾随的空格
* [`替换所有`](/refguide/string-function-calls) - 替换子字符串的事件
* [`替换第一个`](/refguide/string-function-calls) - 替换第一个子字符串的出现时间
* [`字符串汇合( + )`](/refguide/string-function-calls) - 连接字符串字符串

### 3.8 创建日期

* [`日期时间`](/refguide/date-creation) - 使用服务器的日历创建日期值

### 3.9 日期间函数调用间隔

* [`毫秒之间`](/refguide/between-date-function-calls) - 两个日期之间的毫秒
* [`秒之间`](/refguide/between-date-function-calls) - 两个日期之间的秒数
* [`分钟间隔`](/refguide/between-date-function-calls) - 两个日期之间的分钟
* [`小时之间`](/refguide/between-date-function-calls) - 两个日期之间的小时
* [`天之间`](/refguide/between-date-function-calls) - 两个日期之间的天数
* [`周之间`](/refguide/between-date-function-calls) - 两个日期之间的周
* [`日历月间`](/refguide/between-date-function-calls) - 两个日期之间的月
* [`日历年之间`](/refguide/between-date-function-calls) - 两个日期之间的年份

### 3.10 添加日期功能调用

* [`addMilliseconds`](/refguide/add-date-function-calls) — 添加毫秒到某个日期
* [`addonds`](/refguide/add-date-function-calls) — — 添加秒到某一日期
* [`添加分钟`](/refguide/add-date-function-calls) — 添加分钟到一个日期
* [`添加小时`](/refguide/add-date-function-calls) — 添加小时到某个日期
* [`添加天`](/refguide/add-date-function-calls) - 给日期添加天数
* [`添加周`](/refguide/add-date-function-calls) - 将周添加到某个日期
* [`添加月`](/refguide/add-date-function-calls) — 添加月到某个日期
* [`添加年份`](/refguide/add-date-function-calls) — 添加年份到日期

### 3.11 解析 & 格式十进制函数调用

* [`格式小数`](/refguide/parse-and-format-decimal-function-calls) — 将小数转换为字符串

## 4 阅读更多

* [微型流动](微流)
* [工作流](workflows)
* [设置 & 更改微流中不同活动的值](microflows-setting-and-changing-value)
* [表达式](/refguide/expressions)
