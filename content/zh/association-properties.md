---
title: "关联属性"
parent: "关联"
menu_order: 10
tags:
  - "域模型"
  - "关联"
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/association-properties.pdf)。
{{% /报警 %}}

## 1 导言

有两种方法来编辑 [关联](associations) 的属性。 此页面描述了您可以在域模型中关联属性窗格中编辑的属性。 或者直接从关联或实体属性中的关联标签打开关联属性对话框。

您也可以在实体属性中直接编辑关联标签。 欲了解更多信息，请参阅 [关联标签属性](association-member-properties)。

{{% alert type="info" %}}
关联外部实体的属性在原始应用程序中定义，唯一可以应用于这些实体的本地更改是本地名称和描述。 For further information, see the [Attributes](external-entities#attributes) section of *External Entities*.
{{% /报警 %}}

## 2 个关联属性

下面的图像显示了关联属性的示例：

![关联属性](attachments/associations/association-properties.png)

协会有下列财产：

* [名称](#name)
* [文件](#documentation)
* [多重性](#multiplicity)
* [导航能力](#navigability)
* [删除行为](#delete-behavior)

### 2.1 名称 {#name}

指向关联的名称。 例如，在形式或微流方面。

### 2.2 文件 {#documentation}

您可以在 **文档** 属性中写入备注和文档。

### 2.3 多重性 {#multiplicity}

多重性可以是以下类型：

| 多重性         | 含义            | 等于：                                                                |
| ----------- | ------------- | ------------------------------------------------------------------ |
| 一对一的        | 一个X对象与一个Y对象关联 | An association of type **Reference** with owner set to **Both**    |
| 一对多的 *(默认)* | 一个X对象与多个Y对象关联 | An association of type **Reference** with owner set to **Default** |
| 多对多         | 多个X对象与多个Y对象关联 | 类型 **引用集** - 在这种情况下所有权由 **导航能力设置** 属性                              |

欲了解更多关于关联类型的信息，请参阅 *关联标签属性*中的 [类型](association-member-properties#type) 部分， 欲了解所有权，请参阅 [所有者](association-member-properties#owner) 章节 *关联标签属性*。

### 2.4 Navigability {#navigability}

| 导航能力                | 含义         | 等于：                                                                    |
| ------------------- | ---------- | ---------------------------------------------------------------------- |
| X 对象引用到 Y 对象 *(默认)* | 该协会的所有者是 X | An association of type **Reference set** with owner set to **Default** |
| X 和 Y 对象相互引用        | 这两个实体都是所有者 | An association of type **Reference set** with owner set to **Both**    |

这对应于 **参考集** 的 **所有者** 属性。 请参阅 *Association Tab Properties 的 [所有者](association-member-properties#owner) 部分* 以更详细地讨论改变导航能力的影响。

尽管它有名称，但通航能力通常只有在添加或更改关联时才很重要。 使一个对象所有者成为一个社团，并不会阻止您从非所有者的末尾读取社团。

### 2.5 删除行为 {#delete-behavior}

| 值                                                                                                                              | 描述                       |
| ------------------------------------------------------------------------------------------------------------------------------ | ------------------------ |
| 删除 {name of entity} 对象，但保留 {name of other entity} 对象 *(默认)*                                                                    | 当一个对象被删除时，关联对象不会被删除。     |
| 删除 {name of entity} 对象和 {name of other entity} 对象<sup><small>[1]</small></sup>                                                 | 当一个对象被删除时，关联对象也会被删除。     |
| Delete {name of entity} object only if it is not associated with {name of other entity}<sup><small>[2]</small></sup> object(s) | 一个对象只能在与任何其他对象无关的情况下被删除。 |

<sup><small>[1]</small></sup>如果您想要删除任何关联的 **配置文件** 当一个 **客户** 被删除时，此删除行为将被使用：

![](attachments/associations/association-delete-both.png)

<sup><small>[2]</small></sup>如果您想要能够删除一个 **客户** 只有当它与任何 **订单没有关联时** 才会使用这种删除行为。 在这种情况下，如果不能删除</strong> 客户对象，您将被要求输入一个 **错误信息，以告知最终用户该客户不能被删除，或许建议下一个行动方针：</p>

![](attachments/associations/association-prevent-delete.png)

## 3 阅读更多

* [社会联系](关联)
