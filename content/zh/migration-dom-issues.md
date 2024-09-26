---
title: "故障排除DOM更改"
parent: "从 7-8 移动"
menu_order: 10
description: "此文档解释了更新的 Mendix 8 的DOM结构以及这对应用的 CSS 意味着什么。"
tags:
  - "DOM"
  - "小部件"
  - "主题"
  - "班级"
---

## 1 导言

Mendix 8中客户端的其他改进，Mendix 应用程序的HTML也已更新。 这些更改使得部件更容易访问、更加一致，并且使您能够使用更清洁的标记。

然而，这些更新可能会影响到您的搭配。 您的应用程序的外观可能会受到影响，因为部件的文档对象模型结构已更新。 本参考指南将概述Mendix 7和8之间与DOM和CSS有关的差异。 此文档仅适用于使用自定义的 CSS 或修改现有的 Atlas UI CSS 的应用。

## 2 更新阿特拉斯系统

升级到 Mendix 8 时，DOM 结构更改也会更改相关的 Sass 样式文件。 这可能会使你的样式无法继续正常工作。 要使您的样式与 Mendix 8 兼容，请参阅 [Troubleshoot Atlas UI 更改，迁移到 Mendix 8](migration-atlas)。

## 3 个简化的自定义主题

在 Mendix 8 之前，如果您的应用程序没有主题，客户端提供了大量的默认样式。 这就使您难以构建自己的主题，因为您需要覆盖默认风格。 从Mendix 8开始，所有样式都已移动到AtlasUI。 现在，从头开始构建您自己的主题需要的工作要少得多。

如果您已经在早些版本的Mendix中从零开始构建了您自己的主题， 您可能依赖于默认样式(具体来说是 Bootstrap 文件和 **mxui)。 默认 Mendix 8 应用程序中不包含 ss** 文件。 对于这种情况，Mendix 提供了遗留的 **mxui.css** 和 Bootstrap文件，默认为 [GitHub 仓库](https://github.com/mendix/legacy-mxui-css)。 从这个仓库下载文件以启用您的自定义主题。

{{% alert type="info" %}}
如果您收到错误消息 `CE6103: 我们检测到您的主题没有使用 Atlas UI 。 请检查'疑难解答DOM更改'，以确保您的主题完全符合Mendix 8。 右键单击查看更多选项`，您可以通过右键单击它并选择 **标记为已解决的** 来清除消息。
{{% /报警 %}}

## 4 个焦点特定类已删除

Mendix 8之前，客户端经常将 `mx-focus` 应用于接收焦点的元素，并删除 `mx-focus` 当元素失去焦点时。 因为所有支持的浏览器现在都对 `:focus` 伪类有适当的支持，因此这些重新应用已不再必要。  关于 `:focus`的更多信息，见 Mozilla [:focus 文档](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus)。

如果你在主题中使用 `mx-focus` ，你应该替换为 `:focus`。

像这样代码：

```css
.mx-listview-item.mx-focus {
    /* your styling */
}
```

应更改为:

```css
.mx-listview-item:focus {
    /* your styling */
}
```

## 5 数据网格标记更新

我们对数据网格标记进行了一些更新。 以前，数据网分成两个单独的表格：一个是标头的，另一个是载有数据。 这就减少了数据网格的可访问性，因为屏幕阅读器将它们作为两个单独的表格显示。 现在这两个表格已合并为一个表格。 此外， `div` 包装两个表格已被移除。

另一个数据网格标记变化是，包含工具栏的 `div` 和包含分页栏的 `div` 现在都是逻辑顺序。 以前，需要额外的 CSS 来以正确的顺序显示它们，需要额外的 JavaScript 来决定逻辑标签行为。 目前的结构符合 [Web Content Accessibility Guidelines 2。 第 1.3.2 条标准](https://www.w3.org/TR/WCAG21/#meaningful-sequence) 表示了 [DOM订单跟随了视觉顺序](https://www.w3.org/TR/WCAG20-TECHS/C27.html)

随着新辅助功能的实施，现在 `div` 包含分页部分 (控制栏内) 有适当的 `角色` 属性集。 此 `div`的内置按钮，包括 `div` 本身. 现在有可翻译的 `aria-label` 属性可以从Modeler设置 `System Texts` 页面具有类别名称 `Accessibility` 新的 `shart` and `标题` 元素作为兄弟添加到 *`按钮` 分别用于分页* 和 `thead`。 只显示屏幕阅读器。

这是数据网格的当前标记(不改变代码省略)：

```html
<div class="mx-grid mx-datagrid mx-name-grid1">
    <div class="mx-grid-searchbar" style="display: none;">...</div>
    <div class="mx-grid-controlbar">
        ...
        <div ... role="navigation" aria-label="Pagination(translatable text)">
            <button ...  aria-label="Go to first page(translatable text)"> </button>
            <button ... aria-label="Go to previous page(translatable text)"></button>
            <div ... aria-hidden="true">1 到 20 of 132</div> 
                <span class="sr-only">当前显示(可翻译文本) 1 到 20 of 132</span>
            <button ... aria-label="Go to next page(translatable text)"></button>
            <button ... aria-label="Go to last page(translatable text)"></button>
        </div>
...
    </div>
    <div class="mx-grid-content">
        <table>
            <caption class="sr-only">标题</caption>
            <colgroup>...</colgroup>
            <thead>
                <tr class="mx-name-head-row"></tr>
            </thead>
            <tbody>
                <tr class="mx-name-index-0" >. 。</tr>
            </tbody>
            <tfoot></tfoot>
        </table>
    </div>
</div>
```

此外，表格上的一些其他类已被删除，因为它们很容易使用元素名称访问。

如果您以这种方式将您的数据网格样式：

```css
.mx-datagrid .mx-datagrid-head-table {
    // your styling
}
.mx-datagrid .mx-datagrid-body-table .mx-datagrid-body tr td {
    // your styling
}
```

您应该使用这些准则重写数据网格样式：

```css
.mx-datagrid thead 然后
    // 你的样式
}

.mx-datagrid tbody tr tr power
    // 你的样式
}
```

## 6 列表视图标记更改

列表视图部件的标记也已更改。 为了简化风格，已删除以下类：

* `mx-list`
* `mx列表视图列表`
* `mx-listview-striked`
* `mx-listview-item`
* `mx-listview-search 输入`
* `mx-listview-clearing 按钮`

对于不在选择页面中的参考或参考设置选择器的列表视图。 列表视图的 `mx-listview-selected` 已被删除。 不需要的 `div` 元素与类 `mx-listview-content` 围绕每个列表视图项的内容也已被删除。

列表视图搜索栏的DOM元素的顺序已更正为符合视觉顺序。 搜索输入字段周围的 `div` 元素已被删除。

如果您的列表视图小部件以这种方式样式：

```css
.mx-listview-items volume
    // 你的样式

x-listview-search-inputing inputes 然后再输入
    // 您的样式
}
x-listview-clear-clear-butor Power
    // 你的样式
}
```

您应该使用这些准则重写您的列表视图样式：

```css
.mx-listview li vol
    // 你的样式
}
x-listview-searchbar输入
    // 您的样式
}
x-listview-searchbar 按钮 &#
    // 你的样式
}
```

## 7 滚动容器标记更改

以 `mx-layoutcontainer` 为起点的所有类已从滚动容器中删除，因为它们与 `mx-scrollcontainer` 对应的类是多余的。

## 8 链接按钮标记更改

链接按钮的标记与其他按钮更加一致：

```html
<a href="#" class="mx-link mx-name-actionButton1">
    <span class="glyphicon glyphicon-euro"></span>
    链接按钮
</a>
```

## 9 输入小部件标记更改

每个输入小部件都有一个隐含的表单组结构包裹。 在最近的更改之前，一个输入小部件的 DOM 结构可能会根据其设置而失调。 现在，表单组结构确保输入小部件在数据视图中正确对齐并适当标记。

### 9.1 数据视图上的垂直和水平类

上次， 当 **表单方向** 设置为 **水平** 时，数据视图会渲染 `格式-水平` 类，如果将此选项设置为 **垂直** 则没有此类。 现在， `form-水平` or `form-垂直` 将分别添加到 **水平** 和 **垂直** 选项。

这就更容易通过在您的 CSS 选择器中选择一个类来为不同方向的表单风格(和输入它们)。 如果你以前依赖于 `表面水平的存在或不存在，` 现在您可以通过使用 `表单垂直` 来简化您的 CSS 选择器。

这是数据视图部件的DOM结构现在是如何组织的：

```html
<div class="mx-dataview [form-horizontal or form-vertical]">
    <div class="mx-dataview-content">
        ...
        <div class="form-group"> ... </div>
        <div class="form-group"> ... </div>
        ...
    </div>
    <div class="mx-dataview-controls">
        ...
    </div>
</div>
```

### 9.2 表格组结构

之前, 如果小部件有 **显示标题** 选项设置为 **没有**, 表单组结构缺失 `表单组` 顶级类 `div`

```html
<div class="mx-name-textBox4 [...]" [...]>
    <INPUT-WIDGET />
</div>
```

现在， `form-group` 类与额外 `无列` 类保持不变：

```html
<div class="form-group no allies mx-name-textBox4 [...]" [...]>
    <INPUT-WIDGET />
</div>
```

如果您之前使用 `.form-group` 自定义样式，这可能是一个像 `一样的突破性变化。 orm-group`  现在匹配更多元素。 您现在可以只在水平或只在使用 `的垂直表单上对目标表单组和元素。 orm-水平.form-group` or `.form-垂直.form-group`

### 9.3 输入部件类型类

表单组现在有特殊类名，取决于他们的小部件类型：

* `.mx复选框`
* `.mx-日期选择器`
* `.mx-下拉列表`
* `.mx-inputreferencesetselector`
* `.mx-radiobutongra`
* `.mx引用选择器`
* `.mx-textarea`
* `.mx-文本框`

### 9.4 表组布局实例

垂直表单组输入小部件现在有一个标签、输入控制和可选的验证消息在同一级：

```html
<div class="form-group mx-name-textBox4 [...]" [...]>
    <label class="control-label" for="123_abc">
        标题
    </label>

    <INPUT-CONTROL/>
    <！ - 或者，只读样式文本 -->
    <div class="form-control-static">值</div>

    <！ - 可选：验证消息 -->
    <div class="alert alert-danger mx-validation-message">checkboom</div>
</div>
```

水平表单组输入小部件现在有标签 `col-sm-{labelWith}`和 `div.col-sm-{12-labelWith}` 它的标签还包含输入控制和可选的验证消息：

```html
<div class="form-group mx-name-textBox4 [...]" [...]>
    <label class="control-label col-sm-4" for="123_abc">
        标题
    </label>
    <div class="col-sm-8">
        <INPUT-CONTROL/>
        <！ - 或者，只读样式文本 -->
        <div class="form-control-static">值</div>

        <！ - 可选：验证消息 -->
        <div class="alert alert-danger mx-validation-message">checkboom</div>
    </div>
</div>
```

这是在水平或垂直数据视图中输入部件的结构。 使用 **显示标签** 设置为 **没有**。 输入小部件有一个输入控制和一个可选的验证消息：

```html
<div class="form-group mx-name-textBox4 [...]" [...]>
    <！ - 一个没有标签的表单组仍然是一个表单组 -->

    <INPUT-CONTROL/>
    <！ - 或者，只读样式文本 -->
    <div class="form-control-static">值</div>

    <！ - 可选：验证消息 -->
    <div class="alert alert-danger mx-validation-message">checkboom</div>
</div>
```

### 9.5 只读控制

上次， 有 **只读样式** 的输入小部件不可编辑的输入控制设置为 **文本** 可以使用一个 `p` 或一个 `标签` 包含一个 `表单控制静态` 类的元素呈现出来。

使用 **只读样式** 设置为 **文本** 的只读控制现在呈现如下所示：

```html
<div class="form-control-static">值</div>
```

### 9.6 输入部件结构

以前，一些输入小部件有一个围绕其控制的包装元素。

这些多余的包装器已被移除，现在只要有可能即可放置控制(无线电按钮组中的无线电按钮除外)。 每个单独的控制被包装在一个 `div` 中。

### 9.7 投入控制实例

下面列出了各种输入控制的几个例子。

文本框：

```html
<input class="form-control" type="text" id="123_abc" />
```

文本区域：

```html
<textarea class="form-control mx-textarea-input mx-textarea mx-textarea-input-noresize"></textarea>
```

检查框：

```html
<input type="checkbox" value="" />
```

当 **标签位置** 设置为 **控制后** 时选中复选框(在这种情况下，表格组上的标签未显示)：

```html
<input type="checkbox" id="123_abc" value="" />
<label for="123_abc">标签</label>
```

单选按钮：

```html
<div role="radiogroup" id="123_abc" aria-labelledby="123_abc-label">
    <div class="radio">
        <input type="radio" id="123_abc_0" value="Funghi">
        <label for="123_abc_0">Funghi</label>
    </div>
    <div class="radio">
        <input type="radio" id="123_abc_1" value="Pepperoni">
        <label for="123_abc_1">Pepperoni</label>
    </div>
    <div class="radio">
        <input type="radio" id="123_abc_2" value="Tre_Formaggi">
        <label for="123_abc_2">Tre Formaggi</label>
    </div>
    <div class="radio">
        <input type="radio" id="123_abc_3" value="Margherita">
        <label for="123_abc_3">Margherita</label>
    </div>
</div>
```

下拉：

```html
<select class="form-control">
    <option value=""></option>
    <option value="a1">a1</option>
    <option value="a2">a2</option>
    <option value="a3">a3</option>
</select>
```

## 10 日期选择器部件更改

### 10.1 Input

对日期选择器输入小部件作了以下更改：

* 类 `mx-dateinput` and `mx-dateinput-input` 已经被移除，以利于新的 `mx-compound-control` 类
* `mx-compound-control` 类被引入用于由多个元素组成的输入小部件， 例如输入旁边按钮的小部件
* 内核 `<div>` 含有类的元素 `mx-dateinput-input-wrapper` 围绕输入被删除
* `<button>` 元素在 DOM 输入后被放置以匹配视觉顺序

### 10.2 日历

由于日历弹出窗口不再使用 Dojo 框架实现，因此对日历弹出窗口的内部结构进行了几次更改：

* 所有以 `dijit` 开头的类已被删除
* 最远的 `<div>` 元素现在有类 `mx-日历`
* 代表日历视图中的天数的 `<td>` 元素获得以下类：
    * `mx-calendar-day month-your current`, `mx-calendar-day-play-play-play-three` or `mx-calendar-day-month-through`: 取决于当日、上月还是下个月
    * `mx-calendar-day已选择`: 如果当前日期选择器已打开日历的日期
    * `mx-calendar-day activity`: 如果当前的日子有焦点
* `<span>` 内在 `<td>` 和 `<th>` 元素已被删除

月份标题现在有以下结构：

```html
<div class="mx-calendar-month-header">
    <button class="mx-calendar-month-previous">
        <span class="glyphicon glyphicon-minus"/>
    </button>
    <div class="mx-calendar-month-dropdown">
        <div class="mx-calendar-month-current">
            <div class="mx-calendar-month-spacer">
                <div>January</div>
...
            </div>
            <div class="mx-calendar-month-label">June</div>
        </div>
        <span class="glyphicon glyphicon-chevron-down"/>

        <！ - 仅在单击下拉菜单时渲染——>
        <div class="mx-calendar-month-dropdown-options">
            <div>January</div>
...
        </div>
    </div>
    <button class="mx-calendar-month-next">
        <span class="glyphicon glyphicon-plus"/>
    </button>
</div>
```

年切换器现在具有以下结构：

```html
<div class="mx-calendar-year-switcher">
    <span class="mx-calendar-year-previous">2018</span>
    <span class="mx-calendar-year-selected">2019</span>
    <span class="mx-calendar-year-next">2020</span>
</div>
```

## 11 参考选择器和输入参考集选择器标记更改

已对参考选择器标记作了下列更改：

* `mx-referenceselector` and `mx-referencesetselector` 已经从主 `<div>` 元素支持新的 `mx-compound-control` 类， 它是为由多个元素组成的输入小部件引入的(一个包含多个元素的常用输入小部件是一个旁边的按钮)。

对输入参考集选择器标记作了以下更改：

* 表单组现在将获得类 `mx-referenceselector` or `mx-inputreferesetselector` (注意 `输入` 前缀)
* 內部的 `<div>` 元素(共享一个以 `-input-wrapper`结尾的类被删除)
* `<button>` 元素已经放置在输入DOM后以匹配视觉顺序

## 12个DropDown按钮小部件清理

已对 `DropButton` 小部件作了以下更改：

* 类 `mx-list` 已从对话框中的条目列表中删除
* 类 `mx-down` 已从对话框中删除，因为它与搜索输入中的下拉没有什么关系。

## 13 个文件管理器和图像上传器小部件更改

以前，文件管理器和图像上传器部件在桌面和移动浏览器上呈现出不同的形式。 这些小部件在桌面上呈现为一个简单风格的自定义 HTML 代码片断，而在移动上，它们显示为难于风格的本地文件输入。

文件管理器和图像上传器部件已更改以保持一致性。 现在，他们总是显示相同的 HTML 结构。 此外，这些小部件的DOM结构与其他复合部件更加一致(例如参考选择器和日期选择器)。

现在，文件管理器和图像上传器部件总是作为一个 `div`  元素，其上传类为 `mx-compound-control` 类。 另外， `mx-filefinput` 类已被移动到表单组。 在 `div`中，有一个 `表单控制` 类的输入. 此输入代表当前选定文件的文件名。 类 `mx-包装标签` 来自输入。 在输入旁边，有两个按钮之一用于上传和下载当前文件。 这些按钮与以前相同的类。

## 14 阅读更多

* [疑难解答图集界面更改](migration-atlas)
