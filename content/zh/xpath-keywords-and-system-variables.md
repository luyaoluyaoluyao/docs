---
title: "XPath 关键字 & 系统变量"
parent: "xpat-conditions"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/xpath-keywords-and-system-variables.pdf)。
{{% /报警 %}}

## 1 概览

在XPath 中，几个关键词和系统变量可以称为比较。

## 2 个关键字

这些关键字中的任何一种都可以用来检查属性是否有一个值(任意值)，或者它是否留空：

* `空值`
* `空的`

### 2.1 实例

此查询返回系统不知道名称的所有客户：

```java
//Sales.Customer[name = NUL]
```

这些关键字只能与属性结合使用。 社团的存在不能以这种方式得到证实。 关于如何约束关联的更多信息，请参阅 [XPath 约束函数](xpath-constraint-functions)。

## 3 系统变量

系统变量可以用来获取系统或日期相关值。 以下是可用代币。

### 3.1 与目标有关的

| 令牌                  | 描述                  |
| ------------------- | ------------------- |
| `[%CurrentUser%]`   | 用户当前登录的 GUID        |
| `[%CurrentObject%]` | 活动对象的 GUID (在上下文中)。 |

### 3.2 用户角色

这些将为您应用中的每个用户角色创建。 下面是一个示例：

| 令牌                           | 描述       |
| ---------------------------- | -------- |
| `[%UserRole_Administrator%]` | 管理员用户角色。 |

以下是检索该用户角色的示例：

![](attachments/xpath/user-role.png)

### 3.3 时间相关的

以下令牌可以用来获取日期和时间值：

| 令牌                            | 描述                |
| ----------------------------- | ----------------- |
| `[%CurrentDateTime%]`         | 当前日期和时间。          |
| `[%BeginOfCurrentMinute%]`    | 本分钟开始的日期和时间。      |
| `[%BeginOfCurrentMinuteUTC%]` | UTC 当前分钟开始的日期和时间。 |
| `[%EndOfCurrentMinute%]`      | 本分钟结束时的日期和时间。     |
| `[%EndOfCurrentMinuteUTC%]`   | 当前分钟结束的日期和时间 UTC  |
| `[%BeginOfCurrentHour%]`      | 当前小时开始的日期和时间。     |
| `[%BeginOfCurrentHourUTC%]`   | UTC 当前小时开始的日期和时间  |
| `[%EndOfCurrentHour%]`        | 当前小时结束的日期和时间。     |
| `[%EndOfCurrentHourUTC%]`     | UTC 当前小时结束的日期和时间  |
| `[%BeginOfCurrentDay%]`       | 本日开始时的日期和时间。      |
| `[%BeginOfCurrentDayUTC%]`    | UTC 当前开始的日期和时间。   |
| `[%EndOfCurrentDay%]`         | 本日结束时的日期和时间。      |
| `[%EndOfCurrentDayUTC%]`      | UTC 当前日结束的日期和时间。  |
| `[%BeginOfCurrentWeek%]`      | 本周初的日期和时间。        |
| `[%BeginOfCurrentWeekUTC%]`   | UTC 当前星期开始的日期和时间。 |
| `[%EndOfCurrentWeek%]`        | 本周末的日期和时间。        |
| `[%EndOfCurrentWeekUTC%]`     | UTC 当前周末的日期和时间。   |
| `[%BeginOfCurrentMonth%]`     | 本月初的日期和时间。        |
| `[%BeginOfCurrentMonthUTC%]`  | 当前月初UTC 的日期和时间。   |
| `[%EndOfCurrentMonth%]`       | 本月底的日期和时间。        |
| `[%EndOfCurrentMonthUTC%]`    | UTC 当前月底的日期和时间。   |
| `[%BeginOfCurrentYear%]`      | 今年年初的日期和时间。       |
| `[%BeginOfCurrentYearUTC%]`   | 当年年初在UTC 中的日期和时间。 |
| `[%EndOfCurrentYear%]`        | 今年年底的日期和时间。       |
| `[%EndOfCurrentYearUTC%]`     | 当年年底在UTC 的日期和时间。  |

以下令牌可以用来添加或减去一个从日期和时间令牌值的时间段：

| 令牌                 | 描述          |
| ------------------ | ----------- |
| `[%DayLength%]`    | 一天时间(24小时)。 |
| `[%HourLength%]`   | 一个小时的长度。    |
| `[%MinuteLength%]` | 1分钟的长度。     |
| `[%SecondLength%]` | 1秒的长度。      |
| `[%WeekLength%]`   | 为期一周(7天)。   |
| `[%MonthLength%]`  | 一个月的长度。     |
| `[%YearLength%]`   | 一年长度。       |

{{% alert type="info" %}}
这些变量必须用作字符串值并放置在两个引号之间。 与时间相关的令牌与周期相关的令牌必须放在一个字符串中。 见例子3。
{{% /报警 %}}

#### 3.3.1 实例

此查询仅返回自本周开始注册的客户：

```java
//Sales.Customer[已注册 >= '[%BeginOfCurrentWeek%]']
```

此查询仅返回本周注册的客户：

```java
//Sales.Customer[已注册 >= '[%BeginOfCurrentWeek%]'和日期注册 <[%EndOfCurrentWeek%]']
```

此查询仅返回在过去三年中注册的客户：

```java
//Sales.Customer[已注册 > '[%BeginOfCurrentDay%] - 3 * [%YearLength%]']
```

此查询返回用户的角色为“管理员”：

```java
/ System.User[System.UserRole = '[%UserRole_Administrator%]']
```
{{% alert type="info" %}}
因为系统变量被写为字符串(引号之间)，所以无法使用圆括号来分组表达式。
{{% /报警 %}}
