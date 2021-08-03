---
title: "表达式"
parent: "应用逻辑："
menu_order: 30
description: "描述可以用于多种目的的 Mendix 表达式(例如) 根据逻辑更改对象的成员)。"
tags:
  - "studio pro"
  - "表达式"
  - "微流程表达式"
aliases:
  - /refguide/microflow-expressions.html
---

## 1 导言

表达式会根据函数或函数组合改变一个值。

命名项目 (例如对象、列表) 可以在表达式中插入项目名称并添加一个美元标志(例如)  `$customer` 可以引用名为 `客户` 的对象。

使用斜线访问对象的属性和关联性 (例如) 客户对象的 **名称** 属性被称为 `$customer/名称`和 **CRM。 ustomer_order** 客户对象的关联被称为 `$customer/CRM.Customer_Order`

关联对象的属性可以使用多个斜线访问(例如) 单个关联的 **编号** 属性 **CRM。 rder** 被称为 `$customer/CRM.Customer_order/CRM.Order/Number`。

您可以在表达式中合并函数。 在这种情况下，您可以使用括号来确定计算的优先级和关联性。 For example, the **SellingPrice** is being calculated based on the default **Price** and **Discount** attributes:

```
$CurrentPrice/Price - (($CurrentPrice/Price **div** 100) * $OrderLine/Discount)
```

此处合并了算术功能（减去、分割和乘数）。

### 1.1 示例

For example, you have an object called **package** with two attributes: `weight` (decimal) and `shippingCosts` (decimal). 如果包件重量小于一公斤，则没有运费。 否则，运费为5.00欧元。 更改 `配送成本` 属性的表达式是：

```
如果 $package/权重 < 1.00 到 0.00 否则5.00`
```

### 1.2 正则表达式

[正则表达式](regular-expressions) 资源文档不能用于表达式。 However, the format of regular expressions, sub-expressions, and quantifiers used in regular expression strings is the same as the ones described in the [Expression](regular-expressions#expression) section of *Regular Expressions*.

## 2 单词表达式

* [Unary 减去( - )](unary-expressions)

## 3 算术表达式

* [乘法( * )](arithmetic-expressions)
* [Division ( div or : )](arithmetic-expressions)
* [Modulo ( mod )](arithmetic-expressions)
* [添加 ( + )](arithmetic-expressions)
* [减法 ( - )](arithmetic-expressions)

## 4 关系表达式

* [小于 ( <)](relational-expressions)
* [大于 ( >)](relational-expressions)
* [小于或等于 ( <= )](relational-expressions)
* [大于或等于 ( >= )](relational-expressions)
* [等于 ( = )](relational-expressions)
* [不等于 ( != )](relational-expressions)

## 5 次特殊检查

* [正在检查一个空对象](special-checks)
* [检查空对象成员](special-checks)
* [`是新`](special-checks) - 检查对象是否是新对象

## 6 个布尔表达式

* [和](boolean-expressions)
* [或](boolean-expressions)
* [不是](boolean-expressions)

## 7 如果表达式

* [if](if-expressions) — — 执行一个条件操作

## 8 数学函数调用

* [`最大`](mathematical-function-calls) - 数字列表的最大值
* [`分钟`](mathematical-function-calls) - 数字列表的最小值
* [`环`](mathematical-function-calls) - 一个浮点数的四舍五入，可选为指定精度
* [`随机`](mathematical-function-calls) - 随机生成数字
* [`floor`](mathematical-function-calls) - 下一个浮点数的四舍五入
* [`ceil`](mathematical-function-calls) - 浮点数向上四舍五入
* [`pow`](mathematical-function-calls) - 指数化
* [`abs`](mathematical-function-calls) - 绝对值

## 9 字符串函数调用

* [`toUpperCase`](string-function-calls) — — 将字符串转换为大写。
* [`toLowerCase`](string-function-calls) — — 将字符串转换为小写
* [`长度`](string-function-calls) - 字符串长度
* [`子字符串`](string-function-calls) — — 获取字符串的一部分。
* [`查找`](string-function-calls) - 获得一个子字符串位置
* [`查找最后`](string-function-calls) — 获取最后一个子字符串位置
* [`包含`](string-function-calls) — — 包含子字符串
* [`起点`](string-function-calls)  - 决定字符串是否以指定的子字符串开始
* [`endsWithout`](string-function-calls) - 决定一个字符串是否以指定的子字符串结束
* [`修剪`](string-function-calls) - 删除前导和尾随的空格
* [`isMatch`](string-function-calls) - 匹配正则表达式
* [`替换所有`](string-function-calls) - 替换子字符串的事件
* [`替换第一个`](string-function-calls) - 替换第一个子字符串的出现时间
* [`字符串汇合( + )`](string-function-calls) - 连接字符串字符串
* [`urlEncode`](string-function-calls) — — 转换一个字符串用于一个 URL
* [`urlDecode`](string-function-calls) — — 转换一个字符串从 URL

## 10 日期创建

* [`日期时间`](date-creation) - 使用服务器的日历创建日期值
* [`dateTimeUTC`](date-creation) — 使用 UTC 日历创建日期值

## 11 日期间函数调用间隔

* [`毫秒之间`](between-date-function-calls) - 两个日期之间的毫秒
* [`秒之间`](between-date-function-calls) - 两个日期之间的秒数
* [`分钟间隔`](between-date-function-calls) - 两个日期之间的分钟
* [`小时之间`](between-date-function-calls) - 两个日期之间的小时
* [`天之间`](between-date-function-calls) - 两个日期之间的天数
* [`周之间`](between-date-function-calls) - 两个日期之间的周
* [`日历月间`](between-date-function-calls) - 两个日期之间的月
* [`日历年之间`](between-date-function-calls) - 两个日期之间的年份

## 12 添加日期函数调用

* [`addMilliseconds`](add-date-function-calls) — 添加毫秒到某个日期
* [`addonds`](add-date-function-calls) — — 添加秒到某一日期
* [`添加分钟`](add-date-function-calls) — 添加分钟到一个日期
* [`添加小时`](add-date-function-calls) — 添加小时到某个日期
* [`添加天`](add-date-function-calls) - 给日期添加天数
* [`添加 DaysUTC`](add-date-function-calls) - 使用 UTC 日历添加日期
* [`添加周`](add-date-function-calls) - 将周添加到某个日期
* [`添加 WeeksUTC`](add-date-function-calls) - 使用 UTC 日历将周添加到日期
* [`添加月`](add-date-function-calls) — 添加月到某个日期
* [`addMonthsUTC`](add-date-function-calls) - 使用 UTC 日历给日期添加月数
* [`添加年份`](add-date-function-calls) — 添加年份到日期
* [`添加 YearsUTC`](add-date-function-calls) - 使用 UTC 日历添加日期

## 13 修剪到日期

* [`trimToSeconds`](trim-to-date) - 间隔秒数
* [`修剪分钟`](trim-to-date) - 修剪到分钟
* [`修剪小时`](trim-to-date) — — 修剪到小时
* [`trimToHoursUTC`](trim-to-date) - 使用 UTC 日历的间隔时间
* [`三天`](trim-to-date) — — 每隔几天
* [`trimToDaysUTC`](trim-to-date) — — 每隔几天使用 UTC 日历
* [`三个月`](trim-to-date) — — 每隔几个月
* [`trimToMonthsUTC`](trim-to-date) — — 每隔几个月使用 UTC 日历
* [`三个年份`](trim-to-date) — — 每隔几年
* [`修剪YearsUTC`](trim-to-date) - 使用UTC 日历的年数

## 14 到字符串

详情见 [至字符串](to-string)。

## 15 分析整数

详情请参阅 [分析整数](parse-integer)

## 16 解析 & 格式小数位函数调用

* [`解析小数点`](parse-and-format-decimal-function-calls) - 将字符串转换为小数
* [`格式小数`](parse-and-format-decimal-function-calls) — 将小数转换为字符串

## 17 解析 & 格式日期函数调用

* [`解析日期时间[UTC]`](parse-and-format-date-function-calls) - 将字符串转换为日期值
* [`格式日期时间[UTC]`](parse-and-format-date-function-calls) - 将日期值转换为字符串
* [`格式化时间[UTC]`](parse-and-format-date-function-calls) - 将日期值的时间部分转换为字符串
* [`格式日期[UTC]`](parse-and-format-date-function-calls) - 将日期值的日期部分转换为字符串。
* [`dateToEpachh`](parse-and-format-date-function-calls) - 将一个日期转换成一个很长的日期
* [`epochToDateTime`](parse-and-format-date-function-calls) - 将很长的时间转换到某个日期

## 18 表达式枚举数

* [`getCaption`](enumerations-in-expressions) — 获取当前语言的枚举值的标题
* [`getKey`](enumerations-in-expressions) — 获取枚举值的技术名称
