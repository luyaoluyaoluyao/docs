---
title: "本地生成器 (CLI)"
parent: "本地移动版"
menu_order: 70
tags:
  - "原生的"
  - "移动网络"
  - "部署"
  - "本地生成器"
  - "生成器"
  - "应用中心"
  - "已弃用"
---

{{% alert type="warning" %}}
Native Builder CLI 已被弃用而改用Mendix Native Mobile Builder ，这是一个整合Studio Pro的UI 工具。 阅读更多关于如何在这里部署您的应用 [](/howto/mobile/deploying-native-app) 的信息。
{{% /报警 %}}

{{% alert type="warning" %}}
请更新到 Native Builder v3.2.1 或更高版本。 本地生成器 v3.2. 包括解决GitHub 从使用 **master** 到使用 **main** 作为默认版本库分支名称所需的修复。
{{% /报警 %}}

## 1 导言

本机构建器拿走您的Mendix 项目，其中包含本地个人资料和软件包，用于iOS和Android本地移动应用。 要了解更多关于使用本地生成器的信息，请参阅 [如何部署您的第一个Mendix 本地移动应用程序](/howto8/mobile/deploying-native-app)。

本地建筑商使用 MxBuild、 GitHub 和 App 中心来构建您的应用程序。 该工具使这些进程的配置自动化，以简化您的应用程序构建体验。 本地生成器允许您在 GitHub 上创建尽可能多的应用。 只要他们使用 `--project-name` 参数给出独特的应用程序名称 (用于更多信息) 见下面 [命令](#commands) 部分。 Using the `prepare` and `build` command combination, the Native Builder packages your apps by doing the following:

1. 本地部署您的 Mendix 项目。
2. 使用适合Mendix 版本的 Mendix 原生模板仓库的最新版本创建一个新的仓库(使用项目名称参数提供)。
3. 在新的仓库中创建一个新分支，名为 **build/{build number provided to the tool}**
4. 将所需的文件和资源提交到新版本库中的构建分支。
5. 在应用中心配置您的应用。
6. 启动一个 iOS 和 Android 的构建。
7. 提供构建进度信息。
8. 如果构建成功，下载压缩后的应用，或者如果构建失败，下载构建日志文件。

## 2 个命令 {#commands}

命令行参数为本地生成器提供信息，例如您的 Mendix 项目所在位置。 命令使用以下参数进行配置。 其中一些参数是需要的或强烈建议的。 其余的是可选的，应在与您的应用相关时使用。 要创建一个包含参数的命令——执行后将启动你的本地生成器——请执行以下操作：

1. 以管理员身份打开您的命令行程序，右键点击它的图标或 *.exe* 文件，然后选择 **运行管理员**。
2.  输入 `cd "{your Native Builder .exe location}"` 然后按下 <kbd>输入</kbd>

    ![更改目录](attachments/native-builder/change-directory.png)

### 2.1 Prepare {#prepare}

`准备` 命令处理应用程序在 GitHub 和 App Center上的创建。 设置图标资源和初始化图像，然后验证Java、Mendix和项目路径。 一个配置文件是相对于用户文件夹生成的，以保留该信息供以后使用。 您可以通过使用 `准备` 命令并传递您想要更新的参数来更新此配置。

`准备` 命令的示例：

```bash
native-builder.exe prepare --github-access-token <token> --appcenter-api-token <token> --java-home <absolute-path> --mxbuild-path <absolute-path> --project-path <absolute-path-to-mpr-file> --projectname CoolApp --app-identifier "com.company.myapp" --app-name "My Cool App" --mendix-version 8.5.0
```

| 参数                               | 描述                                             | 示例                                                     |
| -------------------------------- | ---------------------------------------------- | ------------------------------------------------------ |
| `--github-access-token`          | GitHub access token.                           | `c0e1dasf1e102c55ded223dbdebdbe59asf95224`             |
| `--appcenter-api-token`          | App Center API 令牌。                             | `3e18asdfb43f4fe6c85afsd0bf60dde72f134`                |
| `--appcenter-organization`       | 应用中心组织名称。                                      | `我的公司`                                                 |
| `--project-名称`                   | 项目唯一名称。 **(必填)**                               | `冷却应用`                                                 |
| `--app-name`                     | 显示应用程序名称。                                      | `我的冷却应用`                                               |
| `--app-identifier`               | Unique app identifier.                         | `com.mendix.MyAwesomeApp`                              |
| `--app-icon-path`                | 应用图标的绝对路径。                                     | `C:\MyAppIcon.png`                                    |
| `--app-圆形图标路径`                   | 应用圆形图标的绝对路径，专门用于安卓。                            | `C:\MyAppRoundIcon.png`                               |
| `--app-splash-screen-path`       | 应用启动屏幕图像的绝对路径。                                 | `C:\MyAppSplash.png`                                  |
| `--java-home`                    | Java 可执行文件所在目录的绝对路径。                           | `C:\Program Files\JavaScrip\jdk-10.0.1`             |
| `--project-path`                 | Mendix 工程文件的绝对路径。                              | `C:\MyApp\MyApp.mpr`                                 |
| `--mxbuild-path`                 | MxBuilding 可执行文件的绝对路径。                         | `C:\Program Files\Mendix\8.0.0\model\mxbuild.exe` |
| `--runtimeurl`                   | Mendix 运行时间的 URL。                              | `https://myapp.mendixcloud.com`                        |
| `--mendix-版本`                    | Mendix Studio Pro 正在使用您的 Mendix 项目版本。 **(必填)** | `8.5.0`                                                |
| `--firebase-android-config-path` | *谷歌服务.json* 文件的绝对路径。                           | `C:\MyApp\google services.json`                      |
| `--firebase-ios-config-path`     | *GoogleService-Info.plist* 文件的绝对路径。            | `C:\MyApp\GoogleService-Info.plist`                  |


### 2.2 建筑 {#build}

#### 2.2.1 生成发行应用

`构建` 命令构建了 JavaScript 捆绑和资产，在GitHub 上创建一个构建，并启动了应用程序中心上的构建。

如果您已经运行了 `准备了`, 这是一个 `构建` 命令的示例：

```bash
native-builder.exe build--project-name "CoolApp" --app-version "1.0.0" --build-number 1
```

| 参数                         | 描述                                                   | 示例                                                     |
| -------------------------- | ---------------------------------------------------- | ------------------------------------------------------ |
| `--project-名称`             | `准备` 期间使用的工程的唯一名称。                                   | `冷却应用`                                                 |
| `--app-版本`                 | 应用程序版本，语义版本。  **(严格推荐)**                             | `1.2.3`                                                |
| `--build-number`           | 构建数字，一个任意的唯一整数。 **(必填)**                             | `1`                                                    |
| `--github-access-token`    | GitHub access token.                                 | `c0e1dasf1e102c55ded223dbdebdbe59asf95224`             |
| `--appcenter-api-token`    | App Center API 令牌。                                   | `3e18asdfb43f4fe6c85afsd0bf60dde72f134`                |
| `--appcenter-organization` | 应用中心组织名称。                                            | `我的公司`                                                 |
| `--app-name`               | 显示应用程序名称。                                            | `我的冷却应用`                                               |
| `--app-identifier`         | Unique app identifier.                               | `com.mendix.MyAwesomeApp`                              |
| `--app-icon-path`          | 应用图标的绝对路径。                                           | `C:\MyAppIcon.png`                                    |
| `--app-圆形图标路径`             | 应用圆形图标的绝对路径，专门用于安卓。                                  | `C:\MyAppRoundIcon.png`                               |
| `--app-splash-screen-path` | 应用启动屏幕图像的绝对路径。                                       | `C:\MyAppSplash.png`                                  |
| `--java-home`              | Java 可执行文件所在目录的绝对路径。                                 | `C:\Program Files\JavaScrip\jdk-10.0.1`             |
| `--project-path`           | Mendix 工程文件的绝对路径。                                    | `C:\MyApp\MyApp.mpr`                                 |
| `--mxbuild-path`           | MxBuilding 可执行文件的绝对路径。                               | `C:\Program Files\Mendix\8.0.0\model\mxbuild.exe` |
| `--runtimeurl`             | Mendix 运行时间的 URL。                                    | `https://myapp.mendixcloud.com`                        |
| `--output-path`            | 到工件应该去的位置的绝对路径。                                      | `C:\下载`                                               |
| `--platform`               | 要运行命令的平台。 默认 iOS 和 Android。                          | `ios` 或 `android`                                      |
| `--skip-mxbuild...`        | 如果捆绑JavaScript 捆绑和资产，请使用 JavaScript 捆绑。 默认为 `false`。 | `true` or `false`                                      |

#### 2.2.2 生成自定义开发者应用 {#generate}

当使用时， `build-app` 命令将创建一个像Make it Native app一样的预览应用程序。 然而，它所做的预览应用将是一个针对您的项目和Studio Pro 版本的自定义开发者应用程序。 此命令在 GitHub 上创建一个 **开发** 分支，并初始化应用程序中心上的构建。 它还期望您运行 `至少准备一次` 命令。

下面是一个命令的示例，其中有 `构建dev-app`:

```bash
native-builder.exe building dev-app --project-name "CoolApp" --output-path "C:\bundles\developer"
```

| 参数              | 描述                          | 示例                 |
| --------------- | --------------------------- | ------------------ |
| `--project-名称`  | `准备` 期间使用的工程的唯一名称。 **(必填)** | `冷却应用`             |
| `--output-path` | *ZIP* 档案的绝对输出路径。            | `C:\bundles\开发者` |
| `--platform`    | 要运行命令的平台。 默认 iOS 和 Android。 | `ios` 或 `android`  |

### 2.3 重新生成 {#regenerate}

`重新生成` 命令重新创建在 GitHub 上的项目，使用最新版本的 `原生模板`重命名前一个应用程序以保存更改(如果有的话)，然后更新应用中心应用程序的构建配置。 运行 `再生` 也期望 `准备` 至少运行过一次 `--project-name`。

{{% alert type="info" %}}
没有自动保存您对前一个模板所作的更改。 如果你有一些，你必须在新的 GitHub 仓库中手动应用它们。 此外，在更改您的应用程序的 Mendix 版本时，还请使用 `准备` 命令，更新 `mxbuild-path`
{{% /报警 %}}


| 参数             | 描述                                    | 示例              |
| -------------- | ------------------------------------- | --------------- |
| `--project-名称` | Java 可执行文件所在目录的绝对路径。                  | `我的冷却应用`        |
| `--mendix-版本`  | 该项目正在使用Mendix Studio Pro 版本。 **(必填)** | `8.5.0` 或 `8.5` |

`再生` 命令的示例：

```bash
native-builder.exe regenerate --project-name "CoolApp" --mendix-version 8.5.0
```

| 参数             | 描述                 | 示例     |
| -------------- | ------------------ | ------ |
| `--project-名称` | `准备` 期间使用的工程的唯一名称。 | `冷却应用` |

### 2.4 创建空中部署版本 {#ota}

`推送更新` 命令处理生成一个新的 JavaScript 包和资产，并在空中(OTA) 更新时进行部署。

下面是一个包含 `推送更新` 的命令示例：

```bash
native-builder.exe release pus-up-update --project-name "CoolApp" --target-version "1.0.0" --build-number 1 --rollout-百分比100
```

| 参数                     | 描述                                                   | 示例                                |
| ---------------------- | ---------------------------------------------------- | --------------------------------- |
| `--project-名称`         | `准备` 期间使用的工程的唯一名称。 **(必填)**                          | `冷却应用`                            |
| `--target-version`     | 此更新应影响到的已发布应用版本的版本或范围。 **(必填)**                      | 语义学版本见 [语义版](https://semver.org/) |
| `--rollout-percentage` | 应获取此更新的用户数量。 一旦设置，其后无法降低值。 **(必填)**                  | `1` 和 `100` 之间的数字。                |
| `--build-number`       | 应用中心构建数字，此更新应该针对。 **(必填)**                           | `构建期间定义的任何数字`                     |
| `--description`        | 用户在下载前会看到更多与此更新相关的信息。                                | 任何文字信息。                           |
| `--mandatory`          | 确定此更新是否被认为是重要的并强制使用者。 默认值为 true。                     | `true` or `false`                 |
| `--platform`           | 要运行命令的平台。 默认 iOS 和 Android。                          | `ios` 或 `android`                 |
| `--deployment-target`  | OTA目标组。 默认为 `生产`。                                    | `发布中`                             |
| `--skip-mxbuild...`    | 如果捆绑JavaScript 捆绑和资产，请使用 JavaScript 捆绑。 默认为 `false`。 | `true` or `false`                 |

### 2.5 更新OTA部署发布元数据 {#update-ota}

`补丁更新` 命令允许您更新发布的更新的元数据，但尚未推出给所有用户 (技术术语)。 更新没有 `展开百分比` 值 `100`

下面是一个包含 `补丁更新` 的命令示例：

```bash
native-builder.exe release patch-update --project-name "CoolApp" --label "v4" --target-version "1.0.1"
```

| 参数                     | 描述                             | 示例                                    |
| ---------------------- | ------------------------------ | ------------------------------------- |
| `--project-名称`         | `准备` 期间使用的工程的唯一名称。 **(必填)**    | `冷却应用`                                |
| `--label`              | 要补丁的唯一更新标签。 **(必填)**           | 可以通过使用 `版本列表` 命令来做到这一点。               |
| `--target-version`     | 更新应该影响的已经发布应用版本的版本或范围。         | 语义版本控制查看 [语义学版本](https://semver.org/) |
| `--rollout-percentage` | 应获取更新的用户数量。 一旦设置，其后无法降低值。      | `1` 和 `100` 之间的数字。                    |
| `--description`        | 用户下载前会看到更多与更新相关的信息。            | 任何文字信息。                               |
| `--mandatory`          | 确定更新是否是强制性的。                   | `true` or `false`                     |
| `--platform`           | 指定您的命令运行的平台。 默认 iOS 和 Android。 | `ios` 或 `android`                     |
| `--deployment-target`  | OTA目标组。 默认为 `生产`。              | `发布中`                                 |

### 2.6 回到先前的部署发布 {#rollback}

`回滚更新` 命令允许您使用相同的应用程序目标版本恢复到以前的部署版本。 此命令使用先前的部署版本创建了一个新的部署，它有 `--label` 参数。

下面是一个包含 `回滚更新` 的命令示例：

```bash
native-builder.exe release rollback-update --project-name "CoolApp" --label "v4"
```

了解以下情况：

* `--label` 参数只能指向先前的部署发布
* 如果你回退到一个损坏的版本，它将被部署到用户。 为了解决这种情况，您将需要重新发布或回滚到正常发布中。

| 参数                    | 描述                          | 示例                      |
| --------------------- | --------------------------- | ----------------------- |
| `--project-名称`        | `准备` 期间使用的工程的唯一名称。 **(必填)** | `冷却应用`                  |
| `--label`             | 要回滚的稳定版本的唯一标签。 **(必填)**     | 可以通过使用 `版本列表` 命令来做到这一点。 |
| `--platform`          | 要运行命令的平台。 默认 iOS 和 Android。 | `ios` 或 `android`       |
| `--deployment-target` | OTA目标组。 默认为 `生产`。           | `发布中`                   |

### 2.7 开列部署津贴

`邮件列表` 命令显示一个预印的所有部署版本列表。

下面是一个包含 `list` 的命令示例：

```bash
native-builder.exe release list --project-name "CoolApp"
```

| 参数                    | 描述                          | 示例                |
| --------------------- | --------------------------- | ----------------- |
| `--project-名称`        | `准备` 期间使用的工程的唯一名称。 **(必填)** | `冷却应用`            |
| `--platform`          | 要运行命令的平台。 默认 iOS 和 Android。 | `ios` 或 `android` |
| `--deployment-target` | OTA目标组。 默认为 `生产`。           | `发布中`             |

### 2.8 仅生成应用包

当使用时， `bundle` 命令 **将只运行MXBuilding 步骤** (跳过 GitHub 配置和应用中心构建步骤)。 此命令输出 *ZIP* 归档，包含相应的 JavaScript 包和每个平台的资源。

下面是一个具有 `捆绑` 功能的命令示例：

```bash
native-builder.exe bundle --project-name "CoolApp" --output-path "C:\bundles"
```

| 参数              | 描述                          | 示例                |
| --------------- | --------------------------- | ----------------- |
| `--project-名称`  | `准备` 期间使用的工程的唯一名称。 **(必填)** | `冷却应用`            |
| `--output-path` | *ZIP* 档案的绝对输出路径。 **(必填)**   | `C:\bundles`     |
| `--platform`    | 要运行命令的平台。 默认 iOS 和 Android。 | `ios` 或 `android` |

### 2.9 iOS特定配置

用于修改 iOS 配置的命令归类在 `配置ios` 命令下。

#### 2.9.1 增加和删除权利

若要添加或移除应享权利，请使用 `附加应享权利` 或 `移除应享权利` 命令：

```bash
native-builder.exe configios addities--project-name "CoolApp" --preferences notification nfc
```

| 参数             | 描述                                 | 示例       |
| -------------- | ---------------------------------- | -------- |
| `--project-名称` | `准备` 期间使用的工程的唯一名称。 **(必填)**        | `冷却应用`   |
| `应享权利`         | 要添加到您的项目的权限列表。 支持的选项是 `通知` 和 `nfc` | `通知 nfc` |

#### 2.9.2 添加和移除背景模式

若要添加或删除后台模式，请使用 `附加背景模式` 或 `移除背景模式` 命令：

```bash
native-builder.exe confios 附加背景模式--project-name "CoolApp" --modes 通知
```

| 参数             | 描述                          | 示例     |
| -------------- | --------------------------- | ------ |
| `--project-名称` | `准备` 期间使用的工程的唯一名称。 **(必填)** | `冷却应用` |
| `--modes`      | 要添加到您项目的背景模式列表。 支持 `通知` 选项。 | `通知`   |

## 3 扩展参数解释 {#parameters}

### 3.1 - 项目名称

此参数是您应用的唯一名称，可以包含任何字符。 此名称用于在您的机器上保持常见的参数配置，如 `--github-access-token`。 这提高了与其他需要的命令的可重复使用。 它也被用作GitHub 和 App Center的应用程序名称。

### 3.2 --runtimeurl

此参数应指向您想要运行应用程序的运行时间。 如果与本地部署的应用程序进行测试，请使用您的机器IP地址(例如， `http://192.168.1.12:8080`)。 如果对Mendix Cloud部署的应用程序进行测试，使用您的部署服务器的完全合格的运行时间URL(例如， `https://myapp.mendixcloud.com`)。 需要添加正确的协议，否则URL将默认使用 `http://` 前缀。

### 3.3 --appcenter-organization

在应用中心中，您可以成为一个或多个组织的成员。 如果应用程序需要作为机构的一部分构建， 然后使用 `--appcenter-organization` 将该组织的名称提供给土著建筑师。 如果您离开命令行参数，应用将成为您个人应用中心帐户的一部分。

### 3.4 --app-name

此参数是您应用的显示名称，可以包含您选择的任何字符。 当用户在设备上安装您的应用时，您可以看到这个名字。 对于iOS应用，这将使用 [CFBundleDisplayName](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html#//apple_ref/doc/uid/20001431-110725)。 对于安卓应用，这是 `应用程序` 标签在 *AndroidManifest.xml* 文件中的 `android:label` 属性。

### 3.5 --app-版本

此参数指定了您想要构建的应用程序版本。 查看 [语义版本](https://semver.org/) 了解如何选择适当版本号的更多信息。

### 3.6 --app-identifier

此参数是您应用的唯一标识符， 必须符合Android的 [应用程序 ID](https://developer.android.com/studio8/build/application-id) 要求以及苹果的 [CFBundleIdentifier](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html) 要求。 一旦您的应用上传到苹果应用商店或Play商店，就不能再修改应用程序的标识符。 如果您在应用程序发布后修改标识符，它将被两个商店视为不同的应用程序。 应用程序标识符被指定为反向DNS标记，例如 {com.mendix.MyAwesomeApp}。

### 3.7 --平台

此参数允许每个特定平台或两者进行选择性构建。 默认情况下，本地生成器试图为两个平台构建，但此参数可以将构建限制为 iOS 或 Android 。

### 3.8 --skip-mxbuild。

在极少数情况下，在捆绑过程完成后可能发生错误。 此参数将允许您在测试过程中跳过 MxBuild以节省时间。

### 3.9 --app-icon-path

此参数指定了一个应用图标文件。 图像必须是 *.png* 文件，并且分辨率为 1024x1024。 Mendix 将为您调整大小。 如果没有提供文件路径，默认的应用图标将由分支 **主** 提供。

### 3.10 --app-crowicon-path

此参数指定了一个专门适用于Android的应用圆形图标文件。 图像必须是 *.png* 文件，并且分辨率为 1024x1024。 Mendix 将为您调整大小。 如果没有提供文件路径，默认的应用图标将由分支 **主** 提供。

### 3.11 --app-splash-screen-path

此参数指定了一个应用splash文件。 图像必须是 *.png* 文件，并且分辨率为1440x2560。 Mendix 将为您调整大小。 如果未提供文件路径，默认的应用样式图像将由分支 **主** 提供。

### 3.12 --build-number

这个独特的配置代表了 Android 和 iOS 版本构建的版本构建号。 计划发布的每个构建都应该有一个独特的、递增的数字。 此号码将被用作应用中心和GitHub 上的分支名称。

对于空中更新，每个构建都与某个特定的发布组相关(`--deption-target`)，该组将获得更新。 默认情况下，这个值设置为 **生产** 并且通常应该保持这种方式。 如果更改，应注意新的值，因为只有在该环境中运行的设备才能获得更新。

安卓系统允许的最大整数为2,147,483,647。 考虑从1开始，每次发布一次递增。 或者，您也可以使用“YmmddHmm”格式的日期，如 {2007310950} 的版本，7月31日运行时间为9:50。

### 3.13 --mendix-version

此参数使得Native Builder 根据您的 Mendix project's Studio Pro 版本选择一个兼容的本地模板版本。 此参数需要是有效的Studio Pro语义版本，例如8.5.1。 所提供的版本需要尽可能具体。 因为即使是补丁版本也可能包含可能与所有可用的本地模板不兼容的修复。 要确定您正在使用哪个Mendix 版本，请检查 **关于** 页面或您的 Mendix 项目版本的 Studio Pro。

### 3.14 --verbose {#verbose}

当本地生成器发生错误时，此参数提供了额外的详细信息。 当 `--verbose` 被使用和本地生成器错误时，本地生成器将输出错误的完整堆栈跟踪。 这对于本土生成器失败但出现未知错误的情况是有用的。


## 4 高级使用 {#advanced-usage}

### 4.1 自定义本地代码

如果您有自定义本机依赖关系或代码， 您可以通过合并您对 GitHub 版本库的 **主** 分支的更改，将他们纳入您的应用中。 来自 **master** 的每个构建分支都将包含您的更改。 请记住同步您的资源库以获取Mendix 本机模板的最新更改。

欲了解更多关于同步您的仓库的信息，请参阅 [何时重新生成您的原生模板](#sync-your-repository)。

### 4.2 自定义应用中心配置

您可以在应用中心配置您的分支级构建。 如果分支 **master**没有可用的配置，本地生成器将创建一个默认配置。 如果配置已经存在，它将不会被工具修改。 当构建的分支初始化后， **master** 的配置将被复制。 连续构建不会改变此分支的配置。 这是为了避免覆盖您的自定义配置，除非使用 `再生` 命令。

### 4.3 自定义开发者应用

Mendix 应用程序到期， 您可能想要扩展它的功能(例如引入自定义小部件或逻辑，需要新的本地依赖)。 一个自定义的开发者应用程序充当了这个角色，替代了 Make it 本地应用， 当您有不被 Make It 本地应用程序支持的自定义部件和逻辑时，应该使用。 自定义开发者应用是您可以使用当前项目结构自行生成的应用。 您的自定义模块以及测试您进化应用的任何其他要求。 欲了解更多信息，请参阅 [如何创建一个自定义开发者应用](/howto8/mobile/how-to-devapps)

## 5 何时重新生成您的本地模板 {#sync-your-repository}

目前正在不断开发土著模板。 这意味着定期发布新版本，以适应Mendix 平台的新功能或修复问题。 当有新版本可用时，本地生成器会建议您运行 `重新生成` 来更新您的基础模板。

您应该在以下场景中更新您的项目模板：

* 您的应用意外崩溃，即使所有Studio Pro 模块和资源都使用Mendix Marketplace完全更新
* 您更新了您的Studio Pro 版本

本地模板与您正在运行的Studio Pro 版本紧密相连。 因此，每次更新您的项目时，考虑运行 `重新生成` 使用原生构建器更新您的模板。

## 6 正在解决错误

### 6.1 GitHub Errors

**无效的访问令牌** — — 您的访问令牌无效。 在 *中咨询 [GitHub Token](/howto8/mobile/deploying-native-app#github-token) 部分，如何部署您的第一个Mendix 本地移动应用程序* 并为本地生成器提供访问令牌。

**无法创建仓库：访问令牌需要访问 Repo Scope** — 您的访问令牌是有效的， 但本地生成器的权限太少而无法工作。 本机构建器克隆模板 GitHub 仓库，创建分支并提交文件。 在 *中咨询 [GitHub Token](/howto8/mobile/deploying-native-app#github-token) 部分，如何部署您的第一个Mendix 本地移动应用程序* 并向本地生成器提供新的访问令牌。

**无法删除分支建筑/{build number}** — — 与 GitHub 通信时出了错。 验证您的连接，请检查GitHub 是否可用，然后再次尝试运行本地生成器。

**无法创建分支建筑/{build number}** - 与 GitHub 通信时出了错。 验证您的连接，请检查GitHub 是否可用，然后再次尝试运行本地生成器。

**无法提交 {build number}** - 与 GitHub 通信时出了错。 验证您的连接，请检查GitHub 是否可用，然后再次尝试运行本地生成器。

### 6.2 应用中心错误

**无效的 API 令牌** — — 您的 API 令牌是无效的。 在 *中按照 [应用中心令牌](/howto8/mobile/deploying-native-app#appcenter-token) 部分来部署您的第一个Mendix 本地移动应用程序* 并向本地生成器提供 API 令牌。

**无法配置构建：{explanation}** — — 在与应用中心通信时出了错。 验证您的连接，检查应用中心是否可用，然后再次尝试运行本地生成器。

**Build {build number} for App {app number} Has Failed** — The native build on App Center has failed. 读取本地生成器下载的日志文件。 日志文件名为 *{AppName}-{BuildNumber}.log* 并且位于与您的本地建设器可执行文件相同的文件夹中。

**构建配置被默认值覆盖** - 虽然原生构建器正在检查以确定它正在构建的分支是否已经被手动配置， 它可能发现虚假阳性。 这可能导致您的自定义配置被覆盖。 如果发生这种情况，考虑直接使用应用中心运行构建，跳过使用本分支的本地构建器。

**未知错误** - 如果您不理解一个错误， 您可以登录到应用中心并删除 **master** 分支的构建配置。 然后再次运行本地生成器。 工具将为 **master** 和您的分支重新创建默认构建配置。

### 6.3 未知错误

如果本地生成器未能完成运行，且没有提供错误。 考虑使用 [--verbose](#verbose) 参数来获取错误的完整堆栈跟踪。 在通过支持沟通问题时，总是很方便地提供这些额外的日志以及构建日志，以便及时找到解决办法。

## 7 阅读更多

* [如何部署您的第一个Mendix 本地移动应用程序](/howto8/mobile/deploying-native-app)
* [如何开始使用本地移动设备](/howto8/mobile/getting-started-with-native-mobile)
* [如何样式您的 Mendix 本地移动应用程序](/howto8/mobile/how-to-use-native-styling)
