---
title: "OData 查询选项"
parent: "已发布的 odata 服务"
tags:
  - "OData"
  - "筛选器"
  - "计数"
  - "排序"
  - "选择"
  - "页面"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/odata-query-options.pdf)。
{{% /报警 %}}

## 1 导言

这是OData查询选项的列表。

{{% alert type="info" %}}
我们目前只支持这里所述的各种选择。
{{% /报警 %}}

## 2 个检索对象

### 2.1 检索所有对象

所有对象都可以通过指定 URI 来检索。 例如： `/odata/myservice/myresource`。 如果您在浏览器中指定URI，您可以看到这一点。

### 2.2 检索单一对象

通过传递URI中的对象标识符可以检索单个对象。 例如： `/odata/myservice/myresource(8444249301330581)`。

### 2.3 检索相关对象

相关对象可以通过通过 `$expand` 查询参数获取。 例如： `/odata/myservice/Exploque?$expand=Cars,Address/City`

{{% alert type="info" %}}
`$expand` 功能是在Studio Pro [8.11.0](/releasenotes/studio-pro/8.11#8110) 中介绍的。
{{% /报警 %}}

## 3 计数对象数量

### 3.1 检索物体数量

您可以通过传递 `$count` 查询选项来发现那里有多少对象。 在这种情况下，结果是一个整数，即对象的数量。 例如： `/odata/myservice/myresource/$count`

### 3.2 内联计数

通过设置 `$inlinecount` 查询选项为“allpages”，返回的项目数量将包含在结果中。 例如： `?$inlinecount=allpages`。

## 4 个过滤

筛选器通过附加一个 `$filter=...` 参数应用到请求中。 例如： `/员工？$filter=name eq 'John'`

### 4.1 传递属性

此表描述了如何传递不同属性类型的值：

| 类型      | 如何通过                                                                                |
| ------- | ----------------------------------------------------------------------------------- |
| 字符串和枚举值 | 以单引号内嵌(例如'John')                                                                    |
| 日期时间    | 以 `日期时间` 结尾，然后用单引号显示(例如日期时间'2015-01-01' 或日期时间&lt;epoch value here&gt;') |
| 其他      | A. 原始价值（例如，15）                                                                      |

### 4.2 比较运算符

我们支持以下比较操作：

| 运算符 | 含义    | 示例                             |
| --- | ----- | ------------------------------ |
| iq  | 等于    | `雇员？$filter=name eq 'John'`    |
| n   | 不等于   | `/员工？$filter=Name ne 'John'`   |
| gt  | 大于    | `/employees?$filter=Age gt 15` |
| 英寸  | 小于    | `/员工？$filter=年龄15分`            |
| ge  | 大于或等于 | `/employees?$filter=Age 15`    |
| l   | 小于等于  | `/员工？$filter=15岁`              |

### 4.3 算术运算符

| 运算符 | 含义      | 示例                                        | 返回          |
| --- | ------- | ----------------------------------------- | ----------- |
| 添加  | 添加      | `/Production?$filter=价格添加 2 eq 10`        | 所有带价格的产品 8  |
| 子项  | minus   | `/Products?$filter=价格2eq 10`              | 所有有价格的产品 12 |
| mul | 乘以：     | `/Production?$filter=价格 2 eq 10`          | 所有价格为5的产品   |
| div | 除以      | `/Production?$filter= Prices div 2 eq 10` | 所有有价格的产品 20 |
| mod | modulus | `/Products?$filter=价格 mod 5 eq 0`         | 价格可分为5的所有产品 |

### 4.4 职能

| 函数          | 示例                                        | 返回                                  |
| ----------- | ----------------------------------------- | ----------------------------------- |
| substringof | `/employees?$filter=substring('f', 名称)`   | 所有包含“f”名称的员工都是                      |
| 端sand       | `/员工？$filter=endswith(名字，'f')`            | 所有具有此末尾“f”名称的员工                     |
| 启动          | `/employees?$filter=startswith(名字, 'f')`  | 所有名字以“f”开头的员工。                      |
| 长度          | `/员工？$filter=length(名称) eq 5`             | 所有名字长度为5的员工数                        |
| 年           | `/员工？$filter=year(DateOfBirth) eq 1990`   | 1990年出生的所有员工：                       |
| 月           | `/employees?$filter=月份(DateOfBirth) eq 5` | 5月份出生的所有员工：                         |
| 天           | `/员工？$filter=day(DateOfBirth) eq 31`      | 月31日出生的所有员工：                        |
| 小时          | `/员工？$filter=小时(注册) eq 13`                | 所有员工在13:00(1 PM)至13:59(1:59 PM)之间注册 |
| 分钟          | `/employees?$filter=minute(注册) eq 55`     | 所有员工在任何小时的55分钟注册                    |
| 秒           | `/员工？$filter=second(注册) eq 55`            | 所有员工都注册在任何一分钟的第55秒内                 |

### 4.5 组合过滤器

过滤器可以与 `和`, `或`, `not`, 和 `()` 合并. 例如： `?$filter=name eq 'John' and (ge gt 65 or Age 11)`

| 组合  | 示例                                                |
| --- | ------------------------------------------------- |
| 和   | `/employees?$filter=name eq 'John' and Age gt 65` |
| 或   | `/员工？$filter=年龄gt 65 或 11`                        |
| 不是  | `/员工？$filter=not(Name eq 'John')`                 |
| ( ) | `/员工？$filter=name eq 'John' 和 (Age gt 65 或 11岁)`  |

### 4.6 按协会筛选

您可以筛选关联实体的属性。 您这样做的方式取决于该社团是否暴露了一个对象或一个对象列表。

| 类型       | 示例                                                  |
| -------- | --------------------------------------------------- |
| 筛选关联对象   | `人民？$filter=生平地/Cityname eq '鹿特丹'`                  |
| 在关联列表中过滤 | `城市？$filter=BornIn/any(person:person/year le 1919)` |

当您 [透露关联关联为链接](odata-representation#associations) 时，可以这样对关联对象或列表进行过滤。 当您 [以关联对象 ID](odata-representation#associations) 的形式揭示关联时，它是不可能的。

## 5 排序

您可以使用 `$orderby` 查询选项排序结果。 例如： `?$orderby=name` 或 `?$orderby=出生地/名称`.

默认方向升高，并且您可以让它变得清晰。 例如： `?$orderby=name asc`

您也可以按降序排序结果。 例如： `?$orderby=Name desc`

它可以按多个属性排序，这些属性必须用逗号分隔。 例如： `?$orderby=名字升序，年龄降序`

## 6 选择字段

您可以通过指定 `$select` 查询选项来选择要返回的属性和关联。 例如： `?$select=Name,年龄`。

## 7页

### 7.1 顶部(限制)

您可以使用 `$top` 查询选项限制返回对象的数量，因为限制是一个正整数。 例如： `?$top=100`

### 7.2 跳过 (Offset)

您可以在使用 `$skip` 查询选项检索结果之前跳过一些对象，而偏移是一个正整数。 例如： `?$skip=100` 会返回从列表中第101个对象开始的对象。

## 8 Null Literals

您可以比较值与 `null` 字幕。 例如： `?$filter=name eq nul`

在这个示例中， `name` 是一个在数据库中没有分配值的字符串属性。 注意 `null` 意味着 *没有值* 而不是 `'` (这是一个空字符串)。

当您过滤关联时，空文可能非常有用。 例如： `?$filter=Association_A_B ne null` 在此示例中， 您查询实体类型 `A` 中至少有一个关联设置为实体类型 `B 类型对象的对象`。
