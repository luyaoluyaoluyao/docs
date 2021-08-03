---
title: "MxBuilding"
category: "常规信息"
menu_order: 50
description: "描述一个 MxBuilding 是构建和部署Mendix 应用程序的命令行工具"
tags:
  - "构建中"
  - "部署"
  - "部署包"
  - "命令行"
  - "studio pro"
---

## 1 导言

MxBuild是一个 Windows 和 Linux 命令行工具，可用来从 Mendix 应用程序构建Mendix 部署包。

您需要的MxBuild的版本取决于您想要构建的 Mendix 模型的版本。 您可以通过将此 URL 输入浏览器并用您自己替换 `mxversion` 来找到正确的 MxBuild。 完整的 Mendix 版本号: `https://cdn。 endix.com/runtime/mxbuild-{mxversion}.tar.gz`

{{% alert type="info" %}}

版本中包含一个构建号码，必须将其包含在上述链接路径中 - 例如`8。 2.1.3458` 是 8.12.1 Studio Pro 版本的3458座构建。

您可以在Mendix 安装的路径中找到构建号码(例如，如果您的安装看起来像是 `C:\Program Files\Mendix\8 2.1.3458`, 使用此 URL 获取您的文件：https://cdn.mendix.com/runtime/mxbuild-8.12.1.3458.tar.gz)。

此  [Studio Pro 发布列表](https://marketplace.mendix.com/link/studiopro/) 中任何公开版本的Studio Pro 将允许您下载 MxBuilding 文件。 如果你在下载文件时遇到问题，请确保你的构建列在那里。

{{% /报警 %}}

您可以使用您最喜欢的归档工具，例如 [7-Zip](https://www.7-zip.org/) 提取文件。

关于MxBuild系统要求的详细信息，请参阅 [System Requirements](system-requirements#mxbuild)。

{{% alert type="info" %}}
除特别提到的情况外，本文件中使用的示例是Windows的。
{{% /报警 %}}

## 2 个命令行

要构建您的软件包，您需要指定 Mendix 应用程序文件(.mpr)，用于在命令行上构建部署包 (.mda)。 文件名之前可以有一个相对路径或绝对路径。 应用程序文件应该位于Mendix 应用程序目录内。

MxBuild需要一些命令行选项来控制Mendix 应用程序的处理方式。 这些选项在应用文件名称之前。

在Windows中，命令行使用以下格式：

`MxBuilding --java-home="JDKDirectory" --java-exe-path="javaExecutable" [options] projectFile`

您也可以使用以下命令行格式在 Linux 下运行 MxBuilding：

`mono mxbuild.exe --java-home="JDKDirectory" --java-exe-path="javaExecutable" [options] projectFile`

创建部署包后，MxBuild进程退出。

### 2.1 一般指挥线选项

命令行选项见下表：

| 选项                         | 描述                                                                                                                                                                                                                                                                                           |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-h`, `--help`             | 打印MxBuilding的简短描述和所有可用选项的列表。                                                                                                                                                                                                                                                                 |
| `--java-home=DIRECTORY`    | (必填)。 安装 JDK 的目录。<br/>例如： `--java-home=/usr/lib/jvm/java-8-oracle`<br/>Windows *DIRECTORY* 应以双引号 `"`                                                                                                                                                                             |
| `--java-exe-path=FILENAME` | (必填)。 **完整路径** 到 Java 可执行文件。<br/>例如： `--java-exe-path=/usr/lib/jvm/java-8-oracle/bin/java`。<br/>Windows *DIRECTORY* 应以双引号 `"`, 并且必须包含完整的文件名 `.\java.exe`                                                                                                                        |
| <code>---target=[包&#124;部署]</code>  | `包`: 省略选项时默认。 创建一个部署包 (.mda 文件)<br/>`部署`: 部署应用而不生成部署包。                                                                                                                                                                                                                                 |
| `--loose-version-检查`       | Creates a deployment package from an app which was created with a lower Mendix version.<br/>The app will be upgraded to the MxBuild version before the deployment package is created.<br /> Any changes included as a result of this upgrade will **not** be stored in your app. |
| `--wring 错误=FILENAME`      | 以 JSON 格式写入应用部署到指定文件时遇到的所有错误、警告和废弃。<br />此文件仅在应用程序包含错误时写入。<br />如果文件已经存在，它将在没有警告的情况下覆盖。<br />关于此文件格式的描述，请参阅下面的 [应用错误](#project-errors) 部分。                                                                                                                                 |

### 2.2 创建包时的选项

{{% alert type="info" %}}
以下选项仅适用于 `--target=package` 选项：
{{% /报警 %}}

创建包时的选项在下面的表格中描述；

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 描述                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------- |
| `-o FILENAME` or<br/>`--output=FILENAME`                                                                                       | 由 MxBuild创建的 .mda 文件的名称 (可选的相对路径或绝对路径)。<br />如果省略了此选项，文件将被保存在 *当前* 目录中，名为 `。 da`. |
| `--project-name=NAME`                                                                                                                | 将应用程序的名称更改为Mendix Runtime所使用的名称。<br />当未指定此选项时，应用的名称被使用。                          |
| `--model-version=VERSION`                                                                                                            | 应用特定版本号到软件包中的模型。                                                                        |
| `--model-description=DESCRIPTI`                                                                                                      | 在包中嵌入模型的描述。                                                                             |

例如，创建一个部署包 `out。 da` 在当前目录中，使用 `MyApp` 使用 *Windows* 版本的 MxBuild, 您可以使用以下命令：

```bat
mxbuild--target=package --java-home="C:\Program Files\JavaScript1.8.0_144"--java-exe-path="C:\Program Files\Java\jdk1.8.0_144\bin\java.exe" "C:\Uers\users\Documents\Mendix\MyApp\MyApp.mpr"
```

## 3 退货代码

当MxBuild退出时，将返回以下代码之一：

| 退出代码 | 描述                |
| ---- | ----------------- |
| 0    | MxBuild成功完成。      |
| 1    | 发生内部错误。           |
| 2    | 命令行选项有问题。         |
| 3    | Mendix 应用程序的部署失败。 |


如果退出代码大于 0，MxBuild将向您显示描述错误的消息。

## 4 个应用错误 {#project-errors}

当您的 Mendix 应用程序包含错误时，部署将失败，MxBuild将报告这些错误。 您可以使用 `--wrarderrors=FILENAME` 命令行选项来告诉MxBuilding 将错误写入文件。

错误是作为具有一个属性的 JSON 对象输出： `个问题`。 此属性的值是一个数组对象，每个对象在您的应用中描述了一个错误、警告或弃置的情况。 例如：

```json
主席:
  "problems": [
    }
      "name": null,
      "严重性": "错误",
      "消息": "开始活动不能是流程的最后对象。 ,
      "locations": [
        }
          "elementId": "252e1008-d795-4e49-b3e3-2ba38eb0a56d",
          "unitId": "1a8a3593-6f01-43a3-bc22-Bd22f9244983",
          "元素": "开始活动",
          "文档": "Microflow",
          "module": "MyModule"
        }
      ]
    }
  ]
}
```

下表描述了 *个问题* JSON 对象的各种属性：

| 财产     | 描述                                                       |
| ------ | -------------------------------------------------------- |
| `名称`   | 在Mendix Metamodel中尚未定义一致性检查时，问题的唯一标识符或 `null`            |
| `严重程度` | 描述问题类型： `警告`, `错误`, 或 `废弃`。                              |
| `留言`   | 对问题的描述。 这与Mendix Studio Pro的 [错误面板](errors-pane) 中的消息相同。 |
| `位置`   | 包含描述问题发生时Mendix 应用程序中位置的零或更多对象(见下表)。                     |

与问题相关的地点具有以下属性：

| 财产          | 描述              |
| ----------- | --------------- |
| `elementId` | 发生问题的模型元素的唯一ID。 |
| `单位ID`      | 发生问题的文件中的唯一标识。  |
| `元素`        | 对问题发生的模型元素的描述。  |
| `文档`        | 说明问题发生的文档。      |
| `模块`        | 问题发生的模块描述。      |
