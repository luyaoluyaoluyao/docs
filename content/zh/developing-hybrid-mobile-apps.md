---
title: "开发混合移动应用"
parent: "混合移动设备"
tags:
  - "studio pro"
aliases:
  - /refguid8/Developing+Hybrid+Mobile+Apps.html
---

## 1 导言

Mendix 混合应用可以在移动网络浏览器中查看。 然而，移动设备功能无法通过 HTML 和 JavaScript 访问。 另外，如果您想要在 Apple App Store 上发布您的混合应用，Google Play 或 Microsoft Phone 商店，您必须将您的应用包装在本机外壳中。 我们使用 [本地版本](/howto8/mobile/build-hybrid-locally) 来实现这一点。

这些应用被称为“混合”应用，因为它们是网络和本机应用的混合物。 Mendix 以多种方式促进混合移动应用程序的创建。

## 2 Mendix 移动应用程序

开发混合移动应用程序时, 您可以通过使用 **在线查看混合电话应用程序** 或 **在线查看混合平板应用** 工具栏或通过 **运行** 菜单快速在浏览器中预览它。

然而，当您在您的混合页面上使用本机小部件时，其中一些小部件可能在浏览器中无法使用。 其中一些小部件在普通浏览器中运行时提供了替代实现；其他小部件根本无法运行。 要看看你的应用将看起来像在包装器内，你可以使用Mendix 移动应用程序。 工作室专业版， 您可以通过 **在工具栏中的 Mendix App** 查看混合移动应用对话框，或通过 **运行** 菜单。 它显示了一个可以通过该应用扫描的二维码。 这是将您的应用加载到兼容环境中的一种快速方式。

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

