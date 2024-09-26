---
title: "按条款排序的 OQL 订单"
parent: "oql"
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/oql-order-by-clause.pdf)。
{{% /报警 %}}

ORDER BY 条款指定了在SELECT 语句中返回的列中使用的排序顺序。 可以指定多列。 栏目按《ORDER》条款中各项的顺序排序。 这一条款可包括SELECT条款中没有出现的项目。 除非指定了SELECT DISTINCT 或者当一个群组存在的子项。 当使用联合国时，列名或别名必须是查询第一部分SELECT条款中规定的名称。

语法如下：

```
ORDER BY
    format@@
        order_by_expression [ ASC | DESC ]
}
```

**order_by_expression** 指定一个实体或一个别名的属性从 FROM 条款排序。

**ASC** 指定结果必须从最低升序到最高值。 ASC 是默认排序。

**DESC** 指定结果必须排序从最高值到最低值。

此查询可检索所有客户并返回姓氏排序的姓名，升序：

```
从销售处选择姓氏。客户
按姓氏排序
```

此查询可检索所有客户并返回按姓氏排序的第一个和姓名，降序：

```
选择姓氏+' + 姓氏来自Sales.客户
BY Lastname DESC
```

{{% alert type="info" %}}
对于NULL值的默认排序行为，请参阅 [NULL值订单行为](ordering-behavior#null-ordering-behavior) 部分 *订单行为* 中。
{{% /报警 %}}
