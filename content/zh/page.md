---
title: "页"
parent: "页面"
---

## 1 导言

{{% alert type="info" %}}

此文档描述一个页面的属性。 关于哪些页面的详细信息以及哪些小部件可以放置在它们上，参见 [页面](pages)。

{{% /报警 %}}

页面定义Mendix 应用程序的最终用户接口。 每个页面都基于 [布局](layout)。 A page fills the "gaps" defined by a layout with widgets such as the [data view](data-view) and [data grid](data-grid).

{{% alert type="success" %}}
来自 Mendix 版本 7。 6 可以通过点击页面编辑器中的 **查看模式** 按钮来预览您正在设计的页面。 您可以通过点击 **编辑模式** 返回编辑页面。

![编辑模式和视图模式按钮](attachments/pages/view-mode.png)

{{% /报警 %}}

## 2 公共属性

{{% snippet file="refguide7/Document+Name+Property.md" %}}

{{% snippet file="refguide7/Documentation+Property.md" %}}

{{% snippet file="refguide7/Document+Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 3 设计师属性

{{% snippet file="refguide7/Canvas+Width+Property.md" %}}

{{% snippet file="refguide7/Canvas+Hight+Property.md" %}}

## 4 个一般属性

### 4.1 标题

使用 [页面标题小部件](page-title) 显示的页面标题。 如果页面显示在弹出窗口中，标题会出现在弹出窗口的标题栏中。 标题可以从打开表格的地方覆盖，以便能够为不同目的重新使用一个页面。 例如， [网格创建按钮](grid-new-button) 和 [编辑按钮](edit-button) 可以引用同一页面， 但是他们分别将标题覆盖到 **新的** 和 **编辑**中。

### 4.2 布局

这是此页面的 [布局](layout)。

### 4.3 URL

页面的 URL 可以直接导航到页面(例如，从外部链接或书签)。 当您访问页面时，它将显示在浏览器的地址栏中。 当导航到没有配置URL的页面时，会显示最后访问过的URL。 请注意，页面的完整URL将是您应用程序的基础URL，然后是 `/p` ，然后是页面的已配置的 URL (例如) `http://示例。 endixcloud.com/p/home_page`)。

具有顶级数据视图(参数化页面)的页面也可以有URL。 此页面的 URL 属性应该包含结尾处的 `{Id}` 路径段。 在浏览器中， `{Id}` 部分将被实体的实际标识符所取代。

在简单的电子商务应用程序中，URL可以配置如下：

* */orders/* — 一个带有 `订单数据网格的页面的 URL` (在浏览器中) URL将看起来像 `http://示例。 endixcloud.com/p/p/orders/`)

* */order/{Id}* - 一个页面的 URL 包含特定的数据 `订单` (浏览器中的实际URL 将看起来像 `http://示例。 endixcloud.com/p/order/3212449487634321`, 其中 `3212449487634321` 是 `命令` 的唯一标识符

## 5 个导航属性

### 5.1 可见于

这些是页面可见的模块角色。 这对 [菜单部件](menu-widgets) 和仅允许时可见的按钮有影响 (例如) [编辑按钮](edit-button)

欲了解更多信息，请参阅 [Module Security](module-security)。

## 6 个弹出属性

弹出窗口属性仅与弹出页面相关(相对于内容页面)。

### 6.1 宽度(Pixels)

这以像素为单位指定弹出宽度。 当设置为 0时，宽度将自动确定。

*默认值：* 0

### 6.2 高度 (Pixels)

指定弹出高度以像素为单位。 当设置为 0时，高度将自动确定。

*默认值：* 0

### 6.3 Resizable

指定弹出窗口是可调整大小(是)还是固定大小(否)。

*默认值：* 是

### 6.4 关闭行动

配置弹出式关闭按钮的行为 (右上角的小交叉)。 弹出窗口关闭按钮的默认行为是回滚任何更改并关闭弹出窗口。 如果您想要自定义弹出关闭按钮的行为，您可以指向页面上的按钮。 当点击弹出窗口关闭按钮时，它会像点击选中按钮一样起作用。 如果选中的按钮不可用，弹出式关闭按钮将恢复为默认行为。

 _默认值：_ 默认 (cancel)

## 7 使用属性

### 7.1 标记为已使用

您可以通过按 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> 来搜索建模中未使用的项目。 仅使用 Java 代码的页面将被列为未使用，因为Moderr 无法在 Java 源代码中看到。

设置属性 **标记为使用** 为 **是**， 您指定文档已隐含使用，当搜索未使用的项目时，Modeler将不再列出它。

*默认值：* 否
