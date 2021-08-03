---
title: "开发混合移动应用"
category: "移动开发"
aliases:
  - /refguid7/Developing+Hybrid+Mobile+Apps.html
---

## 1 导言

Mendix 应用可以简单地在移动网络浏览器中查看。 然而，移动设备的某些功能无法通过 HTML 和 JavaScript 访问。 另外，如果您想要在 Apple App Store 上发布您的应用，Google Play 或 Microsoft Phone 商店，您必须将您的应用包装在本机外壳中。 我们使用 [PhoneGap](http://phonegap.com/) 来做这件事。 PhoneGap创建了一个围绕网页应用程序的本地包装器，并通过JavaScript API提供了对本地功能的访问权限。

这些应用也被称为“混合”应用，因为它们是网络和本地应用的混合物。 Mendix 以多种方式促进混合移动应用程序的创建。

## 2 Mendix 移动应用程序

开发混合移动应用程序时, 您可以通过使用 **在线查看混合电话应用程序** 或 **在线查看混合平板应用** 工具栏或通过 **运行** 菜单快速在浏览器中预览它。

然而，当您在您的混合页面上使用本机小部件时，其中一些小部件可能在浏览器中无法使用。 其中一些小部件在普通浏览器中运行时提供了替代实现；其他小部件根本无法运行。 要看看您的应用将在 PhoneGap 包装器中看起来是什么，您可以使用 Mendix 移动应用程序。 在桌面模式下， 您可以通过 **在工具栏中的 Mendix App** 查看混合移动应用对话框，或通过 **运行** 菜单。 它显示了一个可以通过该应用扫描的二维码。 这是一个将您的应用程序加载到 PhoneGap 兼容环境的快速方法。

![](attachments/Developing+Hybrid+Mobile+Apps/View_Hybrid_Mobile_App_Popup.png)

关于如何下载 Mendix 移动应用的更多信息，请参阅 [获取Mendix 移动应用](getting-the-mendix-app)。

{{% alert type="warning" %}}

您的移动设备必须与Mendix 移动应用的开发机器处于同一网络上。 如果情况如此，并且连接仍然失败，请确保在Wi-Fi接入点允许设备之间的通信。

{{% /报警 %}}

## 3 阅读更多

* [移动设备](移动网络)
* [获取Mendix 移动应用程序](getting-the-mendix-app)
* [自定义混合移动应用程序](customizing-hybrid-mobile-apps)
* [包装混合移动应用](packaging-hybrid-mobile-apps)

