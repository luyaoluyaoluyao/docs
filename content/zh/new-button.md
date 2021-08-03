---
title: "创建按钮"
parent: "按钮小部件"
---

{{% alert type="info" %}}

此按钮已在 Mendix 7.17中删除。 使用普通的 [动作按钮](action-button) **创建对象** 动作代替。

{{% /报警 %}}

当用户按下 **创建** 按钮时， Mendix 应用程序将创建一个新对象并打开一个页面来编辑新对象。

## 按钮属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Tooltip+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguid7/Render+Mode+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

## 公共属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 常规属性

### 页

此属性指定了当终端用户按此按钮时打开的页面。 终端用户在保存之前可以使用此页面编辑新创建的对象。 此页面应包含一个连接到此按钮相同实体的数据视图。

查看 [打开页面](opening-pages)。

### 实体(路径)

指定点击按钮时要创建的对象类型。 它可以创建一个具有关联到附件数据视图中的对象或作为页面参数传递的对象的对象。 创建新对象时将自动设置关联。 许多社团只支持一对一或一对。

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Extened.md" %}}
