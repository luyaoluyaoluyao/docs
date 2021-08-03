---
title: "社会联系"
parent: "实体"
menu_order: 30
tags:
  - "域模型"
  - "关联"
---

## 1 导言

**关联** 标签是实体属性中的一个标签，具有以下设置：

* [名称](#name)
* [类型](#type)
* [所有者](#owner)
* [父母/儿童](#parent-child)

![](attachments/associations/dm-entity-properties-associations-tab.png)

欲了解更多关联信息，请参阅 [关联及其属性](association-properties)。

## 2 个名称 {#name}

该社团的名称用来指它的表格、微流、XPath 制约因素等。

## 3 个类型 {#type}

此属性定义了一个社团是参考(单一)还是参考集(复数)。

| 值   | 描述                        |
| --- | ------------------------- |
| 参考  | 单一：拥有实体的物体是指另一实体的零或一个物体。  |
| 参考集 | 多元化：拥有实体的物体系指另一实体的零或更多物体。 |

* *默认值*: 参考

{{% alert type="info" %}}

这种财产的例子与下面的所有者财产的例子结合在一起。

{{% /报警 %}}

## 4 个所有者 {#owner}

这种财产确定一个协会是拥有一个还是两个业主。 如果有一个拥有者，则所有者位于箭头的开头。

| 值    | 描述               |
| ---- | ---------------- |
| 默认设置 | 只有一个实体是所有者(母公司)。 |
| 两者都是 | 这两个实体都是业主。       |

* *默认值*: 默认

## 5 类型和所有者与多重性和导航性的关系

**输入** and **所有者** 实体的属性与 **相关[多重性](association-properties#multiplicity)** 和 **[导航性](association-properties#navigability)** 属性。 当您更改 **键入** 或 **所有者**时，您更改了 **多重性** 和 **导航性**。

您可以在下面的表格中找到 **类型**/**所有者** 和 **多重性**/**导航能力** 之间的对应。

|                                                 | 类型  | 所有者  |
| ----------------------------------------------- | --- | ---- |
| **多重性**: 一对一 <br />**导航能力**: 不可用          | 参考  | 两者都是 |
| **多重性**: 一对一 <br />**导航能力**: 不可用          | 参考  | 默认设置 |
| **多重性**: 多对多 <br />**导航能力**: X 对象指的 Y 对象  | 参考集 | 默认设置 |
| **多重性**: 多对多 <br />**导航能力**: X 和 Y 对象相互引用 | 参考集 | 两者都是 |

欲了解更多关于多重性和导航性的信息，请参阅第 [2.3 多重性](association-properties#multiplicity) 和 [第 2。 导航能力](association-properties#navigability) 在 *关联及其属性*

## 6 名父母/子女 {#parent-child}

父和子项设置显示关联的方向。 上级定义了关联起始的实体，儿童定义了关联终结的实体。

## 7 个关联示例

从 **订单** 实体到 **客户** 实体的关联结果如下：

![](attachments/domain-model-editor/918217.png)

类型属性有其默认值 `引用`。 在此示例中，客户可以有多个订单，订单只能有一个客户。

在 XML 中，这些实体及其关联的实例如下(注意该社团仅存储在 **命令** 元素中)：

```xml
<Order id="101">
    <telephonenumber></number>
    <date>9/30/2008</date>
    <Order_Customer>id_201</Order_Customer>
</Order>

<Customer id="201">
    <fullname>Apple Inc.</fullname>
    <address>1 无限循环</address>
    <telephonenumber> 1-800-MY-APPLE</telephonenumber>
</Customer>

```

通过绘制一个关联，创建了多对多的关联，然后将 `类型` 属性设置为 `引用设置`。

在此示例中， **客户** 可以有多个 **组**, 和 **组** 可以有多个 **客户**:

![](attachments/domain-model-editor/918127.png)

在 XML 中，这些实体及其协会的实例如下(注意该协会仅存储在 **客户** 元素中)：

```xml
<Customer id="201">
    <fullname>苹果</name>
    <address>1 无限循环</address>
    <telephonenumber>1-800-MY-APPLE</telephonenumber>
    <Customer_Group>id_301 id_302</Customer_Group>
</Customer>

<Group id="301">
    <name>多国公司</name>
</Group>

<Group id="302">
    <name>硬件供应商</name>
</Group>

```

通过设置所有者属性为 `创建了一对一的关联` (在保留类型属性为默认值 `引用` 时)。

在这个示例中， **客户** 可以有一个 **配置文件**, 和一个 **配置文件** 可以有一个 **客户**:

![](attachments/domain-model-editor/918128.png)

在 XML， 这些实体及其关联的实例如下所示(注意关联已保存在 **配置** 元素和 **客户** 元素中)：

```xml
<Profile id="401">
    <religion>佛教</religion>
    <job>首席执行官</job>
    <website>http://www. ple. om/ </website>
    <Customer_Profile>id_201</Customer_Profile>
</Profile>

<Customer id="201">
    <fullname>Steve Jobs</fullname>
    <address>1 无限期循环</address>
    <telephonenumber>1-800-MY-APPLE</telephonenumber>
    <Customer_Profile>id_401</Customer_Profile>
</Customer>

```

通过设置所有者属性为 `` 和类型属性为 `参考设置` 创建一个多对多个关联，两个实体都是所有者。

在此示例中， **会计师** 可以有多个 **组** 和 **组** 可以有多个 **会计师**

{{% image_container width="500" %}}![](attachments/domain-model-editor/918125.png)
{{% /image_container %}}

在 XML， 这些实体及其关联的实例如下所示(请注意，关联已保存在 **会计师** 元素和 **组** 元素中)：

```xml
<Accountant id="501">
    <idnumber>1</idnumber>
    <name>Earl Grey</name>
    <telephonenumber>1-800-EARL-GREY</telephonenumber>
    <Accountant_Group>id_301 id_302</Accountant_Group>
</Accountant>

<Accountant id="502">
    <idnumber>2</idnumber>
    <name>Scrooge McDuck</name>
    <telephonenumber>1-800-SCROOGE-MCDUCK</telephonenumber>
    <Accountant_Group>id_301 id_302</Accountant_Group>
</Accountant>

<Group id="301">
    <name>Multinational corporations</name>
    <Accountant_Group>id_501 id_502</Accountant_Group>
</Group>

<Group id="302">
    <name>Hardware suppliers</name>
    <Accountant_Group>id_501 id_502</Accountant_Group>
</Group>

```

## 8 阅读更多

* [协会及其财产](association-properties)
* [实体](实体)