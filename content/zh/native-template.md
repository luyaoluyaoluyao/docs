---
title: "本地模板"
parent: "本地移动版"
menu_order: 12
tags:
  - "移动网络"
  - "模版"
  - "原生的"
  - "iOS"
  - "Android"
  - "参考指南"
---

## 1 导言

构建Mendix 本地应用程序时需要模板。 简而言之，本机模板描述了您所需的本地依赖性。 并且它包括两个本地应用程序(一个用于iOS，一个用于Android)，可以独立构建来创建完成的应用程序。 本地模板与配置它的本地移动构建器一起工作。 欲了解更多关于本地移动生成器能力的信息，请参阅 [原生移动生成器版本号](/releasenotes/mobile/mendix-native-mobile-builder)。

该模板还包括配刀，帮助集合一切。 具体而言，本机模板使用React本地和 Mendix 自动链接功能，将本机依赖关系与平台特定应用连接， 并使用本机移动工具包，用版本号配置平台特定应用，应用名称，初始屏幕等等。

此外，本机模板帮助创建自定义开发者应用程序。 这些应用程序类似于“Make it Native app”，但是专门设计的应用程序的特定需要。 如果你想要构建一个使用自定义本地小部件等定制功能的应用程序，看到 [如何创建一个自定义开发者应用程序](/howto/mobile/how-to-devapps)。

## 2 个位置

本机模板托管在 [GitHub](https://github.com/mendix/native-template) 上，是公开的。

## 3 Versioning

请注意这个关于版本的关键信息：

* 本机模板使用 [语义版本](https://semver.org/)
* 本机模板版本与正在构建的应用程序的 Mendix Studio Pro 版本密切相关。
* 不使用匹配的版本将导致意外的行为

要确定您应该使用哪个版本的本地模板，请执行以下操作：

1. 注意您正在使用的Studio Pro 哪个版本，例如 *9.0.0*。
1. 导航到 [原生模板 mendix_version.json 文件](https://github.com/mendix/native-template/blob/master/mendix_version.json)。

密钥表示Mendix Studio Pro 版本。 `分钟` and `max` 值是支持的最小和最大原生模板版本：

{{% image_container width="200" %}}![Mendix Versions](attachments/native-template/mendix-version.png){{% /image_container %}}

与上面的例子一样，Mendix Studio Pro 8.9也是如此。 您可以选择 4.0.0 至最晚版本的本地模版版本。 理想的情况是，您应该选择最新支持的版本。

## 4 自动链接依赖关系

React 原生模块是 npm 包，包含依赖关系，这些依赖关系必须与您的平台特定应用链接，以便能够将React 原生模块与应用编译。

本机模板完全支持 [React Native的 CLI 自动链接能力](https://github.com/react-native-community/cli/blob/master/docs/autolinking)。 默认情况下自动链接的库将被正确链接到特定平台的应用程序。

对于不能完全自动连接的库 (通常是需要特殊初始化的库)，我们扩展了默认的自动连接功能。 这一进程仅限于已知的公开能力。 当API公开时，我们将扩展文档。

## 5 本机移动工具箱

本机移动工具包是一个Mendix开发的 npm 模块，用于便利特定平台应用的配置要求。 它可以让您定义应用功能，如版本、包 ID、初始屏幕以及更多的平台诊断方式。

配置已写入JSON。 配置文件是使用递增数版本化的。 当引入破解更改时，版本会递增。

本机移动工具包包含转换逻辑，允许从旧的配置版本转换为更新版本。 这种转换 发生在内存中，这样它不会与自定义实现相冲突。 转换后的配置将在终端的控制台 中输出以进行进一步调试.

### 5.1 移动工具包配置结构

指定应用的信息在顶级 **配置** 文件中定义。 获取可能的配置选项的最佳方式是首先使用 Mendix Native Mobile Builder 配置一个应用程序并注明配置密钥。

**<details><summary>要看到配置版本2所支持的属性，请单击此处。</summary>** 这些是配置版本 2 支持的属性

```
interface NativeTemplateConfig {
    configVersion: 2;
    appName: string;
    appIdentifier: string;
    appVersion: string;
    bundleName: BundleName;
    buildNumber: number;
    deviceTarget: DeviceTarget;
    capabilities: Capabilities;
    orientation: Orientation;
    permissions: Permission[];
    runtimeUrl: string;
}

interface Capabilities {
    appCenterOTA: Capability;
    crashlytics: Capability;
    deepLink: DeepLinkCapability;
    firebaseAndroid: Capability;
    firebaseIos: Capability;
    localNotifications: Capability;
    maps: MapsCapability;
    mapsIos: MapsIosCapability;
    pushNotifications: Capability;
}

interface Capability {
    enabled: boolean;
}

interface IOSPermission extends Permission {
    purpose: string;
}

interface Permission {
    name: string;
    title: string;
    platform: OS;
    required: boolean;
}

interface DeviceTarget {
    phone: boolean;
    tablet: boolean;
}

export interface Orientation {
    portrait: boolean;
    landscape: boolean;
}
```
</details>

**<details><summary>要看到一个已配置的应用的示例，请点击这里</summary>** 这是一个已配置应用的示例：

```
{
    "configVersion": 2,
    "appIdentifier": "com.mendix.mobile",
    "appName": "Mendix App",
    "appVersion": "1.0.0",
    "buildNumber": 1,
    "runtimeUrl": "http://localhost:8080"
    "bundleName": {
        "main": "MendixApp",
        "dev": "MendixAppDev"
    },
    "deviceTarget": {
        "phone": true,
        "tablet": false
    },
    "orientation": {
        "portrait": true,
        "landscape": true
    },
    "permissions": [
        {
            "title": "Internet",
            "name": "android.permission.INTERNET",
            "platform": "android",
            "required": true
        },
        {
            "title": "Location - Always Usage",
            "name": "NSLocationAlwaysUsageDescription",
            "purpose": "To use that feature, the app needs access to your location.",
            "platform": "ios",
            "required": true
        }
    ],
    "capabilities": {
        "deepLink": {
            "value": "",
            "enabled": false
        },
        "maps": {
            "value": "a12dkdadhqow12123123radqwe",
            "enabled": true
        },
        "mapsIos": {
            "enabled": false
        },
        "pushNotifications": {
            "enabled": false
        },
        "crashlytics": {
            "enabled": false
        },
        "firebaseAndroid": {
            "enabled": false
        },
        "firebaseIos": {
            "enabled": false
        },
        "localNotifications": {
            "enabled": false
        },
        "appCenterOTA": {
            "enabled": false
        }
    }
}

```
</details>


### 5.2 资产

移动工具包支持为您的应用配置初始屏幕和图标。 资源预计相对于命名为 **assets** 的文件夹中本地模板的根目录而被保存。

```
- 素材
    - 图标
    - splashScreen
```

#### 5.2.1 iOS 图标

图标的配置需要在一个版本的 *JSON* 格式的 **配置** 文件在 **assets/icons/ios.json** 下定义。

文件名下定义的实际资产文件预计在 **配置** 文件旁边可用。

版本是必需的，用于背向兼容目的。 下面看到配置使用 **版本 1**：

```
interface IOSIconsConfig {
    "images": Array<{
            "size": string",
            "idiom": "ipad" | "iphone" | "ios-marketing",
            "scale": "1x" | "2x"| "3x",
            "type": "icon",
            "filename": string
        }>,
    "version": 1
}
```

**<details><summary>要看到成功配置应用程序所需的所有密钥的示例，请点击这里</summary>**

这是成功配置应用程序所需的所有密钥的示例：

```
{
    "images": [
        {
            "size": "20x20",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "notification@1x.png"
        },
        {
            "size": "20x20",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "notification@2x.png"
        },
        {
            "size": "20x20",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "notification@2x.png"
        },
        {
            "size": "20x20",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "notification@3x.png"
        },
        {
            "size": "29x29",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "settings@1x.png"
        },
        {
            "size": "29x29",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "settings@2x.png"
        },
        {
            "size": "29x29",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "settings@2x.png"
        },
        {
            "size": "29x29",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "settings@3x.png"
        },
        {
            "size": "40x40",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "spotlight@1x.png"
        },
        {
            "size": "40x40",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "spotlight@2x.png"
        },
        {
            "size": "40x40",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "spotlight@2x.png"
        },
        {
            "size": "40x40",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "spotlight@3x.png"
        },
        {
            "size": "60x60",
            "idiom": "iphone",
            "scale": "2x",
            "type": "icon",
            "filename": "app@2x.png"
        },
        {
            "size": "60x60",
            "idiom": "iphone",
            "scale": "3x",
            "type": "icon",
            "filename": "app@3x.png"
        },
        {
            "size": "76x76",
            "idiom": "ipad",
            "scale": "1x",
            "type": "icon",
            "filename": "ipadapp@1x.png"
        },
        {
            "size": "76x76",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "ipadapp@2x.png"
        },
        {
            "size": "83.5x83.5",
            "idiom": "ipad",
            "scale": "2x",
            "type": "icon",
            "filename": "ipadproapp@2x.png"
        },
        {
            "size": "1024x1024",
            "idiom": "ios-marketing",
            "scale": "1x",
            "type": "icon",
            "filename": "appstore@1x.png"
        }
    ],
    "version": 1
}
```
</details>

#### 5.2.2 Android 图标

The icons' configuration needs to be defined in a versioned JSON-formatted **config** file under *assets/icons/android.json*.

文件名下定义的实际资产文件预计在 **配置** 文件旁边可用。

版本是必需的，用于背向兼容目的。 现在，配置处于版本 1：

```
接口AndroidIconsconfig 然后
    "images": Array<}
            "directory": "mipmap-mdpi" | "mipmap-hdpi" | "mipmap-xhdpi" | "mipmap-xxhdpi"
            "filename": "ic_launcher. ng" | "ic_launcher_round. ng"
            "title": string
        }>,
    "version": 1
}
```

**<details><summary>要看到成功配置应用程序所需的所有密钥的示例，请点击这里</summary>**

这是成功配置应用程序所需的所有密钥的示例：

```
{
    "images": [
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-mdpi",
            "title": "mipmap-mdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-hdpi",
            "title": "mipmap-hdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-xhdpi",
            "title": "mipmap-xhdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-xxhdpi",
            "title": "mipmap-xxhdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher.png",
            "directory": "mipmap-xxxhdpi",
            "title": "mipmap-xxxhdpi-ic_launcher.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-mdpi",
            "title": "mipmap-mdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-hdpi",
            "title": "mipmap-hdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-xhdpi",
            "title": "mipmap-xhdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-xxhdpi",
            "title": "mipmap-xxhdpi-ic_launcher_round.png"
        },
        {
            "filename": "ic_launcher_round.png",
            "directory": "mipmap-xxxhdpi",
            "title": "mipmap-xxxhdpi-ic_launcher_round.png"
        }
    ],
    "version": 1
}
```
</details>

#### 5.2.3 iOS 喷溅屏幕

The splash screen configuration needs to be defined in a versioned JSON-formatted **config** file under *assets/splashScreens/ios.json*.

文件名下定义的实际资产文件预计在 **配置** 文件旁边可用。

版本是必需的，用于背向兼容目的。 现在，配置处于版本 1：

```
接口AndroidSplashScreensConfig 然后
      "images": Array<}
              "size": "640x960" | "375x667" | "414x736",
              “idiom”：“普遍”，
              "scale": "1x" | "2x" | "3x",
              "类型": "splashScreen",
              "filename": 字符串
          }>, ,
      "version": 1
}
```

下面是定义所有必需的初始屏幕的文件示例：

```
{
    "images": [
        {
            "size": "640x960",
            "idiom": "universal",
            "scale": "1x",
            "type": "splashScreen",
            "filename": "splash@1x.png"
        },
        {
            "size": "375x667",
            "idiom": "universal",
            "scale": "2x",
            "type": "splashScreen",
            "filename": "splash@2x.png"
        },
        {
            "size": "414x736",
            "idiom": "universal",
            "scale": "3x",
            "type": "splashScreen",
            "filename": "splash@3x.png"
        }
    ],
    "version": 1
}
```

#### 5.2.4 安卓喷溅屏幕

The splash screen configuration needs to be defined in a versioned JSON-formatted **config** file *assets/splashScreens/android.json*.

文件名下定义的实际资产文件预计在 **配置** 文件旁边可用。

版本是必需的，用于背向兼容目的。 现在，配置处于版本 1：

```
接口AndroidSplashScreensConfig@un.org
  "images": Array<}
          "filename": "splash. ng";
          "directory": "draable-hdpi" | "draable-xhdpi" | "draable-xxhdpi",
          "title": 字符串;
      }>,
  "version": 1
}
```

下面是定义所有必需的初始屏幕的文件示例：

```
{
    "images": [
        {
            "filename": "splash.png",
            "directory": "drawable-hdpi",
            "title": "drawable-hdpi-splash.png"
        },
        {
            "filename": "splash.png",
            "directory": "drawable-xhdpi",
            "title": "drawable-xhdpi-splash.png"
        },
        {
            "filename": "splash.png",
            "directory": "drawable-xxhdpi",
            "title": "drawable-xxhdpi-splash.png"
        }
    ],
    "version": 1
}
```

### 5.3 配置 Firebase

使用防火墙需要特别的考虑。 当通过 Native Mobile Toolkit **配置** 文件启用 Firebase功能时， 工具包将在 **assets/firebase** 文件夹中查看适当的配置文件。

文件用名称查找。 每个平台的预期名称如下：

| 平台      | 预期名称                     |
| ------- | ------------------------ |
| Android | Google services.json     |
| iOS     | GoogleService-Info.plist |

本地移动工具包无法验证所提供的配置文件的有效性。 它只能在配置应用程序时将它们移动到正确的 位置。

### 5.4 运行原生移动工具箱

本机移动工具包是一个包含本机模版的节点模块。 因此，它必须先在本地模板根目录中运行 `安装`。 当构建本地时， 当发布新版本的本地移动工具包时，您必须运行 `npm 安装` ，以确保您始终在最新版本上运行。

{{% alert type="info" %}}
npm 脚本预计本机移动工具包配置文件是应用程序的根目录，并名为 **config.json**。 当使用 Mendix Native Mobile Builder 配置本地或远程应用程序时，情况总是如此。
{{% /报警 %}}

要使用 **package.json**定义的运行脚本运行工具包，运行 `npm 运行配置`。

#### 5.4.1 指定自定义配置路径

工具包不需要拥有相对于根目录的配置文件，而是为了方便。 要指定不同的配置文件路径，可以使用以下命令执行工具包：

```
本地移动工具包配置 --config-path='./<name of the configuration>.json'
```

## 6 套装信息

Mendix 原生应用程序基于React Native。 当使用 Mendix Native Mobile Builder 构建您的 Mendix 应用程序时，您的应用程序首先被编译为 Javascript 代码和静态资产。 使用React Native的大都库，客户端代码和资产随后被编译成特定的React本地Bundles平台。 在编译最终应用之前，这些应用最终会被移至本地模板中的正确位置。

这个整个过程是用一个叫做MXBuild的工具进行统一的，这个工具包含在每次安装Mendix Studio Pro的过程中。 欲了解更多信息，请参阅 [MxBuilding 参考指南](mxbuild)。

### 6.1 使用 MxBuild来构建您的原生应用

如果出于某些原因，您不能使用Mendix Native Mobile Builder 来配置和构建您的应用， 例如，在没有显示的 CI环境中运作时， 您必须为您正在构建的应用程序设置正确的 Mendix Studio Pro 版本，然后手动运行 MXBuild。

要这样做：

1. 定位所需的 Studio Pro 安装。
1. 找到可执行文件 **mxbuild.exe** 的路径并注明它。
1.  打开命令行并运行此命令：

    ```
    <path-to-mxbuild.exe> --java-home=DIRECTORY -java-exe-path=FILENAME --target=部署 --native-packer <path-to-the-app-mpr>
    ```

此命令执行以下操作：

* 像往常一样导出网络和本地应用到部署文件夹。
* 运行 React Native metro bundler (note 标志 `--native-packer`) 来创建每个平台的 RN bundles and assets in `/deplement/native/Bundle`.

捆包文件夹结构将看起来像这样：

```
- android
    - ress
        - draable-mdpi
        - draable-hdpi
        - draable-xhdpi
        - draable-xxhdpi
        - draable-xxxhdpi
        - raw
    - assets
        - index. ndroid。 撤消
- iOS 
    - assets
        - 列出所有图像命名空间
        - 索引。 bundle
```

### 6.2 将捆绑包复制到右侧位置

创建的捆绑包需要复制到本地模板中的正确位置才能构建：

* 对于Android， `bundle/android` 的内容反映了资产和bundles 需要复制的确切文件夹到
* For iOS, the content of the `bundle/iOS` folder needs to be simply copied to the `<native-template>/ios/Bundle` directory

## 7 派生应用程序的本地依赖关系

Mendix Studio Pro 9引入了本地依赖解决方案，用于插件和Javascript操作。 欲了解更多信息，请参阅 [声明原生依赖 ](/apidocs-mxsdk/apidocs/pluggable-widgets-native-dependencies)。 Studio Pro 9 Mendix Studio Pro 之前正在配送一组核心依赖关系，这些关系已被移除。

在开发过程中，您可以添加更多的 Mendix Studio Pro 9兼容模块、小部件和操作到您的应用中。 This means and more dependencies will be added that will also need be declared in your app's Native Template prior to building the native apps.

由于您的应用初始设置需要此依赖管理，我们建议您使用Mendix Native Mobile Builder来配置您的应用。 Mendix Native Mobile 生成器能够生成所需的依赖关系，并将它们与您的应用的本地模板连接。

## 8 持续整合测试准则

在一些高级情况下，您可能会考虑设置连续集成(CI)测试。 如果您有多个环境，并且希望在推送到生产前测试 任何夜间的验收变化，这可能是有用的。

我们建议您首先使用Mendix 本地移动构建器开发您的应用，直到本地依赖关系稳定。 在早期阶段就拥有一股公司将导致挫折感，流动依赖将导致意外崩溃。

CI 环境需要能够做以下操作才能成功配置构建的本地模板：

* 从 SVN 查看最新的 Mendix 应用程序
* 查看您的应用本地模板 (配置应用时使用的模板)
* 运行 `mxbuild`
* 设置配置并根据需要移动素材(可以通过简单的 shell 脚本或任何其他解决方案完成) 并且是实施者的选择)
* 运行 `npm i` and `npm 运行配置` 以在构建前使用 Mendix Mobile Toolkit 配置应用程序。

如何构建应用是实现者的一个选择。 Mendix Native App Builder 使用应用中心方便。 还有多个其他的 解决方案可以用于此目的。 我们不赞同其中的任何一个。

## 9 阅读更多

* [离线第一参考指南](离线前)