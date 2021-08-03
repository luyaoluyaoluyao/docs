---
title: "使用矢量图形"
parent: "本地移动版"
menu_order: 80
description: "学习如何将 SVG 集成到您的本地移动应用中。"
tags:
  - "原生的"
  - "svg"
  - "图像"
  - "移动网络"
  - "向量"
  - "矢量图像"
---

## 1 导言

当构建本地移动应用程序时，您可能想要使用矢量图像作为图标或其他插图。 为此目的，您可以使用可缩放矢量图形(SVGs)。 本参考指南将为在本机移动应用中使用SVG提供指导。

## 2 优化SVGs {#optimizing}

当从编辑器导出SVG时，您将经常生成带有几个不必要元素的SVG。 这些元素会增加文件大小，降低性能，并可能导致不需要的副作用。 因此，建议您通过SVG优化工具运行您的SVG。

优化您的 SVGs 您可以通过 [SVGOMG](https://jakearchibald.github.io/svgomg/) 等在线工具运行它们，也可以使用本地工具，例如 [SVGO](https://github.com/svg/svgo)。

## 3 不支持的元素

SVG可以包含几种元素。 然而，并不是所有这些都在本地移动应用中得到支持。 不支持的元素将不会产生任何效果，应该被删除。 下面的SVG 元素不支持本地移动应用程序的 **

* 复杂渐变
* 动画
* 视频
* JavaScript 代码
* CDATA 元素
* `<style />` 标签和 `样式` 属性 (请使用普通属性)

我们建议手动从您的SVG中删除这些元素，或者使用上面 [中提到的工具优化SVG](#optimizing) 以确保其兼容性。

## 4 Styling SVGs

您可能想要更改您的SVG中的某些颜色，例如添加图像时的颜色。 Mendix 允许您通过设置图像样式中的 `填充` 和 `勾画` 属性来做到这一点。 这些属性然后将应用于不具备这些属性的 *SVG 中所有的* 元素。

举出以下SVG作为示例：

```svg
<svg viewBox="0 0 100 100">
    <rect x="10" y="10" width="80" height="80" stroke="blue"/>
</svg>
```

设置此图像样式上的 `填充` 属性将会将矩形(`矩形` 元素)转换为提供的颜色。 设置 `笔划` 属性将不会导致更改，因为 `笔划` 已经设置。

这里是一个没有 `的 SVG 如何填充` 属性外观：

![前](attachments/native-svg/before.png)

这里是 `的 SVG 如何填充` 属性外观：

![之后](attachments/native-svg/after.png)

您可以在 [react-native-svg](https://github.com/react-native-community/react-native-svg#common-props) 仓库中检查允许的样式属性列表。

### 4.1 着色 SVG 图标

图标只能设置为按钮和底部条目。 当您将 SVG 图标集成到按钮或底部条目时，您必须自己设置 SVG 的颜色。 使用Atlas界面的应用程序时，默认情况下的颜色都是白色。 欲了解更多样式信息，请参阅 [原生移动式样式参考指南](/refguide8/native-styling-refguide)。

例如，下列代码：

```jsx
导出DemoButton = Pow.
    container: {
        backgroundColor: 'green'
    },
    标题: {
        color: 'orange'
    },
    icon: {
        color: 'blue'
    }
}
```

生成以下按钮和SVG：

![蓝色svg](attachments/native-svg/blue-svg.png)

## 5 在插件小部件中使用 SVGs

要在可插电的本地小部件的图像属性中使用SVG，我们建议使用提供的 `图像` 或 `图标` 组件。 这将允许任何支持格式的静态图像在您的插件中使用，包括SVG。

下面是一个使用 `图像` 组件的例子：

```jsx
从 "React"导入 { createElement } ；
从 "mendix/components/native/Image"导入 { Image } ；

导出const PluggableWidget = () => (
    <Image source="PUT_SOURCE_HERE" style={{ fill: 'blue' }} />
);
```

这是一个使用 `图标` 组件的示例：

```jsx
从 "React"导入 { createElement } ；
从 "mendix/components/native/Icon"导入 { Icon } ；

导出const PluggableWidget = () => (
    <Icon 
        icon={{
            type: "image",
            iconUrl: "PUT_SOURCE_HERE"
        }}
        size={20}
        color="blue"
    />
);
```

如果您想直接在您的插件中使用 SVG 元素，请查看 [react-native-svg](https://github.com/react-native-community/react-native-svg) 库。

## 5 阅读更多

* [构建插件小部件](/howto8/extensibility/build-native-widget)
* [Atlas界面](/howto8/front-end/atlas-ui)
* [插件部件 API](/apidocs-mxsdk/apidocs/pluggable-widgets)
