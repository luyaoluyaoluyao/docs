---
title: "管理应用签名密钥"
category: "移动开发"
---

## 1 导言

若要创建移动应用，您需要特定平台的应用签名密钥。 移动应用程序在发布前由其开发者用数字签名。 这些签名被应用商店和设备用来验证应用是真实的。

根据您想要攻击的平台，您需要创建所需的签名密钥。 以下章节描述了(每个平台)如何创建这些密钥。

## 2 iOS{#ios}

不幸的是，iOS应用的部署总是需要签名密钥。 即使您只想在您的个人设备上测试应用，不想发布到 Apple App Store。 本节描述如何创建所需文件。

提供苹果马克是方便的，但这并不是一项要求。 您总是需要苹果开发者帐户。

### 2.1 在苹果Mac上

如果您有 Apple Mac 可用， 在 [证书管理](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) 上查看苹果开发者文档以了解如何获取 iOS 签名证书和发行版配置文件的信息。 接着，请参阅苹果文档在 [上如何创建所需的分布配置文件](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html)。 最后，请检查此部分的结尾，了解如何 [上传签名密钥文件到 Adobe PhoneGap 构建](managing-app-signing-keys)。

### 2.2 其他平台

如果您没有 Apple Mac 可用，您可以手动创建证书签名请求。 首先，使用 OpenSSL 实用程序创建私钥和证书签名请求。 以下步骤假定您有一个 Windows 机器，但它们同样适用于Linux 机器，后者通常已经预先安装了 OpenSSL 包。

要手动创建证书签名请求，请遵循以下步骤：

1.  下载 [Windows](https://www.openssl.org/community/binaries.html) OpenSSL 并安装它。 您只需要下载并安装 **Win32 OpenSSL Light** 软件包(获取列表顶部的最新版本)。
    *   如果安装过程抱怨缺失的 VC++ 可再分配的库包，取消安装， 并首先从相同的软件包列表中下载并安装 **Visual C++ 2008 Redistributable** (您将被重定向到微软下载页面)。 安装 OpenSSL 到例如 *C:\OpenSSL* (请注解此目录，因为你将需要步骤3)。
2.  打开命令提示符。 在大多数系统中，您需要以管理员身份执行此操作(右键单击Windows起始菜单链接，然后选择 **作为管理员**)。
3.  用您刚刚安装的 OpenSSL 程序生成私钥。 将 `C:\OpenSSL` 替换为步骤1 中安装 OpenSSL 的地方。 私钥文件存储在 `out` 参数之后指定的位置。 下面的示例将会将文件存储在您的C根目录中：驱动器 (您可以将其更改为任何您想要的文件, 只需选择一个方便的地点，并跟踪文件的存储地点： `"C:\OpenSSL\bin\openssl"。 xe” genrsa out "C:\private.key" 2048`。 命令将输出“生成 RSA 私钥，2048 位长调制”和大量点和加号信号。
4.  生成证书签名请求(CSR)。 文件再次存储在同一个文件夹中，但可以放置在任何地方。 确保指向之前步骤创建的私钥文件： `"C:\OpenSSL\bin\openssl"。 xe" req -new -key "C:\private.key" out "C:\ios.csr"`. 该命令将打印一些文本，然后询问您与您身份相关的几个信息。 只有 **通用名称** 是相关的。 填写您自己的名字，这样在上传给苹果开发者会员中心后，证书可以轻松地认证。

生成的 *ios.csr* 文件必须上传到苹果开发者成员中心才能生成签名证书。 采取这些步骤以便：

1.  打开 [苹果开发者成员中心](https://developer.apple.com/account/overview.action)。
2.  在 **iOS, tvOS, watchOS**, 点击 **证书, 所有**。
3.  在 **iOS 证书** 概述中，点击右上角的加号按钮。 这将在 **选择类型** 中打开 **添加 iOS 证书** 向导，标题为“您需要哪种类型的证书？”
    *   如果加号按钮被禁用 (灰色表示)，您没有足够的权限。 请公司帐户管理员给予您更多的权利。
4.  在 **开发**之下，选择 **iOS 开发证书**。
5.  点击 **继续**。 您现在正处于步骤 **即将创建证书签名请求(CSR)**。 此页面描述了如何在Mac上创建证书签名请求。 你可以忽略它。
6.  点击 **再次继续**。 您现在正处于步骤 **生成**, 标题 **生成您的证书**。
7.  在 **下上传 CSR 文件**，点击 **选择文件...**。
8.  选择您创建的 *ios.csr* 证书签名请求文件。
9.  点击 **继续**。 苹果将在你的CSR签名并提供已签名的证书供下载。
    *   如果您收到一封消息，说您的证书签名请求正在等待批准，您没有足够的权利。 请公司帐户管理员批准您的证书签名请求。
10.  点击 **下载** 并存储 *er* 文件放在您的磁盘上，在方便的地方(例如，密钥和CSR 文件旁边)。
11.  点击 **完成了**。 **iOS 证书** 概述页面再次可见。 您的新证书应该在列表中。 在这里，您可以重新下载它，或者您可以撤销它(如果您丢失了相应的私钥)。

### 2.3 创建所需的分布配置文件

一旦你拥有证书文件，你需要获得一个分发文件。 Apple Developer Member Center允许您定义应用标识符、测试设备，最后是发行版配置。 欲了解更多信息，请检查苹果文档如何 [维护标识符、设备和配置文件](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html)。

### 2.4 上传密钥到 Adobe PhoneGap 版本

一旦您下载了签名证书( *)。 er* 文件), 您需要将签名证书从 *.cer* 转换为 *.p12*. 使用 OpenSSL 执行以下步骤：

1. 从签名证书中创建 PEM 格式： `"C:\OpenSSL\bin\openssl.exe" x509 -in "C:\ios.cer" -infit DER out "C:\ios_pem.pem" -outform PEM`。
2. 从 PEM 证书创建一个密码保护。 此操作需要PEM证书，这是在步骤3中创建的私钥。 和创建 *ios时给出的密码。 sr*: `"C:\OpenSSL\bin\openssl.exe" pkcs12 -export out "C:\ios.p12" -inkey "C:\private.key" -in "C:\ios_pem.pem"`.
3. 您可以上传签名证书(现在是 `.p12` 文件)和分布配置文件( `)。 Adobe PhoneGap 在 <a href="https://build.phonegap.com/people/edit">帐户页面</a> 上构建了 obilepropose` 文件 转到 **签名密钥** 标签，然后点击 **在 **iOS** 下添加一个密钥**。 选择两个文件并给该密钥命名。 点击密钥右侧的黄色锁图标并填写证书密码来解锁密钥。 您的构建作业现在可以使用该密钥。

## 3 Android{#android}

Android 应用程序可以在没有签名的情况下开发并部署到 Android 设备。 然而，要发布到应用商店，需要签名的应用程序。 这需要您生成一个密钥存储，然后上传到Adobe PhoneGap Build。

### 3.1 生成一个密钥库

若要为 Android生成密钥存储，请按照以下步骤：

1. 安装 Java JDK for Mac 或 Windows。 记住您安装的 JDK, 因为JDK bin 文件夹稍后会被使用。
2. 打开您的 **命令提示** 并运行您新的 *keytool.exe* 位于您的 JDK 的bin 文件夹中。
3.  *keytool.exe* 程序可以在您的 Java 安装的 bin 目录中找到(例如: *C:\Program Files\JavaScript 文件\jre1.8.0_20\bin*)：

    ![关键工具位置](attachments/managing-app-signing-keys/cmdjdkexe.png)

4.  当仍指向 *keystore.exe* 时，键入以下命令行提示：

    ```
    {{keytool -genkey -v -keystore file.keystore -alias YOUR_ALIAS_NAME -storepass YOUR_ALIAS_PWD -keypass YOUR_ALIAS_PWD -keyalg RSA -validity 36500}}
    ```

    请务必用您的别名和密码替换 `YOUR_ALIAS_NAME` and `YOUR_ALIAS_PWD`

    ![姓名和密码](attachments/managing-app-signing-keys/ktoolsetup.png)

5.  回答随后的问题，点击 **在每个问题后输入** ，并在被要求确认您的信息时键入 **

    ![信息问题](attachments/managing-app-signing-keys/qanda.png)

6. 完成这些问题生成了一个密钥商店，这个密钥商店将被保存到您当前工作目录中的 *文件。密钥商店* 文件。

### 3.2 将您的密钥存储上传到 PhoneGap 版本

创建密钥存储文件后，将其上传到 Adobe PhoneGap 建立在您的 [账户页面](https://build.phonegap.com/) 上。 然后完成以下指令：

1. 转到 **签名密钥** 标签，然后点击 **在 **Android** 下添加一个密钥**
2. 选择密钥存储文件，填写密钥的标题，并填写你在前一步骤中注意到的别名。
3. 上传密钥存储文件后，解锁密钥。 点击按键右侧的黄色锁图标并填写密钥和密钥密码。 您的构建作业现在可以使用该密钥。
4. 在 [开发者门户](https://sprintr.home.mendix.com/index.html)中，导航到 **部署 > 移动应用程序**, 然后点击 **手机发布** 按钮。 然后点击 **开始PhoneGap 构建作业** 按钮。
5. 一旦应用程序首次构建完毕，请返回 [Adobe PhoneGap 构建](https://build.phonegap.com/)。 点击您的应用名称查看其构建详情。
6. 在 **构建** 标签下，在安卓构建下拉菜单中选择您的密钥。 这将使用密钥自动重建应用程序。 从现在起， [开发者门户](https://sprintr.home.mendix.com/index.html) 将自动使用此密钥来构建应用程序。
