---
title: "对象类型决定"
parent: "经济及社会理事会"
menu_order: 2
tags:
  - "studio pro"
  - "对象类型决定"
  - "经济及社会理事会"
aliases:
  - /refguide8/heritance-split.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/object-type-decision.pdf)。
{{% /报警 %}}

{{% alert type="info" %}}
这种活动只能用于微流，而不能用于纳米流。
{{% /报警 %}}

## 1 导言

对象类型决定是一个根据一个普遍实体的对象类型作出选择的元素。 对象类型决定的输出是继承一般实体的专门实体。 关于专业化和一般化的更多信息，见 [实体](entities)。

如果您想要在微流的其余部分使用专门类型，您可以使用 [Cast](cast-object) 活动。

## 2 属性

对象类型决策属性由以下部分组成：

* [常用的](#common)

* [Input](#input)

    {{% image_container width="250" %}}
![](attachments/decisions/object-type-decision-properties.png)
{{% /image_container %}}

### 2.1 共同部分 {#common}

#### 2.1.1 标题

欲了解更多信息，请参阅 *常见属性* 中的 [标题](microflow-element-common-properties#caption) 部分。

### 2.2 输入部分 {#input}

#### 2.2.1 对象

输入对象包含一个普遍实体的对象。

例如，您有一个实体 **学生** 和一个实体 **教授** 拥有一个实体 **成员** 作为其概括。 您想要为 **教授** 打开一个不同于其他 **成员** 的页面。 所选的 **个成员** 对象在参数 **选定成员** 中可用，并且被用作对对象类型决定的输入。 请注意， **学生** 没有传出流程。 如果传出流缺失，将搜索含有传出流量的最接近的概括。 在这种情况下，这种一般化是 **个成员**。 当 **选定的成员** 不包含对象时，跟随带有标题 **(空)** 的输出流。

![](attachments/decisions/object-type-decision.png)



