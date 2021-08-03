---
title: "原生移动样式"
parent: "本地移动版"
menu_order: 20
description: "本参考指南将在本地移动应用中自定义Mendix 风格元素， 同时解释Mendix小部件的类和风格属性。"
tags:
  - "原生的"
  - "类"
  - "设计"
  - "财产"
  - "样式"
  - "小部件"
  - "studio pro"
---

## 1 导言

本参考指南将在本地移动应用中自定义Mendix 风格元素， 同时解释Mendix小部件的类和风格属性。 学习本机搭配的基础知识， 您可以咨询 [如何实现本地移动式样式](/howto8/mobile/native-styling) 然后跟随 [如何使您的Mendix 本地移动式应用程序](/howto8/mobile/how-to-use-native-styling)。

Mendix 应用程序使用布局来决定页面的外观和功能。 对于本机移动应用，您可以使用本机布局来轻松整合导航和设置以优化本机功能。 欲了解更多布局信息，请参阅 [布局](layout)。

要保持小部件的响应性，Mendix 应用程序使用 Flexbox。 使用Flexbox，组件可以设置子组件的布局。 这允许您的应用在多个表单因素之间保留一个一致的布局。 欲了解更多关于布局的信息，请参阅React Native的 [Flexbox 文档](https://reactnative.dev/docs/flexbox)。

您可以使用 `高度` 和 `宽度` 属性来设置部件组件的尺寸。 欲了解更多关于大小的信息，请参阅React Native的 [高度和宽度文档](https://reactnative.dev/docs/height-and-width)。

## 2 样式对象 {#style-objects}

一个小部件由各种元素组成，每个元素都可以单独设计。 您可以使用样式对象自定义您的部件。 样式对象是具有针对每个部件的一组属性的 JavaScript 对象。 某些属性会重新使用其他元素的属性，例如React的视觉风格、TextStyle、ImageStyle和颜色元素。 当您自定义应用时，您可以咨询以下属性集以获取关于样式属性的更多信息：

* **视图样式** — React Native [视图样式](https://reactnative.dev/docs/view-style-props) 属性集帮助您更改边界，不透明度 和您应用的其他一般方面(视图样式属性集也包含布局、阴影和变换属性)
* **TextStyle** — — React Native的 [Text](https://reactnative.dev/docs/text-style-props) 属性集将允许您使用样式文本——使用这些属性可以控制文本的字体， 选择状态和更多 (文本属性集也包含布局属性)
* **ImageStyle** — React Native's [Image](https://reactnative.dev/docs/image-style-props) property set will allow you to style image from network sources, 一个本地库和临时本地图像 - 使用这些属性，您可以更改图像的大小 更多 图像属性也包含布局属性( `调整大小模式` 值 `重复` 不支持)
* **颜色** — React Native [颜色参考](https://reactnative.dev/docs/colors) 属性集将允许您更改颜色 — 您可以使用红-绿色符号自定义颜色。 更改色调或饱和度，及更多

### 2.1 类名

每个样式对象都有一个名称，称为对象的类名称。 您可以创建新的自定义类，然后通过设置类名称到小部件类属性来应用样式到单个小部件。 您可以在这里看到用于创建 `自定义类名称` 的代码：

```javascript
// 一个自定义样式类
导出const customClassname = }
    container: @un.org
        // 查看样式属性
        paddingTop: 5
    },
    文本：欧共体
        // TextStyle 属性
        字体权重："bold"
    }
}
```

该自定义类可以轻松访问 Mendix Studio 专业版：

{{% image_container width="400" %}}![custom class](attachments/native-styling-refguide/custom-class.png){{% /image_container %}}

当你想要将样式应用于一个小部件的实例时，你可以扩展该小部件的默认类。 每个小部件的默认类都在下面的 [数据小部件](#understanding-data-widgets) 部分中命名。 下面的示例显示如何扩展默认类：

```javascript
导出const ActionButton = Power
    container:vol
        // ViewStyle properties
        borderWid: 3
    },
    字体描述：
        // 文本样式属性
        字体大小：20
    },
};
```

附加组件小部件每个都有基于其完整小部件ID的默认样式类 (在 *{widget name}中找到)。 ml*)，可以通过下划线替换点来创建。 下面的示例显示插件的默认样式类：

```javascript
导出const com_mendix_widget_native_badge_Badge = (Badge = Power
    text:
        // TextStyle 属性
        颜色: "#00FF00",
    }
});
```

关于创建您自己的班级的更多信息 查看 [在 *样式您的Mendix 原生移动应用程序* 中创建您自己的类](/howto8/mobile/how-to-use-native-styling#creating-your-own-classes) 部分。 该文档还显示如何使用自定义类作为设计属性。

## 3 个数据部件 {#understanding-data-widgets}

数据部件对许多Mendix 应用程序至关重要。 这些小部件将允许您的用户创建和处理数据对象，并且可以自定义以满足您的应用需要。

### 3.1 数据视图部件

数据视图小部件显示一个数据对象的内容。 欲了解更多关于这个部件的信息，请参阅 [数据视图](data-view)。这个部件没有用户界面，所以它不支持任何样式。

### 3.2 列表视图部件 {#list-view}

列表视图显示垂直或水平排列对象列表。 欲了解更多关于此部件的信息，请参阅 [List View](list-view)。 这不是默认的列表视图，但是列表视图小部件如何在应用程序中显示：

{{% image_container width="350" %}}![list view](attachments/native-styling-refguide/list-view.png){{% /image_container %}}

这是小部件代码的构建方式：

```xml
<container>
    <listItem>内容</listItem>
    <listItem>内容</listItem>
</container>
```

小部件的样式属性如下：

| 元素       | 样式属性          | 描述                                                                        |
| -------- | ------------- | ------------------------------------------------------------------------- |
| `容器`     | 所有视图样式属性      |                                                                           |
| `容器`     | `numColumns`  | 这是列表应渲染的列数(默认为1)。                                                         |
| `列表项`    | 所有视图样式属性      |                                                                           |
| `列表项`    | `rippleColor` | 这是Android上的波纹的颜色，只有当项目有单击动作设置时才会使用。 否则它将被忽略(默认为 `rgba(0, 0, 0, 0, 0). )`。 |
| `列表项`    | `下颜色`         | 这是在iOS上按下项目时的颜色，只有当项目有单击动作设置时才会使用。 否则它将被忽略，默认仅不透明。                        |
| `列表项已禁用` | 与 `列表项相同的属性`  | 覆盖 `列表项` 样式，如果项目有单击动作，且操作无法执行或禁用。                                         |

样式所有列表视图的默认类命名为 `ListView`。

## 4 个常用部件

在几乎所有应用页面中都使用了常见的小部件。 因为它们无所不在，学习如何风格共同的小部件将对您的应用产生很大的影响。

### 4.1 案文

文本小部件显示可选包含参数的文本。 关于这些小部件的更多信息，见 [文本小部件](text)。 小部件的样式属性如下：

```xml
<container>
    <text>内容</text>
</container>
```

| 元素   | 样式属性                 | 描述 |
| ---- | -------------------- | -- |
| `容器` | 这包含所有视图样式属性。         |    |
| `文本` | 这包含所有的 TextStyle 属性。 |    |

所有文本样式的默认类命名为 `文本`。

### 4.2 图像 {#image}

图像部件可以用于在页面、布局或代码片段上显示预定义的图像。 关于这些小部件的更多信息，请参阅 [图像小部件](image)。 小部件的样式属性如下：

```xml
<container>
    <image/>
</container>
```

| 元素      | 样式属性          | 描述                                                                       |
| ------- | ------------- | ------------------------------------------------------------------------ |
| `容器`    | 这包含所有视图样式属性。  |                                                                          |
| `容器`    | `rippleColor` | 这是Android上的波纹的颜色，仅当容器有单击动作设置时才会使用。 否则它将被忽略(默认为 `rgba(0, 0, 0, 0, 0). )`。 |
| `容器`    | `下颜色`         | 这是在iOS上按下容器时的颜色，只有当容器有点击动作设置时才会使用。 否则它将被忽略，默认仅不透明。                       |
| `容器已禁用` | 与 `容器相同的属性`   | 如果图像在单击操作上有操作且操作无法执行或禁用，则覆盖 `容器` 风格。                                     |
| `图片`    | 这包含所有图像样式属性。  |                                                                          |
| `图片已禁用` | 与 `图像相同的属性`   | 如果图像在单击动作上有操作且操作无法执行或在操作过程中被禁用，则覆盖 `图像` 样式。                              |

所有静态图像风格的默认类命名为 `图像`。 请注意，如下文 [图像查看器](#image-viewer) 部分所述，从模型中加载的图像样式为 `图像查看器`。

### 4.3 页面标题

页面标题小部件显示使用它的页面标题。 这可以是页面本身定义的标题，或者是显示页面时定义的覆盖标题。 欲了解此部件的更多信息，请参阅 [页面标题](page-title)。 小部件的样式属性如下：

```xml
<container>
    <text>页面标题</text>
</container>
```

| 元素   | 样式属性                 | 描述 |
| ---- | -------------------- | -- |
| `容器` | 这包含所有视图样式属性。         |    |
| `文本` | 这包含所有的 TextStyle 属性。 |    |

样式所有页面标题的默认类命名为 `页面标题`。

### 4.4 布局网格

布局网格插件可以用于构建您页面上的内容。 您可以创建可以配置为固定或动态大小的行和列。

小部件的样式属性分为几个对象： `Layoutgrid`, `行`, `nottersRow`, `col`, `colFitToContent`, `col1`, `col2`, `col3`, `col4`, `col5`, `col6`,  `col7`, `col8`, `col9`, `col10`, `col11`, `col12`和 `notters`。

`当列上的宽度属性为“自动填充”时，正在应用col`。

`colFitToContent` 正在应用当列上的宽度属性为“自动适合内容”。

`col1`, `col2`, `col3`, `col4`, `col5`, `col6`,  `col7`, `col8`, `col9`, `col10`, `col11`, `col12` 当列属性上的宽度为“手动”时适用。 基于相关大小属性只应用了一个类。

`nottersRoow` (Row) and `noGutters` (Column) 正在应用当行列属性之间的间距设置为“否”。

主 `Layoutgrid`:

```xml
<container></container>
```

`行`, `nottersRow`:

```xml
<container></container>
```

`col`, `colFitToContent`, `col1`, `col2`, `col3`, `col4`, `col5`, `col6`,  `col7`, `col8`, `col9`, `col10`, `col11`, `col12`, `notters`:

```xml
<container></container>
```

生成的 DOM 看起来像这样：

```xml
<container>
    <row>
        <col></col>
    </row>
</container>
```

## 5 容器部件

容器部件是一组工具，允许您为页面内容提供结构。 下面还有一个叫做容器部件的特定部件。 关于这些部件的更多信息，见 [容器部件](container-widgets)。

### 5.1 容器

容器部件可以用来样式或隐藏一组部件。 默认情况下，这个部件没有视觉演示文稿，不过样式可以用来添加间距。 小部件的样式属性如下：

```xml
<container>
    内容
</container>
```

| 元素      | 样式属性          | 描述                                                                       |
| ------- | ------------- | ------------------------------------------------------------------------ |
| `容器`    | 这包含所有视图样式属性。  |                                                                          |
| `容器`    | `rippleColor` | 这是Android上的波纹的颜色，仅当容器有单击动作设置时才会使用。 否则它将被忽略(默认为 `rgba(0, 0, 0, 0, 0). )`。 |
| `容器`    | `下颜色`         | 这是在iOS上按下容器时的颜色，只有当容器有点击动作设置时才会使用。 否则它将被忽略，默认仅不透明。                       |
| `容器已禁用` | 与 `容器相同的属性`   | 如果在单击操作集中，且操作无法执行或禁用，则此选项将覆盖 `容器` 风格。                                    |

样式所有页面标题的默认类命名为 `Container`。

### 5.2 标签容器 {#tab-container}

标签容器用于显示分类到多个标签页的信息。 标签容器可以帮助显示超出设备屏幕空间的信息。 这是默认标签容器小部件在应用程序中可以看到的方式：

{{% image_container width="350" %}}![tab container](attachments/native-styling-refguide/tab-container.png){{% /image_container %}}

这是小部件代码的构建方式：

```xml
<container>
    <tabBar>
        <tab>
            <activeLabel>PAGE 1</activeLabel>
            <badgeContainer><badgeCaption /></badgeContainer>
        </tab>
        <tab>
            <label>PAGE 2</label>
        </tab>
        <indicator>
    <tabBar>
    content
</container>
```

小部件的样式属性如下：

| 元素       | 样式属性                 | 描述                                            |
| -------- | -------------------- | --------------------------------------------- |
| `容器`     | 这包含所有视图样式属性。         |                                               |
| `tabBar` | 这包含所有视图样式属性。         |                                               |
| `tabBar` | `弹出`                 | 这是一个布尔值，表示标签栏是否在滚动时退出。                        |
| `tabBar` | `press彩色`            | 这是材料riple (仅Android 版)的颜色。                    |
| `tabBar` | `压力不透明度`             | 这是按下标签页的不透明度。                                 |
| `tabBar` | `启用滚动`               | 这是一个启用滚动标签的布尔值。                               |
| `tabBar` | `制表符位置`              | 这是标签视图中标签栏的位置。 和可能的值是 `顶部` 和 `底部` (默认为 `顶部`)。 |
| `指标`     | 这包含所有视图样式属性。         |                                               |
| `tab`    | 这包含所有视图样式属性。         |                                               |
| `标签`     | 这包含所有的 TextStyle 属性。 |                                               |
| `活动标签`   | 这包含所有的 TextStyle 属性。 |                                               |
| `徽章容器`   | 这包含所有视图样式属性。         |                                               |
| `徽章标题`   | 这包含所有的 TextStyle 属性。 |                                               |

样式所有标签容器的默认类命名为 `标签容器`。

### 5.3 滚动容器

一个滚动容器用于启用一个页面的一部分滚动。 默认情况下，这个部件没有视觉演示文稿，不过样式可以用来添加间距。  小部件的样式属性如下：

```xml
<container>
    可滚动的内容
</container>
```

| 元素   | 样式属性         | 描述 |
| ---- | ------------ | -- |
| `容器` | 这包含所有视图样式属性。 |    |

样式所有滚动容器的默认类名为 `ScrollContainer`。

## 6 输入部件

输入小部件通常用于向用户显示数据并允许他们编辑数据。 关于这些小部件的更多信息，请参阅 [输入小部件](input-widgets)。

### 6.1 文本框 {#text-box}

文本框可以用于显示或编辑文本值。 这是一个带验证反馈的文本框小部件和纯文本框小部件在应用中可以看到的方式：

{{% image_container width="350" %}}![text box](attachments/native-styling-refguide/text-box.png){{% /image_container %}}

小部件的样式属性结构如下：

```xml
<container>
    <label>文本框</label>
    <inputError>内容无效</inputError>
    <validationMessage>输入验证反馈</validationMessage>
</container>
<container>
    <label>文本框</label>
    <input>有效文本</input>
</container>
```

| 元素           | 样式属性                 | 描述                                                                                                                                      |
| ------------ | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `容器`         | 这包含所有视图样式属性。         |                                                                                                                                         |
| `容器已禁用`      | 与 `容器相同的属性`          | 如果文本框不可编辑，则覆盖 `容器` 风格。                                                                                                                  |
| `input`      | 这包含所有的 TextStyle 属性。 |                                                                                                                                         |
| `input`      | `自动Capitalize`       | 当用户类型的时候, 这会自动大写某些字符:<br><br>* `字符`: 大写所有字符<br>* `单词`: 大写每个单词的第一个字母<br>* `句子`: 大写每个句子的第一个字母(默认)<br>* `No` |
| `input`      | `占位符文本颜色`            | 这是占位符字符串的文本颜色。                                                                                                                          |
| `input`      | `选择颜色`               | 这是文本输入的高亮和光标颜色。                                                                                                                         |
| `input`      | `下划线颜色安卓系统`          | 这是 `输入` 下划线的颜色。                                                                                                                         |
| `输入焦点`       | 与 `输入相同的属性`          | 覆盖 `输入` 样式，如果文本框被聚焦(Studio Pro v8.15)。                                                                                                  |
| `inputError` | 这个属性与 `输入相同`         | 如果验证错误，覆盖 `输入的` 样式。                                                                                                                     |
| `Input禁用`    | 与 `输入相同的属性`          | 如果文本框不可编辑，则覆盖 `输入的` 样式。                                                                                                                 |
| `标签`         | 这包含所有的 TextStyle 属性  |                                                                                                                                         |
| `标签`         | `编号OfLines`          | 这是要包装标签文本的最大行数。 如果案文更长了，它将被省略线切断(默认为1)。                                                                                                 |
| `标签已禁用`      | 与 `标签相同的属性`          | 如果文本框不可编辑，则覆盖 `标签` 样式。                                                                                                                  |
| `验证消息`       | 这包含所有的 TextStyle 属性。 |                                                                                                                                         |

所有文本框样式的默认类命名为 `TextBox`。

### 6.2 文本区

文本框可以用于显示或编辑带多行的文本值。 这个小部件支持与上面的 [文本框](#text-box) 小部件相同的样式属性和结构。 这是一个带验证反馈的文本区域小部件和纯文本区域小部件在应用中的显示方式：

{{% image_container width="350" %}}![text area](attachments/native-styling-refguide/text-area.png){{% /image_container %}}

所有文本区域样式的默认类命名为 `TextArea`。

### 6.3% {#drop-down}

下拉是一个可用于显示和编辑枚举属性的输入小部件。

自Studio Pro v8.11以来，下拉窗口小部件有一个新的风格属性，名为 `Use UniformDesign: boolan` 让两个平台都有一个统一的设计。

小部件的渲染层次结构如下为非一致性：

```xml
<container>
    <label>Drop down enumeration</label>
    <value>Content invalid</value>
    <validationMessage>Validation feedback enumeration</validationMessage>
</container>
<picker>
    <pickerBackdropIOS/>
    <pickerTopIOS><button>close</button></pickerTopIOS>
    <pickerIOS>
        <pickerItemIOS>First</pickerItemIOS>
        <pickerItemIOS>Second</pickerItemIOS>
        <pickerItemIOS>Third</pickerItemIOS>
    </pickerIOS>
</picker>
```

小部件的渲染层次结构如下为一致性：

```xml
<container>
    <label>Drop down enumeration</label>
    <valueContainer>
        <value>First</value>
    <icon/>
    </valueContainer>
    <validationMessage>Validation feedback enumeration</validationMessage>
</container>
<menuWrapper>
    <selectedItemContainer>
        <selectedItem>First</selectedItem>    <= Selected
    </selectedItemContainer>
    <itemContainer>
        <item>Second</item>
    </itemContainer>
    <itemContainer>
        <item>Third</item>
    </itemContainer>
</menuWrapper>
```

| 元素             | 样式属性                    | 描述                                          |
| -------------- | ----------------------- | ------------------------------------------- |
| `容器`           | 这包含所有视图样式属性。            |                                             |
| `容器已禁用`        | 与 `容器相同的属性`             | 如果下拉菜单不可编辑，则覆盖 `容器` 样式。                     |
| `标签`           | 这包含所有的 TextStyle 属性。    |                                             |
| `标签`           | `编号OfLines`             | 打包标签文本的最大行数。 如果文本已经存在，它将被椭圆切断。 默认为 `1`。     |
| `标签已禁用`        | 与 `标签相同的属性`             | 如果下拉功能不可编辑，则覆盖 `标签` 样式。                     |
| `选取的 IOS`      | 这包含所有视图样式属性。            |                                             |
| `选择器后台IOS`     | 这包含所有视图样式属性。            |                                             |
| `选取主题`         | 这包含所有视图样式属性。            |                                             |
| `验证消息`         | 这包含所有的 TextStyle 属性。    | 样式验证消息(Studio Pro v8.11)。                   |
| `值`            | 这包含所有的 TextStyle 属性     | 切换下拉菜单项和选取器IOS 项的值按钮样式。 如果选择占位符，占位符文本颜色将被应用 |
| `使用统一设计`       | `boolean`               | 启用新的校服设计(与Studio Pro v8.11一起)。              |
| `图标样式`         | 这包含所有的 TextStyle 属性     | 在值旁边的箭头图标样式(Studio Pro v8.15)。              |
| `值`            | `占位符文本颜色：字符串`           | 如果选择占位符，占位符文本颜色将被应用(Studio Pro v8.11)。      |
| `对焦值`          | 与 `值相同的属性`              | 如果下拉框被聚焦，则覆盖 `的值` 样式。 （Studio Pro v8.15）。   |
| `值容器`          | 这包含所有视图样式属性 & ripplle彩色 | 给值按钮的容器样式(Studio Pro v8.11)。                |
| `值容器聚焦于`       | 与 `值容器相同的属性`            | 重写 `值容器` 样式，如果下拉菜单被聚焦(Studio Pro v8.15)。    |
| `menuWrapper`  | 这包含所有视图样式属性             | 所有菜单项的包装器视图样式(Studio Pro v8.11)。            |
| `项目容器`         | 这包含所有视图样式属性             | 下拉菜单中的所有项目容器样式，包括选定的项目容器(Studio Pro v8.11)。 |
| `项目`           | 这包含所有 TextStlye 属性      | 在下拉菜单中设置所有项目的样式，包括所选项目 (Studio Pro v8.11)。  |
| `selectedItem` | 这包含所有的 TextStyle 属性     | 下拉菜单中选中项目的样式(Studio Pro v8.11)。             |
| `已选项目容器`       | 这包含所有视图样式属性             | 在下拉菜单中所选项目的容器样式(Studio Pro v8.11)。          |

### 6.4 复选框

复选框输入小部件可以用于显示和编辑布尔属性，并呈现为开关。 这是一个复选框小部件可以在应用程序中看到的方式：

{{% image_container width="350" %}}![check box](attachments/native-styling-refguide/check-box.png){{% /image_container %}}

小部件的样式属性结构如下：

```xml
<container>
    <label>布尔开关</label>
    <inputError>
        <trackColorOff/>
        <thumbColorOff/>
    </inputError>
    <validationMessage>反馈开关输入</validationMessage>
</container>
<container>
    <label>有效布尔值</label>
    <input>
        <trackColorOn/>
        <thumbColorOn/>
    </input>
</container> </container>
```

| 元素           | 样式属性                 | 描述                                      |
| ------------ | -------------------- | --------------------------------------- |
| `容器`         | 这包含所有视图样式属性。         |                                         |
| `容器已禁用`      | 与 `容器相同的属性`          | 如果文本框不可编辑，则覆盖 `容器` 风格。                  |
| `input`      | 这包含所有的 TextStyle 属性。 |                                         |
| `input`      | `trackColoron`       | 开启时切换曲目的自定义颜色。                          |
| `input`      | `trackColoroff`      | 关闭时切换曲目的自定义颜色。                          |
| `input`      | `thumbColorOn`       | 开启时前景开关的颜色。 如果设置为 iOS，开关抓取将丢失阴影。        |
| `input`      | `thumbColorOff`      | 关闭时前景开关的颜色。 如果设置为 iOS，开关抓取将丢失阴影。        |
| `inputError` | 这个属性与 `输入相同`         | 如果验证错误，覆盖 `输入的` 样式。                     |
| `Input禁用`    | 这个属性与 `输入相同`         | 复选框不可编辑时覆盖 `输入的` 样式。                    |
| `标签`         | 这包含所有的 TextStyle 属性  |                                         |
| `标签`         | `编号OfLines`          | 打包标签文本的最大行数。 如果文本已经存在，它将被椭圆切断。 默认为 `1`。 |
| `标签已禁用`      | 与 `标签相同的属性`          | 如果复选框不可编辑，则覆盖 `标签` 样式。                  |
| `验证消息`       | 这包含所有的 TextStyle 属性。 |                                         |

所有复选框输入样式的默认类命名为 `复选框`。

### 6.5 日期选择器

日期选择器是一个可用于显示和编辑日期或时间属性的输入部件。 这是一个日期选择器小部件在应用程序中可以看到的方式：

{{% image_container width="300" %}}![date picker](attachments/native-styling-refguide/date-picker.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <label>下拉枚举</label>
    <value>内容无效</value>
    <validationMessage>验证反馈计数</validationMessage>
    <pickerBackdropIOS>iOS 选择器模式阴影容器
        <pickerIOS>iOS 选择器
            <pickerTopIOS>iOS 选择器模式标题</pickerTopIOS>
        </pickerIOS>
    </pickerBackdropIOS>
</container>
```

| 元素         | 样式属性                 | 描述                                                            |
| ---------- | -------------------- | ------------------------------------------------------------- |
| `容器`       | 这包含所有视图样式属性。         |                                                               |
| `容器已禁用`    | 与 `容器相同的属性`          | 如果日期选择器不可编辑，则覆盖 `容器` 风格。                                      |
| `标签`       | 这包含所有的 TextStyle 属性。 |                                                               |
| `标签`       | `编号OfLines`          | 这是要包装标签文本的最大行数。 如果文本更长了，它将被省略线切断(默认为 `1`。)                    |
| `标签已禁用`    | 与 `标签相同的属性`          | 如果日期选择器不可编辑，则覆盖 `标签` 样式。                                      |
| `值`        | 这包含所有的 TextStyle 属性  |                                                               |
| `值`        | `rippleColor`        | 这是Android上的波纹的颜色。 并且只在按下日期选择器时才会应用(默认为 `rgba(0, 0, 0, 0). )`。 |
| `值`        | `下颜色`                | 当按下 iOSS 上的日期选择器时使用这种颜色，如果不设置它将被默认设置为仅透明的话。                   |
| `值已禁用`     | 这包含所有的 TextStyle 属性  | 如果日期选择器不可编辑，则覆盖 `值` 风格。                                       |
| `占位符`      | 这包含所有的 TextStyle 属性  |                                                               |
| `占位符已禁用`   | 这包含所有的 TextStyle 属性  | 如果日期选择器不可编辑，则覆盖 `占位符` 风格。                                     |
| `验证消息`     | 这包含所有的 TextStyle 属性  |                                                               |
| `选择器后台IOS` | 这包含所有视图样式属性          |                                                               |
| `选取的 IOS`  | 这包含所有视图样式属性          |                                                               |
| `选取的 IOS`  | `颜色`                 |                                                               |
| `选取主题`     | 这包含所有视图样式属性          |                                                               |

默认的类来样式所有日期选择器输入为 `日期选择器`。

### 6.6 参考选择器

参考选择器是一个可用于显示和编辑关联的输入小部件。 关于此部件的更多信息，请参阅 [参考选择器](reference-selector)。 这个小部件支持与上面 [下拉](#drop-down) 小部件相同的样式属性和结构。

所有引用选择器输入样式的默认类命名为 `ReferenceSelector`。

## 7 个文件部件

文件小部件帮助您的用户应用管理图像和其他文件。 关于这些部件的更多信息，请参阅 [文件小部件](file-widgets)。

### 7.1 图像查看器 {#image-viewer}

图像查看器可以用来显示图像。 这个小部件支持与上面的 [图像](#image) 小部件相同的样式属性和结构。

样式所有图像查看器的默认类命名为  `图像查看器`。

## 8 按钮部件

按钮小部件帮助您的用户执行操作。 关于这些小部件的更多信息，请参阅 [按钮小部件](button-widgets)。

### 8.1 动作按钮

一个动作按钮可以执行各种动作，如呼叫nanoflow，打开一个页面。

{{% image_container width="350" %}}![action button](attachments/native-styling-refguide/action-button.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <icon/><caption>主要</caption>
</container>
```

| 元素      | 样式属性                 | 描述                                                                                                                              |
| ------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `容器`    | 这包含所有视图样式属性。         |                                                                                                                                 |
| `容器`    | `rippleColor`        | 这是Android上的波纹的颜色(默认为 `rgba(0, 0, 0, 0.2)`)。                                                                                     |
| `容器`    | `下颜色`                | 按下 iOSS 按钮时使用此颜色，如果不设置此颜色将被默认设置为仅透明度。                                                                                           |
| `容器已禁用` | 与 `容器相同的属性`          | 如果按键设置了单击动作且无法执行或设置为 `则覆盖 <code>容器` 样式。在动作中禁用</code>。                                                                        |
| `标题`    | 这包含所有的 TextStyle 属性。 |                                                                                                                                 |
| `标题已禁用` | 与 `标题相同的属性`          | 如果按键设置了单击动作且无法执行或设置为 `则覆盖 <code>标题` 样式。在动作中禁用</code>。                                                                        |
| `图标`    | 这包含所有视图样式属性。         |                                                                                                                                 |
| `图标`    | `大小`                 | 这是按钮图标的大小(默认为 `12`)。                                                                                                            |
| `图标`    | `颜色`                 | 这是按钮图标的颜色。                                                                                                                      |
| `图标已禁用` | 与 `图标相同`             | Overrides `icon` styles if the button has on click action set and it cannot be executed or is set with `Disable during action`. |

样式所有动作按钮的默认类命名为 `ActionButton`。 然而，标题中的动作按钮有默认类 `ActionButtonader`。

## 9 页 {#pages}

到样式页面，您可以将类添加到页面或它的布局。 状态栏和页眉是页面的一部分，也可以以这种方式设计。

```xml
<page>
    <statusBar/>
    <header/>
    <container>
        应用程序内容
    </container>
</page>
```

| 元素    | 样式属性         | 描述                                       |
| ----- | ------------ | ---------------------------------------- |
| `状态栏` | `barStyle`   | 状态栏的风格可以是 `深色内容` (黑色文本) 或 `浅色内容` (白色文本)。 |
| `状态栏` | `背景颜色`       | 状态栏的背景颜色 (仅安卓)                           |
| `标题`  | `容器`         | 这包含所有视图样式属性。                             |
| `标题`  | `标题`         | 这包含所有的 TextStyle 属性。                     |
| `标题`  | `背面按钮文本`     | 这包含所有的 TextStyle 属性。                     |
| `标题`  | `背面按钮图标`     | 这包含所有图像样式属性。                             |
| `容器`  | 这包含所有视图样式属性。 |                                          |

布局和页面的默认类是 `布局` 和 `页面`。

## 10 Navigation {#navigation-widget}

导航由底部栏(允许用户在您的应用程序内导航)和进度叠加(可以在等待加载时显示加载指示器)。 这是导航在应用中可以看起来的方式：

{{% image_container width="300" %}}![navigation widget](attachments/native-styling-refguide/nav-widget.png){{% /image_container %}}

导航样式属性如下：

```xml
<app>
    <page/>
    <bottomBar/>
<app>
<progressOverlay>
    <background>
        <container>
            <activityIndicator/>
            <text/>
        </container>
    </background>
</progressOverlay>
```

| 元素                | 样式属性    | 描述                                     |
| ----------------- | ------- | -------------------------------------- |
| `bottomBar`       | `容器`    | 这包含所有视图样式属性。                           |
| `bottomBar`       | `标签`    | 这包含所有的 TextStyle 属性。                   |
| `bottomBar`       | `选择的标签` | 这包含所有的 TextStyle 属性。                   |
| `bottomBar`       | `图标`    | 这包含所有视图样式属性。                           |
| `bottomBar`       | `选中图标`  | 这包含所有视图样式属性。                           |
| `progressOverlay` | `二. 背景` | 这包含所有视图样式属性。                           |
| `progressOverlay` | `容器`    | 这包含所有视图样式属性。                           |
| `progressOverlay` | `活动指示器` | 这与 [活动指示器](#activity-indicator) 小部件相同。 |
| `progressOverlay` | `文本`    | 这包含所有的 TextStyle 属性。                   |

导航样式的默认类命名为  `导航样式`。 在导航上不支持自定义类样式。

## 11 附加组件小部件

附加组件会通过 [原生移动资源](/appstore/modules/native-mobile-resources) 模块分发，它不会通过 Mendix Studio Pro 发送。 其他附加组件也可以通过应用模板以及从其他项目导入页面的模块进行分配。

### 11.1 活动指标 {#activity-indicator}

活动指示小部件显示循环加载指示器。 这是一个活动指示器小部件可以在应用程序中看到的方式：

{{% image_container width="350" %}}![activity indicator](attachments/native-styling-refguide/activity-indicator.png){{% /image_container %}}

小部件的样式属性如下：

```javascript
<container>
    <indicator/>
</container>
```

| 元素   | 样式属性         | 描述                               |
| ---- | ------------ | -------------------------------- |
| `容器` | 这包含所有视图样式属性。 |                                  |
| `指标` | `颜色`         | 这是指示器的颜色(默认为 `灰色`)。              |
| `指标` | `大小`         | 指示器的可能值是 `大的` 和 `小的` (默认为 `大的`)。 |

所有活动指示器样式的默认类命名 `com_mendix_widget_native_activityindicator_ActivityIndicator`。

### 11.2 应用事件

应用事件小部件允许您在您的应用网络状态被更改时设置动作，并允许您设定动作调用限制。 这个小部件没有用户界面，所以不支持任何样式。

### 11.3 背景图像

背景图像小部件可以将一个或多个部件放置在图像顶部。

小部件的样式属性如下：

```javascript
<container>
    <image />
</container>
```

| 元素   | 样式属性         | 描述                         |
| ---- | ------------ | -------------------------- |
| `容器` | 这包含所有视图样式属性。 |                            |
| `图片` | 这包含所有图像样式属性。 |                            |
| `图片` | `svgColor`   | 设置 SVG 图像颜色的属性 (默认为 `黑色`)。 |

所有背景图像样式的默认类命名 `com_mendix_widget_native_backgroundimage_BackgroundImage_BackgroundImage`。

### 11.4 徽章

徽章小部件以徽章形式显示文本或值。 这是一个徽章小部件在应用中可以看到的方式：

{{% image_container width="350" %}}![badge](attachments/native-styling-refguide/badge.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <text>新</text>
</container>
```

| 元素   | 样式属性                 | 描述 |
| ---- | -------------------- | -- |
| `容器` | 这包含所有视图样式属性。         |    |
| `文本` | 这包含所有的 TextStyle 属性。 |    |

所有徽章样式的默认类命名为 `com_mendix_widget_native_badge_Badge`。

### 11.5 条码扫描器

条形码扫描器小部件允许应用扫描条形码和二维码。 这个小部件以风格容器渲染相机视图。

小部件的样式属性如下：

```javascript
<container>
        <mask />
<container />
```

| 元素   | 样式属性         | 描述                                      |
| ---- | ------------ | --------------------------------------- |
| `容器` | 这包含所有视图样式属性。 |                                         |
| `掩码` | 这只允许下面的属性。   |                                         |
| `掩码` | `颜色`         | 设置面具边框指示器颜色的属性(默认为 `#62B1F6`)。          |
| `掩码` | `width`      | 设置条形码阅读器宽度的属性。                          |
| `掩码` | `高度`         | 设置条形码阅读器高度的属性。                          |
| `掩码` | `背景颜色`       | 设置遮罩背景颜色的属性 (默认为 `rgba(0, 0, 0, 0.6)`)。 |

样式所有条形码扫描小部件的默认类名称， `com_mendix_widget_native_barcodescanner`。

### 11.6 反馈

反馈小部件允许用户提供直接反馈。 这是一个反馈小部件在应用程序中可以看到的方式：

{{% image_container width="350" %}}![feedback](attachments/native-styling-refguide/feedback-two.png){{% /image_container %}}

小部件的样式属性如下：

| 元素              | 样式属性                 | 描述                                 |
| --------------- | -------------------- | ---------------------------------- |
| `浮动按钮`          | 这包含所有视图样式属性。         |                                    |
| `对话框`           | 这包含所有视图样式属性。         |                                    |
| `标题`            | 这包含所有的 TextStyle 属性。 |                                    |
| `textAreaInput` | 这包含所有的 TextStyle 属性。 |                                    |
| `textAreaInput` | `占位符文本颜色`            | 这是占位符字符串的文本颜色。                     |
| `textAreaInput` | `选择颜色`               | 这是文本输入的高亮和光标颜色。                    |
| `textAreaInput` | `下划线颜色安卓系统`          | 这是Android 设备的下划线颜色。                |
| `textAreaInput` | `编号OfLines`          | 这是文本区域的高度，以这个文本行数为基础。              |
| `切换标签`          | 这包含所有的 TextStyle 属性。 |                                    |
| `切换输入`          | 这包含所有的 TextStyle 属性。 |                                    |
| `切换输入`          | `trackColoron`       | 开启时切换曲目的自定义颜色。                     |
| `切换输入`          | `trackColoroff`      | 关闭时切换曲目的自定义颜色。                     |
| `切换输入`          | `thumbColorOn`       | 开启时这是前景开关的颜色。 如果设置为 iOS，开关抓取将丢失阴影。 |
| `切换输入`          | `thumbColorOff`      | 开关时这是前景开关的颜色。 如果设置为 iOS，开关抓取将丢失阴影。 |
| `按钮`            | `边框颜色`               | 这是对话框按钮边界的颜色。                      |
| `按钮`            | `borderWidth`        | 这是对话框按钮边界的宽度。                      |
| `按钮`            | `颜色`                 | 这是对话框按钮文本的颜色。                      |
| `按钮已禁用`         | `颜色`                 | 禁用时这是对话框按钮文本的颜色。                   |
| `活动指示器`         | `颜色`                 | 这是提交反馈时显示的活动指示器的颜色。                |

样式所有反馈小部件的默认类命名 `com_mendix_widget_native_feedback_反馈`。

### 11.7 浮动操作按钮

浮动动动动作按钮可以让您自定义浮动动动作按钮的外观和功能。 小部件的样式属性如下：

| 元素                     | 样式属性                 | 描述                |
| ---------------------- | -------------------- | ----------------- |
| `容器`                   | 这包含所有视图样式属性。         |                   |
| `按钮`                   | 这包含所有视图样式属性。         |                   |
| `按钮`                   | `大小`                 | 这是按钮的半径。          |
| `按钮`                   | `rippleColor`        | 这是Android上的波纹的颜色。 |
| `按钮图标`                 | 这包含所有图像样式属性。         |                   |
| `次要按钮`                 | 这包含所有视图样式属性。         |                   |
| `次要按钮`                 | `大小`                 | 这是次要按钮的半径。        |
| `次要按钮图标`               | 这包含所有图像样式属性。         |                   |
| `次要按钮字幕`               | 这包含所有的 TextStyle 属性。 |                   |
| `次要按钮CaptionContainer` | 这包含所有视图样式属性。         |                   |

所有浮动动动作按钮样式的默认类命名 `com_mendix_widget_native_floatingactionbuton_FloatingAction按钮`。

### 11.8 地图

地图小部件支持各种数字地图提供者。 这是一个地图小部件可以在应用中看到的方式：

{{% image_container width="350" %}}![maps](attachments/native-styling-refguide/maps.png){{% /image_container %}}

小部件的样式属性如下：

| 元素               | 样式属性         | 描述           |
| ---------------- | ------------ | ------------ |
| `容器`             | 这包含所有视图样式属性。 |              |
| `loadingOverlay` | 这包含所有视图样式属性。 |              |
| `加载指示器`          | `颜色`         | 这是加载指示器的颜色。  |
| `标记`             | `颜色`         | 这是位置标记的颜色。   |
| `标记`             | `不透明度`       | 这是位置标记的不透明度。 |

所有地图部件样式的默认类命名 `com_mendix_widget_native_maps_Maps`。

### 11.9 通知

通知小部件允许您在应用中显示自定义消息。 这个小部件没有用户界面，所以不支持任何样式。

### 11.10 进度条

进度栏小部件显示进度百分比。 这是进度条小部件可以在应用程序中看到的方式：

{{% image_container width="300" %}}![progress bar](attachments/native-styling-refguide/progress-bar.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <bar><fill/></bar>
    <validationMessage/>
</container>
```

| 元素     | 样式属性                 | 描述              |
| ------ | -------------------- | --------------- |
| `容器`   | 这包含所有视图样式属性。         |                 |
| `条形图`  | 这包含所有视图样式属性。         |                 |
| `填充`   | `背景颜色`               | 这是填充进度条部分的背景颜色。 |
| `验证消息` | 这包含所有的 TextStyle 属性。 |                 |

样式所有进度条的默认类命名 `com_mendix_widget_native_progressbar_ProgressBar`。

### 11.11 进步圆

进度圈小部件在一个循环中显示正值或负值的进展。 这是进度圈小部件可以在应用程序中看到的方式：

{{% image_container width="300" %}}![progress circle](attachments/native-styling-refguide/progress-circle.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <circle><fill/></circle>
    <validationMessage/>
</container>
```

| 元素     | 样式属性                 | 描述                |
| ------ | -------------------- | ----------------- |
| `容器`   | 这包含所有视图样式属性。         |                   |
| `圆圈`   | `大小`                 | 这是进度圈的半径。         |
| `圆圈`   | `borderWidth`        | 这是进度圈的边框宽度。       |
| `圆圈`   | `边框颜色`               | 这是进度圆边框的颜色。       |
| `填充`   | `背景颜色`               | 这是圆圈填充部分的颜色。      |
| `填充`   | `width`              | 这是进度圈的宽度。         |
| `填充`   | `线性圆角`               | 这决定了旋转线前端是否已四舍五入。 |
| `文本`   | 这包含所有的 TextStyle 属性。 |                   |
| `验证消息` | 这包含所有的 TextStyle 属性。 |                   |

所有进度圈样式的默认类命名 `com_mendix_widget_native_progresscircle_ProgressCircle`。

### 11.12 QR Code

二维码小部件生成基于一个值的二维码，然后用户可以扫描。 这是一个二维码小部件在应用程序中可以看到的方式：

{{% image_container width="350" %}}![qr code](attachments/native-styling-refguide/qr-code.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <qrcode/>
</container>
```

| 元素       | 样式属性         | 描述          |
| -------- | ------------ | ----------- |
| `容器`     | 这包含所有视图样式属性。 |             |
| `qrcode` | `大小`         | 二维码的大小。     |
| `qrcode` | `颜色`         | 二维码的颜色。     |
| `qrcode` | `背景颜色`       | 二维码背后的背景颜色。 |

样式所有二维码的默认类命名 `com_mendix_widget_native_qrcode_QRCode`。

### 11.13 Range Slider {#range-slider}

范围滑块小部件允许您使用滑块更改范围内的最大和最小绑定值。 这是一个范围滑块小部件可以在应用程序中看到的方式：

{{% image_container width="300" %}}![range slider](attachments/native-styling-refguide/range-slider.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <track><highlight/><marker/></track>
    <validationMessage/>
</container>

<container>
    <trackDisabled><highlightDisabled/><markerDisabled/></trackDisabled>
    <validationMessage/>
</container>
```

| 元素         | 样式属性                 | 描述 |
| ---------- | -------------------- | -- |
| `容器`       | 这包含所有视图样式属性。         |    |
| `曲目`       | 这包含所有视图样式属性。         |    |
| `Track已禁用` | 这包含所有视图样式属性。         |    |
| `高亮显示`     | 这包含所有视图样式属性。         |    |
| `高亮已禁用`    | 这包含所有视图样式属性。         |    |
| `标记`       | 这包含所有视图样式属性。         |    |
| `标记激活`     | 这包含所有视图样式属性。         |    |
| `标记已禁用`    | 这包含所有视图样式属性。         |    |
| `验证消息`     | 这包含所有的 TextStyle 属性。 |    |

样式所有滑块输入的默认类命名 `com_mendix_widget_native_rangeslider_RangeSlider`。

### 11.14 安全区域视图

安全区域视图小部件防止内容在不需要的区域中，例如在环形屏幕边缘或节点后面。 这个小部件仅在 iOS 应用程序上支持。 注意 `容器` 样式只适用于安全区域。

小部件的样式属性如下：

```xml
<container>内容</container>
```

| 元素   | 样式属性         | 描述 |
| ---- | ------------ | -- |
| `容器` | 这包含所有视图样式属性。 |    |

样式所有安全区域视图的默认类命名 `com_mendix_widget_native_safeareaview.SafeAreaView`。

### 11.15 滑块

滑块小部件允许您使用滑块更改数字值。 这是一个滑块小部件在应用程序中可以看到的方式：

{{% image_container width="300" %}}![slider](attachments/native-styling-refguide/slider.png){{% /image_container %}}

这个小部件支持上面的 \[range slider\] (#range-slider) 小部件相同的样式属性。

样式所有滑块输入的默认类命名 `com_mendix_widget_native_slider_Slider`。

### 11.16 评分

评分小部件允许用户对对象从 0 到 5 评分。 这是一个评级小部件在应用中可以看到的方式：

{{% image_container width="350" %}}![ratings](attachments/native-styling-refguide/ratings.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <icon/><icon/><icon/><icon/><icon/>
</container>

<containerDisabled>
    <icon/><icon/><icon/><icon/><icon/>
</containerDisabled>
```

| 元素      | 样式属性         | 描述        |
| ------- | ------------ | --------- |
| `容器`    | 这包含所有视图样式属性。 |           |
| `容器已禁用` | 这包含所有视图样式属性。 |           |
| `图标`    | 这包含所有视图样式属性。 |           |
| `图标`    | `大小`         | 图标的大小。    |
| `图标`    | `颜色`         | 图标的颜色。    |
| `图标`    | `选中的颜色`      | 选择图标时的颜色。 |

样式所有评分输入的默认类命名为 `com_mendix_widget_native_rating_Rating`。

### 11.17 切换按钮

切换按钮小部件允许您设置枚举属性。 这是一个切换按钮小部件在应用程序中可以看到的方式：

{{% image_container width="350" %}}![toggle buttons](attachments/native-styling-refguide/toggle-buttons.png){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <button><text>Standard</text></button>
    <activeButton><activeButtonText>Sattelite</activeButtonText></activeButton>
    <button><text>Hybrid</text></button>
    <validationMessage/>
</container>

<containerDisabled>
    <button><text>Standard</text></button>
    <activeButton><activeButtonText>Sattelite</activeButtonText></activeButton>
    <button><text>Hybrid</text></button>
    <validationMessage/>
</containerDisabled>
```

| 元素       | 样式属性                 | 描述 |
| -------- | -------------------- | -- |
| `容器`     | 这包含所有视图样式属性。         |    |
| `容器已禁用`  | 这包含所有视图样式属性。         |    |
| `按钮`     | 这包含所有视图样式属性。         |    |
| `文本`     | 这包含所有的 TextStyle 属性。 |    |
| `活动按钮`   | 这包含所有视图样式属性。         |    |
| `活动按钮文本` | 这包含所有的 TextStyle 属性。 |    |
| `验证消息`   | 这包含所有的 TextStyle 属性。 |    |

所有切换按钮的默认类名称， `com_mendix_widget_native_togglebutons_ToggleButtons`。

### 11.18 视频播放器

视频播放器小部件允许您根据URL播放视频，仅限 MP4。 这是视频播放器小部件可以在应用程序中看到的方式：

{{% image_container width="300" %}}![video player](attachments/native-styling-refguide/video-player.png){{% /image_container %}}

小部件的样式属性如下：

| 元素     | 样式属性                 | 描述       |
| ------ | -------------------- | -------- |
| `容器`   | 这包含所有视图样式属性。         |          |
| `指标`   | `颜色`                 | 加载指示器颜色。 |
| `视频`   | 这包含所有视图样式属性。         |          |
| `错误消息` | 这包含所有的 TextStyle 属性。 |          |

所有视频播放器样式的默认类命名为 `com_mendix_widget_native_videoplayer_VideoPlayer`。

### 11.19 Web 视图

网页视图小部件允许您将静态或动态网站嵌入到您的应用中。 小部件的样式属性如下：

| 元素     | 样式属性                 | 描述 |
| ------ | -------------------- | -- |
| `容器`   | 这包含所有视图样式属性。         |    |
| `容器错误` | 这包含所有视图样式属性。         |    |
| `错误文本` | 这包含所有的 TextStyle 属性。 |    |

所有网页视图样式的默认类命名 `com_mendix_widget_native_webview_WebView`。

### 11.20 动画

动画小部件允许您动画容器。 您可以让内容变量、 移动、 更改大小等等。

小部件的样式属性如下：

```xml
<container>
    {content}
</container>
```

| 元素   | 样式属性         | 描述 |
| ---- | ------------ | -- |
| `容器` | 这包含所有视图样式属性。 |    |

默认类样式所有动画小部件名为 `com_mendix_widget_native_animation_动画`。

### 11.21 介绍屏幕

这个介绍屏幕小部件显示您可以滑动的分页内容，并在每个页面提供按钮继续或返回：

{{% image_container width="350" %}}![intro screen](attachments/native-styling-refguide/intro-screen.gif){{% /image_container %}}

小部件的样式属性如下：

```xml
<fullscreenContainer>
    content
    <paginationContainer>
        <dotStyle/><activeDotStyle/><dotStyle/>
    </paginationContainer>
    <paginationAbove.buttonsContainer>
        <buttonSkip.container>
            <icon/><caption>Skip</caption>
        </buttonSkip.container>
        <buttonPrevious.container>
            <icon/><caption>Back</caption>
        </buttonPrevious.container>
        <buttonNext.container>
            <icon/><caption>Next</caption>
        </buttonNext.container>
        <buttonDone.container>
            <icon/><caption>Done</caption>
        </buttonDone.container>
    </paginationAbove.buttonsContainer>
</fullscreenContainer>

<popupContainer>
    content
    <paginationBetween>
        <buttonSkip.container>
            <icon/><caption>Skip</caption>
        </buttonSkip.container>
        <buttonPrevious.container>
            <icon/><caption>Back</caption>
        </buttonPrevious.container>
        <paginationContainer>
            <paginationText>4 / 5</paginationText>
        </paginationContainer>
        <buttonNext.container>
            <icon/><caption>Next</caption>
        </buttonNext.container>
        <buttonDone.container>
            <icon/><caption>Done</caption>
        </buttonDone.container>
    </paginationBetween>
</popupContainer>
```

| 元素         | 样式属性                 | 描述               |
| ---------- | -------------------- | ---------------- |
| `全屏容器`     | 这包含所有视图样式属性。         |                  |
| `弹出容器`     | 这包含所有视图样式属性。         |                  |
| `分页容器`     | 这包含所有视图样式属性。         |                  |
| `分页文本`     | 这包含所有的 TextStyle 属性。 |                  |
| `dotStyle` | 这包含所有视图样式属性。         |                  |
| `活动Dot样式`  | 这包含所有视图样式属性。         |                  |
| `按钮容器`     | 这包含所有视图样式属性。         |                  |
| `容器`       | 这包含所有视图样式属性。         | 键盘、按钮完成、上次按钮和按钮。 |
| `标题`       | 这包含所有视图样式属性。         |                  |
| `图标`       | `大小`                 | 图标的大小。           |
| `图标`       | `颜色`                 | 图标的颜色。           |

默认类为屏幕小部件风格的名称为 `com_mendix_widget_native_animation_动画`。

### 11.22 滑动列表

列表视图的滑动小部件可以通过在列表项目的后台添加滑动手势和额外按钮使列表视图交互：

{{% image_container width="350" %}}![list view swipe](attachments/native-styling-refguide/list-view-swipe-buttons.gif){{% /image_container %}}

小部件的样式属性如下：

```xml
<container>
    <leftAction>
        {Left background}
    </leftAction>
    {Foreground}
    <rightAction>
        {Right background}
    </rightAction>
</container>
```

| 元素     | 样式属性         | 描述              |
| ------ | ------------ | --------------- |
| `容器`   | 这包含所有视图样式属性。 |                 |
| `左侧操作` | 这包含所有视图样式属性。 |                 |
| `左侧操作` | `panelSize`  | 背景按钮的像素数量和合并大小。 |
| `左侧操作` | `阈值`         | 接受滑动动动作的像素数量。   |
| `右侧操作` | 这包含所有视图样式属性。 |                 |
| `右侧操作` | `panelSize`  | 背景按钮的像素数量和合并大小。 |
| `右侧操作` | `阈值`         | 接受滑动动动作的像素数量。   |

默认类样式所有动画小部件名为 `com_mendix_widget_native_listviewswipe_ListViewSwipe`。

### 11.23 底板

底部板材小部件在阻止与屏幕其他部分的互动或固定在屏幕底部的可拖动的表面时创建了一组选项。 有两个可自定义的变量：

* 模式底板：

    {{% image_container width="350" %}}![modal bottom sheet](attachments/native-styling-refguide/modal-bottom-sheet.gif){{% /image_container %}}

* 正在展开底部工作表：

    {{% image_container width="350" %}}![expanding bottom sheet](attachments/native-styling-refguide/expanding-bottom-sheet.gif){{% /image_container %}}

小部件的样式属性如下：

```xml
<container />
<containerWhenExpandedFullscreen />
<modal />
<modalItems>
    <defaultStyle />
    <primaryStyle />
    <dangerStyle />
    <customStyle />
</modalItems>
```

| 元素             | 样式属性                 | 描述                         |
| -------------- | -------------------- | -------------------------- |
| `容器`           | 这包含所有视图样式属性。         |                            |
| `容器扩展全屏`       | 这包含所有视图样式属性。         | 只有在 `展开` and `启用全屏` 时才可用。  |
| `模式`           | 这包含所有视图样式属性。         |                            |
| `defaultStyle` | 这包含所有的 TextStyle 属性。 | 当 `默认` 被选为基本项目的样式时可用。      |
| `primaryStyle` | 这包含所有的 TextStyle 属性。 | 当 `主` 被选为基本项目的样式时可用。       |
| `危险样式`         | 这包含所有的 TextStyle 属性。 | 当 `危险` 被选为基本物品的样式时有效。      |
| `自定义样式`        | 这包含所有的 TextStyle 属性。 | 当 `被选择为基本项目的风格时，自定义` 是可用的。 |

所有底部板块样式的默认类命名 `com_mendix_widget_native_bottomSheet`。

### 11.24 Popup Menu

弹出菜单小部件允许您显示上下文菜单，正是在哪里点击。

小部件的样式属性如下：

```xml
<container/>
<buttonContainer/>
<custom>
    <containerStyle/>
    <itemStyle>
        </rippleColor>
    </itemStyle>
</custom>
<basic>
    <containerStyle/>
    <dividerColor/>
    <itemStyle>
        <ellipsizeMode/>
    </rippleColor>
        <defaultStyle/>
        <primaryStyle/>
        <dangerStyle/>
        <customStyle/>
    </itemStyle>
<basic/>
```

一个主对象有四个对象。

| 元素   | 样式属性           | 描述                               |
| ---- | -------------- | -------------------------------- |
| 基本的  | BasicItemStyle | 样式基本项。                           |
| 自定义  | 自定义项目样式        | 自定义条目样式。                         |
| 按钮容器 | 这包含所有视图样式属性。   | 触发器的包装视图样式，因为可能有多个元素，它必须用一个视图包裹。 |
| 容器   | 这包含所有视图样式属性。   | 在整个菜单周围设置包装器视图样式。                |

#### BasicItemStyle

| 元素   | 样式属性         | 描述                |
| ---- | ------------ | ----------------- |
| 容器样式 | 这包含所有视图样式属性。 | 围绕一个基本项目样式包装器的样式。 |
| 项目样式 | 项目样式         | 基本项目样式。           |
| 分红颜色 | `字符串`        | 样式分隔符颜色。          |

#### 项目样式

| 元素           | 样式属性                   | 描述                                                                   |
| ------------ | ---------------------- | -------------------------------------------------------------------- |
| 椭圆大小模式       | `头`, `中`, `尾部`, 或 `素材` | 如果文本过长, 将如何剪切。                                                       |
| rippleColor  | `字符串`                  | 点击项目时，触摸反馈的颜色样式。 适用于 iOS 和 Android 平台。                               |
| defaultStyle | 这包含所有的 TextStyle 属性。   | Styles all basic menu items which have the `default` style selected. |
| primaryStyle | 这包含所有的 TextStyle 属性。   | 所有基本菜单项都选择了 `主菜单样式` 样式。                                              |
| 危险样式         | 这包含所有的 TextStyle 属性。   | 选择了所有基本菜单项的样式 `危险` 风格。                                               |
| 自定义样式        | 这包含所有的 TextStyle 属性。   | 所有基本菜单项都选择了 `自定义` 风格。                                                |


#### 自定义项目样式

| 元素   | 样式属性              | 描述                                     |
| ---- | ----------------- | -------------------------------------- |
| 容器样式 | 这包含所有视图样式属性。      | 环绕一个自定义项目的包装器样式。                       |
| 项目样式 | `ripplColor: 字符串` | 点击项目时，触摸反馈的颜色样式。 适用于 iOS 和 Android 平台。 |
| 分红颜色 | `字符串`             | 样式分隔符颜色。                               |

样式所有弹出菜单的默认类命名 `com_mendix_widget_native_popupmenu_Popupmenu`。

### 11.25 Carousel

轮播小部件允许您在旋转时显示可滑动的项目。

小部件的样式属性如下：

```xml
</container>
<cardLayout>
    </slideItem>
    </inactiveSlideItem>
    </indicator>
    <pagination>
        </container>
        </dotStyle>
        </inactiveDotStyle>
        </dotContainerStyle>
        </text>
    </pagination>
</cardLayout>
<fullWidthLayout>
    </slideItem>
    </inactiveSlideItem>
    </indicator>
    <pagination>
        </container>
        </dotStyle>
        </inactiveDotStyle>
        </dotContainerStyle>
        </text>
    </pagination>
</fullWidthLayout>
```

主对象必须有三个对象，名为 `container`, `cardLayout`, 和 `完整宽度`。 `卡布局` and `全宽布局` 将根据小部件属性中选定的布局自动应用。

```
导出myCarouselStyle = 然后
    container: ViewStyle //
    cardLayout: ...LayoutStyle,
    全宽布局: ...LayoutStyle
}
```

| 元素   | 样式属性         | 描述                                       |
| ---- | ------------ | ---------------------------------------- |
| 容器   | 这包含所有视图样式属性。 | 旋转旋转小部件的视图样式。 为了获得最好的结果，请确保给定一个固定的 `高度`。 |
| 卡片布局 | 布局样式         | 布局设置为卡时的旋转样式                             |
| 全宽布局 | 布局样式         | 当布局设置为全宽时，旋转滚轮的样式。                       |

#### 布局样式

| 元素      | 样式属性            | 描述                                         |
| ------- | --------------- | ------------------------------------------ |
| 幻灯片项目   | 这包含所有视图样式属性。    | 每张幻灯片周围的视图样式，包括非活动幻灯片。                     |
| 禁用幻灯片项目 | `不透明度：数字，缩放：数字` | `非活动幻灯片不透明度` and `非活动幻灯片`, 将允许非活动幻灯片缩放和淡入。 |
| 指标      | `颜色：字符串`        | 旋转屏幕加载时显示的加载指示器。                           |
| 分页      | 分页              | 样式分页容器、点、活动点和文本。                           |

#### 分页

| 元素             | 样式属性                              | 描述                                                  |
| -------------- | --------------------------------- | --------------------------------------------------- |
| 容器             | 这包含所有视图样式属性。                      | 无论文字或点如何，分页周围的主视图样式。                                |
| dotStyle       | 所有视图样式属性 + `颜色：字符串`               | 样式所有分页点.                                            |
| 禁用DotStyle     | 所有视图样式属性 + `不透明度：数字；大小：数字；颜色：字符串` | 非活动点的额外样式。 将与 `点风格` 合并。                             |
| dotContainer样式 | 这包含所有视图样式属性。                      | 为单个分页点的视图风格。                                        |
| 文本             | 这包含所有的 TextStyle 属性。              | 当有超过五个元素的卡路塞尔时，将会应用。在这种情况下，分页按钮将会变成像 **1/5** 这样的文本。 |

样式所有弹出菜单的默认类命名 `com_mendix_widget_native_carousel_Carousel`。

### 11.26 直线图

[行图](https://github.com/mendix/widgets-resources/blob/master/packages/pluggableWidgets/line-chart-native) 小部件会根据静态和动态数据集呈现可缩放的行图。

小部件由下列元素组成：

```xml
<container/>
<errorMessage/>
<chart/>
<grid/>
<xAxis>
    <label/>
</xAxis>
<yAxis>
    <label/>
</yAxis>
<legend>
    <container/>
    <item/>
    <indicator/>
    <label/>
</legend>
<lines>
    <customLineStyles>
        <any_custom_line_style_name>
            <line/>
            <markers/>
        </any_custom_line_style_name>
    </customLineStyles>
</lines>
<lineColorPalette/>
```

| 元素                                                   | 样式属性                                                         | 描述                                                                                                          |
| ---------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| `容器`                                                 | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `错误消息`                                               | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `图表`                                                 | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `网格`                                                 | `背景颜色`                                                       | 将颜色应用于网格背景(字符串)。                                                                                            |
| `网格`                                                 | `仪表阵列`                                                       | 对网格线应用破折号和间隙图案 (包含 [破折模式](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) 的字符串)。         |
| `网格`                                                 | `线性颜色`                                                       | 将颜色应用于网格线(字符串)。                                                                                             |
| `网格`                                                 | `lineWidth`                                                  | 将宽度应用于网格线(数)。                                                                                               |
| `网格`                                                 | `padding`                                                    | 将填充应用于网格的所有边(数字)。 使用它来使坐标轴值标签可见。                                                                            |
| `网格`                                                 | `paddingBottom`                                              | 将填充应用于网格底部(数)。 使用它来使坐标轴值标签可见。                                                                               |
| `网格`                                                 | `垂直平移`                                                       | 将填充应用于网格的水平边(数)。 使用它来使坐标轴值标签可见。                                                                             |
| `网格`                                                 | `paddingLeft`                                                | 将填充应用于网格左侧(数)。 使用它来使坐标轴值标签可见。                                                                               |
| `网格`                                                 | `paddingRight`                                               | 将填充应用于网格右侧(数)。 使用它来使坐标轴值标签可见。                                                                               |
| `网格`                                                 | `paddingTop`                                                 | 将填充应用于网格的顶部(数字)。 使用它来使坐标轴值标签可见。                                                                             |
| `网格`                                                 | `垂直平移`                                                       | 将填充应用于网格的垂直边(数)。 使用它来使坐标轴值标签可见。                                                                             |
| `xAxis`                                              | `颜色`                                                         | 将颜色应用于坐标轴值标签(字符串)。                                                                                          |
| `xAxis`                                              | `仪表阵列`                                                       | 对轴线应用破折号和间隙模式(包含 [破折模式](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) 的字符串)。           |
| `xAxis`                                              | `字体类`                                                        | 将字体应用于轴值标签(字符串)。                                                                                            |
| `xAxis`                                              | `fontSize`                                                   | 将大小应用于轴值标签(数)。                                                                                              |
| `xAxis`                                              | `fontStyle`                                                  | 将字体样式应用于轴值标签("普通" 或 "斜体")。                                                                                  |
| `xAxis`                                              | `字体权重`                                                       | 将字体重应用于轴值标签(“普通”或“粗体”或“100”或“200”或“300”或“400”或“500”或“600”或“700”或“700”或“800”或“800”或“800”或“900”或“900”或“900”)。 |
| `xAxis`                                              | `线性颜色`                                                       | 将颜色应用于轴线(字符串)。                                                                                              |
| `xAxis`                                              | `lineWidth`                                                  | 将宽度应用于轴线(数值)。                                                                                               |
| `xAxis` > `标签`                                       | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `xAxis` > `标签`                                       | `相对位置网格`                                                     | 轴标签位于网格底部或右侧("底部"或"右")。                                                                                     |
| `yAxis`                                              | 所有 `xAxis` 元素样式。                                             |                                                                                                             |
| `yAxis` > `标签`                                       | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `yAxis` > `标签`                                       | `相对位置网格`                                                     | 坐标轴标签位于网格顶部或左侧("顶部"或"左")。                                                                                   |
| `图例` > `容器`                                          | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `传说` > `项目`                                          | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `传说` > `指示器`                                         | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `图例` > `标签`                                          | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `行`                                                  | `lineColorPalette`                                           | 向没有配置线条颜色的行提供颜色(用';'分隔的颜色列表的字符串)。                                                                           |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `行`  | `仪表阵列`                                                       | 将破折号和间隙应用于图行(包含 [破折模式](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) 的字符串)。            |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `行`  | `结束`                                                         | 将平坦或四舍五入的行末尾应用于图形行(“平整”或“圆形”)。                                                                              |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `行`  | `线性颜色`                                                       | 将颜色应用于图形行(字符串)。                                                                                             |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `行`  | `lineWidth`                                                  | 将宽度应用于图形行(数字)。                                                                                              |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `标记` | `背景颜色`                                                       | 将背景颜色应用于图形行的标记 (字符串)。                                                                                       |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `标记` | `边框颜色`                                                       | 将边框颜色应用于图形行的标记 (字符串)。                                                                                       |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `标记` | `borderWidth`                                                | 将边框宽度应用于图形线的标记(字符串)。                                                                                        |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `标记` | `显示`                                                         | 是否显示标记的影响。 当显示时，它会将图形行的标记放在顶部或下面("false"或者"底部"或者"onTop")。                                                   |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `标记` | `大小`                                                         | 将大小应用于图形行的标记(数字)。                                                                                           |
| `行` > `自定义行风格` > `any_custom_line_style_name` > `标记` | `符号`                                                         | 将符号应用于图形行的标记(“圆圈”或“钻石”或“附加”或“微小”或“正方形”或“星”或“三角下载”或“三角形”)。                                                   |

样式所有行图小部件的默认类命名 `com_mendix_widget_native_linechart_LineChart`。

### 11.27 条形图

[条图表](https://github.com/mendix/widgets-resources/blob/master/packages/pluggableWidgets/bar-chart-native) 小部件根据静态和动态数据集渲染水平条形图。

小部件由下列元素组成：

```xml
<container/>
<errorMessage/>
<chart/>
<grid/>
<xAxis>
    <label/>
</xAxis>
<yAxis>
    <label/>
</yAxis>
<legend>
    <container/>
    <item/>
    <indicator/>
    <label/>
</legend>
<domain>
    </padding>
</domain>
<bars>
    </barsOffset>
    </barColorPalette>
    <customBarStyles>
        <any_custom_bar_style_name>
            </bar>
            </label>
        </any_custom_bar_style_name>
    </customBarStyles>
</bars>
```

| 元素                                                                 | 样式属性                                                         | 描述                                                                                                          |
| ------------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| `容器`                                                               | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `错误消息`                                                             | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `图表`                                                               | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `网格`                                                               | `背景颜色`                                                       | 将颜色应用于网格背景(字符串)。                                                                                            |
| `网格`                                                               | `仪表阵列`                                                       | 对网格线应用破折号和间隙图案 (包含 [破折模式](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) 的字符串)。         |
| `网格`                                                               | `线性颜色`                                                       | 将颜色应用于网格线(字符串)。                                                                                             |
| `网格`                                                               | `width`                                                      | 将宽度应用于网格线(数)。                                                                                               |
| `网格`                                                               | `padding`                                                    | 将填充应用于网格的所有边(数字)。 这使得轴值标签可见。                                                                                |
| `网格`                                                               | `paddingBottom`                                              | 将填充应用于网格底部(数)。 这使得轴值标签可见。                                                                                   |
| `网格`                                                               | `垂直平移`                                                       | 将填充应用于网格的水平边(数)。 这使得轴值标签可见。                                                                                 |
| `网格`                                                               | `paddingLeft`                                                | 将填充应用于网格左侧(数)。 这使得轴值标签可见。                                                                                   |
| `网格`                                                               | `paddingRight`                                               | 将填充应用于网格右侧(数)。 这使得轴值标签可见。                                                                                   |
| `网格`                                                               | `paddingTop`                                                 | 将填充应用于网格的顶部(数字)。 这使得轴值标签可见。                                                                                 |
| `网格`                                                               | `垂直平移`                                                       | 将填充应用于网格的垂直边(数)。 这使得轴值标签可见。                                                                                 |
| `xAxis`                                                            | `颜色`                                                         | 将颜色应用于坐标轴值标签(字符串)。                                                                                          |
| `xAxis`                                                            | `仪表阵列`                                                       | 对轴线应用破折号和间隙模式(包含 [破折模式](https://www.w3.org/TR/SVG11/painting.html#StrokeDasharrayProperty) 的字符串)。           |
| `xAxis`                                                            | `字体类`                                                        | 将字体类型应用于轴值标签(字符串)。                                                                                          |
| `xAxis`                                                            | `fontSize`                                                   | 将大小应用于轴值标签(数)。                                                                                              |
| `xAxis`                                                            | `fontStyle`                                                  | 将字体样式应用于轴值标签("普通" 或 "斜体")。                                                                                  |
| `xAxis`                                                            | `字体权重`                                                       | 将字体重应用于轴值标签(“普通”或“粗体”或“100”或“200”或“300”或“400”或“500”或“600”或“700”或“700”或“800”或“800”或“800”或“900”或“900”或“900”)。 |
| `xAxis`                                                            | `线性颜色`                                                       | 将颜色应用于轴线(字符串)。                                                                                              |
| `xAxis`                                                            | `lineWidth`                                                  | 将宽度应用于轴线(数值)。                                                                                               |
| `xAxis` > `标签`                                                     | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `xAxis` > `标签`                                                     | `相对位置网格`                                                     | Positions the axis label at the **bottom** or **right** side of the grid.                                   |
| `yAxis`                                                            | 所有 `xAxis` 元素样式。                                             |                                                                                                             |
| `yAxis` > `标签`                                                     | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `yAxis` > `标签`                                                     | `相对位置网格`                                                     | Positions the axis label at the **top** or **left** side of the grid.                                       |
| `图例` > `容器`                                                        | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `传说` > `项目`                                                        | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `传说` > `指示器`                                                       | 所有 [视图风格](https://reactnative.dev/docs/view-style-props) 属性。 |                                                                                                             |
| `图例` > `标签`                                                        | 所有 [文本样式](https://reactnative.dev/docs/text-style-props) 属性。 |                                                                                                             |
| `domain` > `padding`                                               | `x`                                                          | 应用数个填充点的像素来添加X轴域的起始和终(数字)。                                                                                  |
| `domain` > `padding`                                               | `年`                                                          | 应用数个填充点的像素来添加Y轴域的起始和终(数字)。                                                                                  |
| `条`                                                                | `barColorPalette`                                            | 提供颜色给未配置条形状的条形状(以';'分隔的颜色列表的字符串)。                                                                           |
| `条`                                                                | `barsOffset`                                                 | 确定组中每个条形应从其在 Y 轴上的原始位置(数字)抵销的像素数量。 这仅适用于演示模式为 **分组** 的情况。                                                   |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `bar`   | `结束`                                                         | 指定一个半径来应用于每个条形。                                                                                             |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `bar`   | `颜色`                                                         | 将颜色应用于栏 (字符串)。 如果条形被配置为有标签，标签将与条形状相同。                                                                       |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `bar`   | `width`                                                      | 将宽度应用于栏 (数字)。                                                                                               |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `字体类`                                                        | 将字体类型应用于条形标签(字符串)。                                                                                          |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `fontSize`                                                   | 将大小应用于条形标签(数字)。                                                                                             |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `fontStyle`                                                  | 将字体样式应用于条形标签(**普通** 或 **斜体**)。                                                                              |
| `bars` > `customBarStyles` > `any_custom_bar_style_name` > `label` | `字体权重`                                                       | 将字体重应用于条形标签(“普通”或“粗体”或“100”或“200”或“300”或“400”或“500”或“600”或“700”或“700”或“800”或“800”或“900”或“900”)。             |

样式所有条形图部件的默认类命名 `com_mendix_widget_native_barchart_BarChart`。

## 12 阅读更多

* [如何样式您的 Mendix 本地移动应用程序](/howto8/mobile/how-to-use-native-styling)
* [如何实现本地移动样式](/howto8/mobile/native-styling)
* [设计属性文档](/apidocs-mxsdk/apidocs/design-properties)
