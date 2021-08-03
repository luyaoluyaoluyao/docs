---
title: "Datasets"
category: "桌面模型"
---


数据集可以用来定义 [报告小部件](report-widgets) 在 [页面中显示的数据](pages)。

数据集是使用 [OQL 查询](oql) 或自定义 [Java 动作](java-actions) 定义的。 要约束数据集，可以定义可以在 OQL 查询或 Java 操作中使用的参数。

数据集有以下字段：

## A. 概况

*   _描述_: 数据集的描述。这只是相关的文档。

## 来源

*   _OQL 查询_: [OQL 查询](oql) 定义数据集。

*   _Java 动作_: 返回数据集的 Java 动作的接口。 列的 [数据类型](data-types) 需要在桌面模式中指定。 基于此规格，桌面模型将为此操作创建一个模板。

以下显示一个 OQL 查询示例，这个查询计算特定客户群所有订单的总订单金额：

```java
FROM CRM.Customers as CustomerObj
INNER JOIN CustomerObj/CRM.Orders_Customer/CRM.orders as OrderObj
WHERE CustomerObj/CRM ustomer_Group = $ParGroup
GROUP BY CustomerObj/name
SELECT CustomerObj/name as Name、SUM(OrderObj/ Totalamet) as TotalAmount
```

## 参数

数据集可以有多个参数。 参数用于过滤/操纵数据集。 数据集的安全性是根据参数配置的。 在 Java 动作中，参数被用于生成的模板。

{{% alert type="info" %}}

在 OQL 中，参数可以使用 **$** 符号，例如： **$Month**

{{% /报警 %}}

参数具有以下可配置属性：

*   _名称_: 参数名称 </em>

*   _输入_: 参数类型：对象、枚举或原始参数(例如，DateTime、Float、Integer、Boolean等)。 查看 [数据类型](data-types) 以获取可能的参数类型。

*   _制约因素_: 对一个参数的限制。 这些约束会影响最终用户为参数输入值选择的值。 限制可以与数据集安全中的用户角色相关联。 有两种约束类型：适用于数值和日期参数的范围和适用于对象参数的 XPath 限制。

* _范围_: 当一个参数被定义为范围时，报表中的下拉框会显示每个范围而不是范围内的所有值。 货币(过时)、浮点(过时)和小数参数总是范围的。

**XPath 约束**

可以使用 [XPath](xpath) 定义一个 XPath 约束。 可以在参数上定义多个约束，每个约束可以与 [用户角色](user-roles) 相关联。
