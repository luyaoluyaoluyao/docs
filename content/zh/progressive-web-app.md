---
title: "渐进网络应用程序"
category: "移动设备"
menu_order: 2
tags:
  - "移动网络"
  - "渐进的 web 应用程序"
  - "PWA"
  - "studio pro"
---

## 1 导言

渐进式网络应用程序(PWAS)是传统网络应用程序的演变。 总的来说，PWA的行为往往更像本机移动应用，其受欢迎性正在增加。 与混合应用和本地移动应用相比，PWA有一个不同和可能的优势，即PWA不需要通过应用商店分配，而是可以直接通过浏览器访问。

渐进式网络应用有三个主要特点：

* **可安装 —** PWAs 让您将您的应用程序添加到您的主屏幕并启动全屏应用。 这使得PWA感觉到能够更充分的本地应用。
* **可靠的 —** 使用服务工人，PWA可以脱机或部分脱机工作。 Mendix PWA可以部分离线工作 (资源如样式、页面和图像被缓存) 或完全离线(例如离线混合和本地移动应用程序)。
* **Capable —** PWA可以调用多个设备功能，如相机和位置，并且可以支持 web 推送通知。 请注意，功能的支持取决于使用哪个浏览器。

## 2 启用 PWA 功能

由于PWA基本上是具有额外功能的网络应用，Mendix 提供这些功能作为网页导航配置文件的一部分。 基于所需内容，您可以创建一个完全能够脱机的 PWA。 或者一个需要互联网连接但仍使用 PWA 功能的网络应用程序。

要创建一个完整的离线第一个PWA，请选择并添加以下配置文件 (取决于您需要哪个表单因子): 响应式网络离线。 手机离线或平板电脑离线。 欲了解离线第一应用的更多信息，请参阅 [离线第一参考指南](/refguide/offline-first)。

{{% alert type="info" %}}
离线第一个渐进式网络应用程序有一些限制，以确保它们能够完全脱机工作。 欲了解更多信息，请参阅 [确保您的应用处于离线第一 ](offline-first#limitations) 部分 *离线第一参考指南*。
{{% /报警 %}}

在导航图中，可以配置以下的 PWA 功能：

{{% image_container width="350" %}}![PWA settings](attachments/progressive-web-app/settings.png){{% /image_container %}}

为了能够全面测试PWA功能，应用需要部署到云端。 这是因为服务工人只能在云端通过 HTTPS 启用。

### 2.1 作为渐进网络应用程序发布

当选中并部署到云端时，应用注册了一个 [服务工作人员](https://developers.google.com/web/fundamentals/primers/service-workers) 作为PWA的基础。 在离线导航配置文件上，此选项始终启用。 在网上导航配置文件中，启用此选项也会在设备没有连接时给最终用户一个自定义页面。 如有需要，可以通过在主题文件夹中添加 *offline.html* 页面来定制此页面 (例如， *theme/offline.html*)。 请注意，此页面不应加载网络上的任何其他资源。

### 2.2 允许“添加到主屏幕”提示

当 **添加到主屏幕** 选项被选择时， 最终用户可能会被主动要求将应用添加到他们设备的主屏幕或桌面。 每个浏览器的行为可能因时间而异。 当未选中时，应用仍然可以被添加到主屏幕上，但用户不会被主动询问。

### 2.3 预加载静态资源

启用此选项将使应用程序在后台预加载静态资源，如页面、图像和小部件。 这可以有助于业绩。 此预加载发生在用户首次打开应用程序或模型改变时。 这使应用在导航到新页面时感觉更快。 然而，由于最初需要更多的带宽和设备储存，费用高昂。

在离线配置文件中，此功能将自动启用，允许应用程序完全离线。

请注意，导航配置文件中所有页面和图像都可以被浏览器加载。 从安全角度来看，这个配置可能是不可取的，取决于您的使用案例和要求。

## 3 预览或测试一个 PWA

PWA可以在您的机器或设备上的浏览器中直接查看和测试。 通过 **查看** 菜单，您可以在浏览器中直接打开 PWA 配置文件：

![查看菜单](attachments/progressive-web-app/view-menu.png)

您也可以通过您设备上的 **视图** 选项在您的设备上打开 PWA 配置文件：

{{% image_container width="350" %}}![View menu](attachments/progressive-web-app/view-dialog.png){{% /image_container %}}

请注意，如果您正在使用 Parallels 的 Mac 上运行 请确保转发端口 8080 (或您为您的应用配置的任何端口)，并确保您使用您的 Mac IP而不是虚拟机IP。 关于Mendix 和 Parallels的更多信息，请参阅 [如何配置Parallels](/howto/mobile/using-mendix-studio-pro-on-a-mac)。

{{% alert type="info" %}}
在本地预览或测试离线第一个PWA时，需要互联网连接才能加载应用程序。 初始加载后，应用将完全脱机进行操作，但如果没有连接，无法重新加载。 一旦应用被部署到云端，最终用户在第一次访问后总是可以在没有连接的情况下加载它。
{{% /报警 %}}

### 3.1 PWA 灯塔检查

要检查PWA的能力，您可以使用 [灯塔](https://developers.google.com/web/tools/lighthouse)。 灯光是一种开放源码自动化工具，用以提高网页质量。 它可以检查您的应用是否符合进步的网络应用要求，并可以为改进您的网络应用提供建议。

## 4 散布或分享PWA

因为PWA是网页应用，可以通过分享PWA的 URL轻松共享。

当在设备或浏览器上打开应用程序时，Mendix 会自动基于用户代理和浏览器功能决定导航配置文件。 如果浏览器不支持离线功能，将使用在线配置文件。

Google Chrome 和 Microsoft Edge (Chromium edition) 完全支持运行离线第一应用程序。

### 4.1 配置文件选择示例

例如，当配置了手机离线配置文件并且应用程序在浏览器中打开时，可以发生以下场景：

| 设备 & 浏览器             | 结果                                                      |
| -------------------- | ------------------------------------------------------- |
| 桌面浏览器                | 响应式网页配置文件已加载                                            |
| Android - Chrome 浏览器 | 手机网络离线配置文件已加载                                           |
| iOS - 任何浏览器          | 如果有手机网络配置文件，将会加载；否则将加载响应式网络配置文件。 这是因为离线PWA不支持 (尚未) iOS。 |

接下来， 它可以通过在URL中提供配置文件名作为查询参数来强制一个配置文件： `http://localhost:8080/? rofile=PhoneOffline` 可能的配置文件值如下：

| 配置文件名称   | URL中的值 |
| -------- | ------ |
| 响应式网络    | 响应性    |
| 响应式离线网络  | 离线责任   |
| 手机网络     | 电话     |
| 手机网络脱机   | 电话脱机   |
| 平板电脑网络   | 平板电脑   |
| 平板电脑离线模式 | 平板离线模式 |

当在云端部署中强制使用特定配置文件时，可能需要先清除浏览器缓存。

## 5 高级设置

关于高级设置的信息，请参阅下面的章节。

### 5.1 Web 应用程序清单

PWAs 使用 web 应用程序清单为浏览器提供有关应用程序的信息。 Mendix 基于模型自动生成一个。 它可以通过更改 `的最佳覆盖。webmanifest` *.json* 文件在 **主题** 文件夹中自定义来满足特定需要。 `背景颜色` 和 `主题颜色` 属性常常有助于自定义：

```json
{
    "background_color": "white",
    "theme_color": "#0CABF9"
}
```

更多关于网页应用清单中可用属性的信息 阅读 [简短介绍](https://web.dev/add-manifest/) 或查看 [MDN](https://developer.mozilla.org/en-US/docs/Web/Manifest) 的完整参考信息。

### 5.2 会议

离线第一个PWA使用寿命长的会话，即使在应用程序关闭后，用户仍然登录更长时间。 默认情况下，用户将在 7 天不活动后注销。 这可以使用 *LongLivedSession超时* 运行时间设置自定义的。

关于会话和如何定制超时的更多信息 在 Mendix Runtime 参考指南</em> 中查看 *Triky 自定义设置部分的 [会话持续时间](tricky-custom-runtime-settings#session-duration) 部分。</p>

## 6 访问设备功能

浏览器提供通过 API 访问设备功能的权限，这些功能可以在 PWAs 中杠杆。 这些设备功能可以被可用的小部件和nanoflow 操作所使用。 还可以通过使用 [JavaScript 动作](/refguide/javascript-actions) 或 [Pluggable 部件](/howto/extensibility/pluggable-widgets) 扩展平台来影响额外的设备功能。

此表列出了最常用的设备功能和 API，并且记录了它们与共同浏览器的兼容性：

| 功能                                                                                | Chrome/边缘                                                          | Firefox                                                            | Safari                                                             |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| [摄像头](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices)              | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) |
| [付款](https://developer.mozilla.org/en-US/docs/Web/API/Payment_Request_API)        | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) |
| [凭据（生物计）](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/credentials) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [推送通知](https://developer.mozilla.org/en-US/docs/Web/API/Push_API)                 | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [权限](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/permissions)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [前景检测](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      |
| [蓝牙](https://developer.mozilla.org/en-US/docs/Web/API/Bluetooth)                  | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [文件访问权限](https://developer.mozilla.org/en-US/docs/Web/API/File)                   | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      |
| [地理位置](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/geolocation)    | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) |
| [电量：](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getBattery)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [分享](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/share)            | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) | ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg) |
| [振动](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/vibrate)          | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [内存](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/deviceMemory)     | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |
| [连接](https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation)         | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)      | ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)       |

**图例** — 上面的符号对应于以下定义：

*  完全兼容：

    ![完全兼容](attachments/progressive-web-app/icons/check-mark.svg)

*  仅当使用 HTTPS 协议时兼容：

    ![使用 HTTPS 时兼容](attachments/progressive-web-app/icons/warning.svg)

*  不兼容：

    ![不兼容](attachments/progressive-web-app/icons/cross-mark.svg)

关于浏览器支持某些设备功能的更多信息，见第三方网站 [我可以使用](https://caniuse.com/)。

{{% alert type="info" %}}
要测试需要 HTTPS 协议的功能，请使用 [ngrok](https://ngrok.com/) 在您的本地主机中启用功能。
{{% /报警 %}}

## 7 决定 PWA 或 Native Mobile App

Mendix 提供了构建本地移动应用程序和 PWAs的选项。 根据您的应用的要求或约束，一个或另一个可能更合适。 还可以在一个应用中使用本机移动版和PWA图， 它们之间可以互相运行并大量重叠。

{{% alert type="info" %}}
重要限制：苹果不支持iOS上PWA推送通知。

目前，无法为iOS创建完全离线的第一个PWA——补充说，支持是我们2022年路线图的一部分。
{{% /报警 %}}

使用下面的图表来决定是构建一个 PWA，一个本地移动应用，还是两者兼而有：

{{% image_container width="350" %}}![Native app or PWA](attachments/progressive-web-app/native-or-pwa.png){{% /image_container %}}

## 8 阅读更多

* [本机移动参考指南](本地移动版)
* [离线第一参考指南](离线前)
* [导航参考指南](navigation)
