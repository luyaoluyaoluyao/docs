---
title: "移动设备"
tags:
  - "studio pro"
---

## 1 导言

Mendix 允许您快速构建真实的 [本机移动应用程序](#nativemobile) 和 [混合应用](#hybridmobile)。 此文档提供了Mendix移动应用开发的概述。

通过Mendix，您可以创建不同的频道(例如响应、混合移动和本地电话)，使用导航配置文件。 这些移动配置文件可以单独添加和删除。 如果您添加了个人资料，您还必须提供一个主页。 欲了解更多导航信息，请参阅 [Navigation](navigation)。

## 2 个本地移动应用程序 {#nativemobile}

使用 Mendix 8 可以构建完全原生的移动应用程序。 本地移动应用程序不同于混合应用程序：它们不会在网络视图中渲染，而是使用本地UI元素。 这导致性能快速运行、动画平滑、自然互动模式(如滑动手势)，并改善所有本地设备能力的获取。  要使这种响应性的本地移动应用，Mendix 会利用通用的开源框架 [React Native](https://facebook.github.io/react-native/)。

你构建Mendix 本机移动应用的方式与构建网络或混合应用的方式相同。 您可以使用页面、小部件、纳夫洛、JavaScript行动、微流和许多其他熟悉的元素来构建您的应用程序。 关于如何构建本地移动应用的更多信息，请参阅 [使用本地移动应用启动](/howto8/mobile/getting-started-with-native-mobile)。

然而，在构建本地移动应用和构建混合应用之间存在着一些差异。 例如，小部件(及其可用属性)在优化本地移动应用时略有不同。 此外，本机移动应用的主题和样式是基于 JavaScript 而不是SASS/CSS。 关于样式的更多信息，请参阅 [本机样式](native-styling-refguide)。

## 3 混合移动应用程序 {#hybridmobile}

Mendix混合移动应用程序是通过移动网络浏览器查看的多功能应用。 然而，某些移动设备功能无法通过 HTML 和 JavaScript 访问这些应用程序的基础。

Mendix 使用 [Cordova](https://cordova.apache.org/) 和 [本地版本](/howto8/mobile/build-hybrid-locally) 来构建移动应用，这些应用可以让某些设备功能发挥杠杆作用，并发布到 Apple App Store 或 Google Play 商店。 Cordova 创建一个围绕网络应用程序的本地包装器，并通过 JavaScript API提供访问本地函数。 这些应用被称为“混合”，因为它们既是网络应用，也是本地应用的混合物。

为了让您的混合应用访问设备的原生功能，Mendix 在 [Mendix Marketplace](https://marketplace.mendix.com/) 中提供了几个小部件。 您也可以构建您自己的自定义小部件或 JavaScript 动作来影响本机功能。 关于构建自定义小部件或 JavaScript 动作的更多信息。 查看 [如何构建插件](/howto8/extensibility/pluggable-widgets) and [构建JavaScript 操作](/howto8/extensibility/build-javascript-actions)。

## 4 个离线第一个应用程序

通过Mendix，您可以构建能够正常工作的应用，而不论网络连接如何。 离线应用为最终用户提供了持续的经验，并使他们相信他们的数据在所有情况下都是安全的。 页面和逻辑与设备上的离线数据库交互，数据可能时与服务器同步。 这就使得用户界面更加简洁，更加可靠，设备电池寿命更长。 欲了解离线第一应用能力的更多信息，请参阅 [离线第一](offline-first)。

Mendix的原生移动应用程序总是用离线第一功能配置的。 在构建混合移动应用程序时，您可以选择构建一个可与服务器连接的在线应用程序。 或者一个即使没有互联网连接也能运行的离线第一个应用程序。 可以通过在 Mendix Studio Pro中选择相应的导航配置文件。 关于设置此配置文件的更多说明，请参阅 [Navigation](navigation)。

## 5 个此类别中的主要文档

* [本机移动](native-mobile) - 提供关于使用本机UI元素的 Mendix 平台构建完全本机移动应用的信息
* [混合移动](hybrid-mobile) - 描述如何准备、包和自定义Mendix 混合应用
* [离线第一个](offline-first) - 提供离线第一个应用程序在Mendix 中的建筑概念的详细信息
