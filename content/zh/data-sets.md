---
title: "Datasets"
parent: "资源"
menu_order: 50
tags:
  - "studio pro"
  - "数据集"
  - "dataset"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/data-sets.pdf)。
{{% /报警 %}}

## 1 导言

数据集可以用来定义 [报告小部件](report-widgets) 在 [页面中显示的数据](pages)。

数据集是使用 [OQL 查询](oql) 或自定义 [Java 动作](java-actions) 定义的。 要约束数据集，可以定义可以在 OQL 查询或 Java 操作中使用的参数。

数据集字段描述如下。

## 2 概况

* **名称** -- 数据集的名称。
* **描述** -- 数据集的描述，仅适用于文档。

## 3 源

* **OQL 查询** -- [OQL 查询](oql) 定义数据集。
*  **Java 动作** -- 返回数据集的 Java 动作的接口。 需要在 Studio Pro中指定列的列和 [数据类型](data-types)。 基于此规格的Studio Pro 将为此操作创建一个模板。

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

* **名称** -- 参数名称
* **输入** - 参数类型：对象、枚举或原始参数(例如日期和时间、 Integer、Boolean等)。 查看 [数据类型](data-types) 以获取可能的参数类型。
* **制约因素** -- 对一个参数的限制。 这些约束影响最终用户为参数输入值选择的值。 限制可以与数据集安全中的用户角色相关联。 有两种约束类型：适用于数值和日期参数的范围和适用于对象参数的 XPath 限制。
* **范围** - 当一个参数被定义为范围时，报表中的下拉框显示的是每个范围，而不是范围内的所有值。 十进制参数始终是范围。
* **XPath 约束** - 可以使用 [XPath](xpath) 定义XPath 约束. 可以在参数上定义多个约束，每个约束可以与 [用户角色](user-roles) 相关联。
