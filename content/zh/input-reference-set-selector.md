---
title: "输入参考集选择器"
parent: "输入小部件"
---


输入参考集选择器是 [输入小部件](input-widgets) ，可用来显示和编辑 [associations](associations) 其多重设置被配置为允许多个父对象与多个子对象相关联。 这类协会也被称为参考集。

{{% alert type="info" %}}

![](attachments/16713883/16844008.jpg) 可以通过双击 [域模型中的关联](domain-model) 来找到一个关联的多重设置。

{{% /警示%}}!{% alert type="info" %}}

![](attachments/pages/input-reference-set-selector.png) 此输入参考设置选择器允许您将员工链接到组织。

{{% /报警 %}}

当点击时 输入参考集选择器将打开一个包含可以用来填写关联的所有对象的小部件的选择页面。

## 常规属性

### 选择页面

选择页面决定当输入参考选择器被点击时显示哪个页面。 此页面可以用来从所有可能的对象列表中选择关联的对象。 此页面应包含一个数据网格、模板网格或与输入参考集选择器连接到同一个实体的列表视图。

如果输入参考集选择器在任何情况下都不可编辑，则不需要选择页面。

查看 [打开页面](opening-pages)。 请注意禁止打开内容中的选择页面。

{{% alert type="success" %}}

您可以通过右键单击小部件和选择“生成选择页面...”来生成一个新页面以显示。

{{% /报警 %}}

## 可选择的对象属性

### XPath 约束

使用 XPath 约束，您可以添加手动约束来限制可以选择的对象列表。

{{% alert type="info" %}}

产品参考选择器的 XPath 约束 `[Instock = true()]` 将确保只有库存中的产品是可以选择的。

{{% /报警 %}}

### 约束者

输入参考集选择器可以被一个或多个路径限制。 这通常用于使一个参考选择器依赖另一个参考选择器。 例如，在您可以编辑用户的页面中，组织选择器可以受国家选择器的约束。 在选择一个国家之后，组织选择者受到该国的限制，只显示与该国有联系的组织。

{{% alert type="info" %}}

![](attachments/16713883/16844007.jpg)

在网域模型中，用户有一个参考协会与国家和参考协会与组织。 从国家到组织的第三个协会描述这两个实体之间的关系。 这种“三角”形成域模型的一部分是可能的制约因素。

![](attachments/16713883/16844006.jpg)

页面显示了一个参考选择器用于参考国家和一个输入参考选择器用于参考组织设置。 后者受到构成三角的域模型的路径限制。

![](attachments/16713883/16844005.jpg)

{{% /报警 %}}

## 数据源属性

{{% snippet file="refguide7/Attribute+Path+Property.md" %}}

{{% snippet file="refguid7/Label+Property.md" %}}

## 编辑属性

{{% snippet file="refguide7/Editable+Property.md" %}}

{{% snippet file="refguide7/Read+Only+Style.md" %}}

{{% snippet file="refguide7/Condition+Property.md" %}}

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}

## 事件属性

{{% snippet file="refguide7/On+Change+Event.md" %}}

## 公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 阅读更多

*   [数据视图](data-view)
