---
title: "Datasets"
parent: "资源"
menu_order: 50
tags:
  - "studio pro"
  - "数据集"
  - "dataset"
---

## 1 导言

数据集可以用来定义 [报告小部件](report-widgets) 在 [页面中显示的数据](pages)。

数据集是使用 [OQL 查询](oql) 或自定义 [Java 动作](java-actions) 定义的。 要约束数据集，可以定义可以在 OQL 查询或 Java 操作中使用的参数。

## 2 概况

数据集字段包含以下属性：

* **名称** - 这是数据集的名称。
* **描述** - 这是数据集的描述，它只是相关的文档。

## 3 源

* **OQL 查询** - 这是 [OQL 查询](oql) 定义数据集。
* **Java 动作** - 这是返回数据集的 Java 动作的接口。 需要在 Studio Pro中指定列的列和 [数据类型](data-types)。 基于此规格，Studio Pro 将为此操作创建一个模板。

以下显示一个 OQL 查询示例，这个查询计算特定客户群所有订单的总订单金额：

```sql
FROM CRM.Customers as CustomerObj
INNER JOIN CustomerObj/CRM.Orders_Customer/CRM.orders as OrderObj
WHERE CustomerObj/CRM ustomer_Group = $ParGroup
GROUP BY CustomerObj/name
SELECT CustomerObj/name as Name、SUM(OrderObj/ Totalamet) as TotalAmount
```

## 4 参数

数据集可以有多个参数。 参数用于过滤/操纵数据集。 数据集的安全性是根据参数配置的。 在 Java 动作中，参数被用于生成的模板。

{{% alert type="info" %}}

在 OQL 中，参数可以使用 **$** 符号，例如： **$Month**

{{% /报警 %}}

参数具有以下可配置属性：

* **名称** - 这是参数的名称。
* **输入** - 参数的类型可以是： **布尔值**, **日期和时间**, **枚举**, **十进制**, **Integer/Long**, 或 **字符串**.
* **约束** -- 参数影响的约束，最终用户可以为参数输入值选择哪个值。 限制因素可以与数据集安全性的 [用户角色](user-roles) 相关联。 有两类制约因素：
  * 适用于数字和日期参数的范围
  * 适用于对象参数的 XPath 约束
* **范围** -- 当参数被定义为范围时 报表中的下拉框显示每个范围而不是范围内的所有值。 十进制参数始终是范围。
* **XPath 约束** - 可以使用 [XPath](xpath) 定义XPath 约束. 可以在参数上定义多个约束，每个约束可以与用户角色相关联。
