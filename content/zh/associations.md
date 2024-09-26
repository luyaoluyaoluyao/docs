---
title: "社会联系"
parent: "域名模型"
menu_order: 20
tags:
  - "域模型"
  - "关联"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/associations.pdf)。
{{% /报警 %}}

## 1 导言 {#intro}

一个协会描述了实体之间的关系。 在域模型中，一个协会由两个实体之间的一条线或箭头来表示。

{{% alert type="info" %}}
来自同一数据源的两个外部实体之间的关联在原始应用程序中定义，因此在实体被用于模型时自动建立。 For further details, see the [Associations](external-entities#properties) section of *External Entities*.
{{% /报警 %}}

### 1.1 所有权 {#ownership}

关联的值应该从身为关联的 [所有者的](association-member-properties#owner) 实体中查看和编辑。 一个社团的所有权被箭头标明（注意箭头并不表示方向）。 一个实体或两个实体都可以成为该协会的所有者。 如果一个实体是业主，则有一个从业主到另一个实体的箭头。 如果两个实体都是业主，两个实体之间就有一条线，但没有箭头。 这是唯一可以控制箭头的方式。

必须理解为什么存在所有权。 所有权是在 Mendix 中实现的，以便您能够动态地改变关系，而不是被第一个设计卡住。 例如， 如果你设计了一个 [单对多的关联](#one-to-many) 并且需要它是一个 [的多对多的关联，默认所有者](#many-to-many), 您不需要重建您的数据库，因为Mendix 可以为您处理它。

### 1.2 多重性

一个社团的 [多重性](association-properties#multiplicity) (或所指对象的数量) 在社团的任何一侧都以编号1 (`1`)或星号(`*`表示出来。

在下面的示例中，箭头表示 **订单** 是该协会的所有者。 和 `1` 和 `*` 表示一个客户与许多订单相关联：

![](attachments/associations/association-order-customer.png)

{{% alert type="info" %}}
可持久实体和不可持久实体之间的关联必须从不可持续实体中启动并拥有所有者 **默认值**。 关于可持久性和不可持久性实体的更多信息，见 [可持久性](persistability)。
{{% /报警 %}}

## 2 正在创建关联 {#creating}

创建关联的最快方式是在 [域模型](domain-model) 中绘制两个实体之间的关联。 默认情况下，这将创建一个一对一的社团，从社团的所有者/多方面开始，到社团的一方结束。 该协会将通过用下划线加入两个实体的名字来命名。 然后您可以编辑下一个章节中讨论的关联。

您也可以在应用的不同模块中创建实体间的关联。 在这种情况下，无法成立协会。 您可以在拥有关联的实体的 **关联** 标签中创建一个新的关联到另一个模块的域模型中的实体。 然后您可以选择应用内的任何实体作为关联的目标。 欲了解更多信息，请参阅 [关联标签属性](association-member-properties)。

{{% alert type="info" %}}
您只能在外部实体和本地实体之间创建和编辑关联。 然而，外部实体不能是本地实体关联的 [所有者](association-member-properties#owner)。
{{% /报警 %}}

{{% alert type="info" %}}
如果您需要连接两个外部实体，考虑添加一个本地实体并将这个本地实体与两个外部实体连接起来。 在这种情况下，地方实体必须是这两个协会的所有者。
{{% /报警 %}}

## 3 编辑关联

有两种编辑社团的方式。

### 3.1 直接编辑协会

您可以编辑关联本身。 在这种情况下，您将使用多重性和导航性来定义关联。

![](attachments/associations/edit-association.png)

欲了解更多信息，请参阅 [关联属性](association-properties)。

### 3.2 从实体中的协会编辑

您可以将社团编辑为实体成员。 在此情况下，您将使用类型和所有者定义关联。

![](attachments/associations/edit-entity-association.png)

欲了解更多信息，请参阅 [关联标签属性](association-member-properties)。

## 4 个关联示例 {#examples}

### 4.1 一对多协会 {#one-to-many}

在此示例中，从 **订单** 实体中绘制到 **客户** 实体的结果如下：

![](attachments/associations/association-order-customer.png)

类型属性有其默认值 `引用`，所有者(订单实体)是 `默认`。 这与将多重性设置为 `一个'客户'对象与多个'订单'对象` 相关，因此客户可以有多个订单。 但订单只能有一个客户。

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

### 4.2 拥有默认所有权的多对多人协会 {#many-to-many}

通过绘制一个关联，然后将类型属性设置为 `引用了` 并将所有者设置为 `默认` ，从而创建了一个多对多的关联，默认所有权。

在此示例中， **客户** 可以有多个 **组**, 和 **组** 可以有多个 **客户**。 这与多个设置为 `多个'组'对象与多个'客户'对象` 关联，导航能力设置为 `'客户'对象指'组'对象`:

![](attachments/associations/association-customer-group.png)

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

### 4.3 一对一协会

通过设置所有者属性为 `创建了一对一的关联` (在保留类型属性为默认值 `引用` 时)。

在这个示例中， **客户** 可以有一个 **配置文件**, 和一个 **配置文件** 可以有一个 **客户**。 这与设置为 `的多重性相同。一个'客户' 对象与一个 '配置' 对象` 相关：

![](attachments/associations/association-customer-profile.png)

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

### 4.4 具有双重所有权的多对多人协会

通过设置所有者属性为 `` 和类型属性为 `参考设置` 创建一个多对多个关联，两个实体都是所有者。

在此示例中， **会计师** 可以有多个 **组** 和 **组** 可以有多个 **会计师** 这与多个设置为 `多个“组”对象与多个“会计”对象` 关联，导航能力设置为 `“会计”类和“组”类对象相互关联`：

{{% image_container width="500" %}}![](attachments/associations/association-accountant-group.png)
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
