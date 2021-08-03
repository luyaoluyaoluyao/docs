---
title: "表达式"
parent: "常用元素"
aliases:
  - /refguide7/microflow-expressions.html
description: "描述可以用于多种目的的 Mendix 表达式(例如) 根据逻辑更改对象的成员)。"
---

表达式可以用来根据逻辑更改对象的成员。 微流中的变量可以在表达式中通过插入变量的名称并添加一个美元标志来调用。 例如： _$customer_ 指的是变量 _客户_。 表达式可以递归使用，例如 _1 + 2 + 3_。 对象变量的属性和关联可以用slash访问，例如， _$customer/name_, _$customer/CRM.Customer_order_

要说明这个图象，一个具有变量名称 _包_ 的对象具有两个属性： _权重_ (浮点) 和 _装运费用 _(十进制)。 规则：如果包件重量小于一公斤，则没有运费。 否则运费为5.00欧元\。 更改属性 _船运成本_ 的表达式是： _ $package/权重 < 1.00或0.00 等于5.00_

下面概述了各种表述的可能性。

### [异常表达式](unary-expressions):

* [Unary 减去( - )](unary-expressions)

### [Arithmetic Expressions](arithmetic-expressions):

* [乘法( * )](arithmetic-expressions)
* [Division ( div or : )](arithmetic-expressions)
* [Modulo ( mod )](arithmetic-expressions)
* [添加 ( + )](arithmetic-expressions)
* [减法 ( - )](arithmetic-expressions)

### [关联表达式](relational-expressions):

* [小于 ( <)](relational-expressions)
* [大于 ( >)](relational-expressions)
* [小于或等于 ( <= )](relational-expressions)
* [大于或等于 ( >= )](relational-expressions)
* [等于 ( = )](relational-expressions)
* [不等于 ( != )](relational-expressions)

### [特别检查](special-checks)

* [正在检查一个空对象](special-checks)
* [检查空对象成员](special-checks)
* [`是新`](special-checks) - 检查对象是否是新对象

### [布尔表达式](boolean-expressions)

* [和](boolean-expressions)
* [或](boolean-expressions)
* [不是](boolean-expressions)

### [如果表达式](if-expressions)

### [数学函数调用](mathematical-function-calls)

* [`最大`](mathematical-function-calls) - 数字列表的最大值
* [`分钟`](mathematical-function-calls) - 数字列表的最小值
* [`环`](mathematical-function-calls) - 四舍五入一个浮点数，可选为指定精度
* [`随机`](mathematical-function-calls) - 随机数字生成
* [`floor`](mathematical-function-calls) - 四舍五入一个浮点数
* [`ceil`](mathematical-function-calls) - 向上四舍五入一个浮点数
* [`pow`](mathematical-function-calls) - 指数化
* [`abs`](mathematical-function-calls) - 绝对值
* [`浮点等价` `/ 货币等价`](mathematical-function-calls) - 一定精度的浮点/货币等价(过时)

### [字符串函数调用](string-function-calls)

* [`toUpperCase`](string-function-calls) - 将字符串转换为大写。
* [`toLowerCase`](string-function-calls) - 将字符串转换为小写
* [`长度`](string-function-calls) - 字符串长度
* [`子字符串`](string-function-calls) - 获取字符串的部分
* [`找到`](string-function-calls) - 获取子字符串位置
* [`查找最后`](string-function-calls) - 获取最后一个子字符串位置
* [`包含`](string-function-calls) - 包含子字符串
* [`启动`](string-function-calls)  - 确定字符串是否以指定的子字符串开始
* [`endsWits`](string-function-calls)  - 确定一个字符串是否以指定的子字符串结束
* [`修剪`](string-function-calls) - 删除前导和尾随空格
* [`isMatch`](string-function-calls) - 匹配正则表达式
* [`替换所有`](string-function-calls) - 替换子字符串的事件
* [`替换第一个`](string-function-calls) - 替换第一个子字符串
* [字符串连接( + )](string-function-calls) - 连接字符串
* [`urlEncode`](string-function-calls) - 转换一个字符串用于一个 URL
* [`urlDecode`](string-function-calls) - 从 URL 转换一个字符串

### [创建日期](date-creation)

* [`日期时间`](date-creation) - 使用服务器的日历创建日期值
* [`dateTimeUTC`](date-creation) - 使用 UTC 日历创建日期值

### [在日期之间的函数调用](between-date-function-calls)

* [`毫秒之间`](between-date-function-calls) - 两个日期之间的毫秒
* [`秒之间`](between-date-function-calls) - 两个日期之间的秒数
* [`分钟之间`](between-date-function-calls) - 两个日期之间的分钟
* [`小时之间`](between-date-function-calls) - 两个日期之间的小时
* [`天之间`](between-date-function-calls) - 两个日期之间的天数
* [`周之间`](between-date-function-calls) - 两个日期之间的周

### [添加日期函数调用](add-date-function-calls)

* [`addMilliseconds`](add-date-function-calls) - 将毫秒添加到某个日期
* [`addonds`](add-date-function-calls) - 给日期添加秒数
* [`添加分钟`](add-date-function-calls) - 将分钟添加到一个日期
* [`添加小时`](add-date-function-calls) - 将小时添加到某个日期
* [`添加天`](add-date-function-calls) - 将天添加到某个日期
* [`添加 DaysUTC`](add-date-function-calls) - 使用 UTC 日历将天数添加到日期
* [`添加周`](add-date-function-calls) - 将周添加到某个日期
* [`添加周际`](add-date-function-calls) - 使用 UTC 日历将周添加到日期
* [`添加月`](add-date-function-calls) - 将月添加到一个日期
* [`addMonthsUTC`](add-date-function-calls) - 使用 UTC 日历将月份添加到日期
* [`添加年份`](add-date-function-calls) - 添加年份到日期
* [`添加 YearsUTC`](add-date-function-calls) - 使用 UTC 日历将年添加到日期

### [修剪到目前为止的版本](trim-to-date)

* [`trimToSeconds`](trim-to-date) - 修整秒钟
* [`修剪分钟`](trim-to-date) - 修剪到分钟
* [`修剪小时`](trim-to-date) - 修剪到小时
* [`trimToHoursUTC`](trim-to-date) - 使用 UTC 日历修剪小时数
* [`三天`](trim-to-date) - 整整几天
* [`trimToDaysUTC`](trim-to-date) - 使用UTC 日历修整天数
* [`三个月`](trim-to-date) - 修整几个月
* [`三季月UTC`](trim-to-date) - 使用 UTC 日历修整几个月
* [`季度`](trim-to-date) - 修剪年数
* [`三个年级`](trim-to-date) - 使用 UTC 日历修剪年份

### [到字符串](to-string)

### [to float](to-float) (废弃)

### [解析整数](parse-integer)

### [Parse/格式浮动函数调用](parse-and-format-float-function-calls) (废弃)

* [`parseFloat`](parse-and-format-float-function-calls) - 将字符串转换为浮点数
* [`格式浮动`](parse-and-format-float-function-calls) - 将一个浮点转换为字符串

### [解析/格式小数函数调用](parse-and-format-decimal-function-calls)

* [`解析小数点`](parse-and-format-decimal-function-calls)  - 将字符串转换为小数
* [`格式小数`](parse-and-format-decimal-function-calls)  - 将小数转换为字符串

### [解析/格式日期函数调用](parse-and-format-date-function-calls)

* [`解析日期时间[UTC]`](parse-and-format-date-function-calls) - 将字符串转换为日期值
* [`格式日期时间[UTC]`](parse-and-format-date-function-calls) - 将日期值转换为字符串
* [`格式时间[UTC]`](parse-and-format-date-function-calls) - 将日期值的时间部分转换为字符串
* [`格式日期[UTC]`](parse-and-format-date-function-calls) - 将日期值的日期部分转换为字符串

### [表达式的枚举数](enumerations-in-expressions)

* [`getCaption`](enumerations-in-expressions) - 获取当前语言的枚举值的标题
* [`getKey`](enumerations-in-expressions) - 获取枚举值的技术名称
