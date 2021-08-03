---
title: "MxBuilding"
category: "A. 概况"
menu_order: 50
description: "描述一个 MxBuilding 是构建和部署Mendix 应用程序的命令行工具"
tags:
  - "构建..."
  - "部署"
  - "部署包"
  - "命令行"
---

## 1 导言

MxBuild是一个 Windows 和 Linux 命令行工具，可用来从 Mendix 项目构建Mendix 部署包。

您需要的MxBuild的版本取决于您想要构建的 Mendix 模型的版本。 您可以在格式 `https://cdn.mendix.com/runtime/mxbuild-{mxversion}.tar.gz` 的链接中找到正确的 MxBuilding 下载。

{{% alert type="info" %}}

Mendix 版本 7.18.1 及以上版本包含版本号，这必须包含在链接路径中。 例如：

* 7.17.2
* 7.18.1.40272

您可以在Mendix 安装路径中找到构建编号(例如 `C:\Program Files\Mendix\7.18.1.40272`)。

{{% /报警 %}}

所以，Mendix 版本 7.18.1 的 MxBuilding 可在 [https://cdn.mendix.com/runtime/mxbuild-7.18.1.40272.tar.gz](https://cdn.mendix.com/runtime/mxbuild-7.18.1.40272.tar.gz) 上找到。

您可以使用您最喜欢的归档工具，例如 [7-Zip](https://www.7-zip.org/) 提取文件。

MxBuild的系统要求在这里被记录： [系统要求](system-requirements#mxbuild)。

{{% alert type="info" %}}
除特别提到的情况外，本文件中使用的示例是Windows的。
{{% /报警 %}}

## 2 个命令行

要构建你的软件包，你需要指定Mendix Project 文件(.mpr)，你想要在命令行上构建部署包 (.mda)。 文件名之前可以有一个相对路径或绝对路径。 项目文件应该位于Mendix 项目目录内。

MxBuild需要一些命令行选项来控制Mendix 项目的处理方式。 这些选项在项目文件名称之前。

在Windows中，命令行使用以下格式：

`MxBuilding --java-home="JDKDirectory" --java-exe-path="javaExecutable" [options] projectFile`

您也可以使用以下命令行格式在 Linux 下运行 MxBuilding：

`mono mxbuild.exe --java-home="JDKDirectory" --java-exe-path="javaExecutable" [options] projectFile`

创建部署包后，MxBuild进程退出。

{{% alert type="info" %}}
本文档中使用的示例是 Windows。
{{% /报警 %}}

### 2.1 一般指挥线选项


<!-- Note to editor: the &nbsp; here makes the column wider so that options are not broken at hyphens
  The alternative of using non-breaking hyphens means that a cut and paste may not work -->

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 描述                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `-h`, `--help`                                                                                                                                                                                               | 打印一个 MxBuilding 的简短描述和所有可用选项的列表。                                                                                                                                                                                                                                                                       |
| `--java-home=DIRECTORY`                                                                                                                                                                                      | (required) 安装JDK 的目录<br/>例如： `--java-home=/usr/lib/jvm/java-8-oracle`<br/>Windows 的 *DIRECTORY* 应以双引号形式包含： `"`.                                                                                                                                                                            |
| `--java-exe-path=FILENAME`                                                                                                                                                                                   | (required) the **full path** to the Java executable<br/>for example `--java-exe-path=/usr/lib/jvm/java-8-oracle/bin/java`<br/>for Windows the *DIRECTORY* should be enclosed in double-quotes, `"`, and must contain the complete file name `...\java.exe`.                               |
| <code>---target=[包&#124;部署]</code>                                                                                                                                                                                    | `包` (默认，如果省略选项)：创建一个部署包 (. 文件<br/>`部署`: 在不设置部署包的情况下进行项目部署。                                                                                                                                                                                                                                       |
| `--loose-version-检查`                                                                                                                                                                                         | create a deployment package from a project which was created with a lower Mendix version.<br/>The project will be upgraded to the MxBuild version before the deployment package is created.<br /> Any changes included as a result of this upgrade will **not** be stored in your project. |
| `--wring 错误=FILENAME`                                                                                                                                                                                        | 以 JSON 格式写下项目部署到指定文件时遇到的所有错误、警告和废弃。<br />此文件仅在工程包含错误时写入。<br />如果文件已经存在，它将在没有警告的情况下被覆盖。<br />关于此文件的格式，请参见第4节 [项目错误](#project-errors)                                                                                                                                                  |

### 2.2 创建包时的选项

{{% alert type="info" %}}
以下选项仅适用于 `--target=package` 选项：
{{% /报警 %}}

| Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 描述                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `-o FILENAME` or<br/>`--output=FILENAME`                                                                                                                                                                                                                                                                                             | 由 MxBuild创建的 .mda 文件的名称 (可选的相对路径或绝对路径)。<br />如果省略此选项，文件将保存在 *当前* 目录中的名称为 `da`. |
| `--project-name=NAME`                                                                                                                                                                                                                                                                                                                      | 更改 Mendix Runtime 使用的应用程序名称。<br />当未指定此选项时，项目名称将被使用。                           |
| `--model-version=VERSION`                                                                                                                                                                                                                                                                                                                  | 应用特定版本号到软件包中的模型。                                                                     |
| `--model-description=DESCRIPTI`                                                                                                                                                                                                                                                                                                            | 在包中嵌入模型的描述。                                                                          |

例如，创建一个部署包 `out。 da` 在当前目录中，使用 `MyApp` 使用 *Windows* 版本的 MxBuild, 您可以使用命令：

```bat
mxbuild--target=package --java-home="C:\Program Files\JavaScript1.8.0_144"--java-exe-path="C:\Program Files\Java\jdk1.8.0_144\bin\java.exe" "C:\Uers\users\Documents\Mendix\MyApp\MyApp.mpr"
```

## 3 退货代码

当MxBuild退出时，将返回以下代码之一：

| 退出代码 | 描述            |
| ---- | ------------- |
| 0    | MxBuild成功完成   |
| 1    | 发生内部错误        |
| 2    | 命令行选项有错误      |
| 3    | Mendix 项目部署失败 |


如果退出代码大于 0，MxBuild也会输出描述错误的消息。

## 4 个项目错误 {#project-errors}

当您的 Mendix 项目包含错误时，部署将失败，MxBuild将报告这些错误。 您可以使用 `--wrarderrors=FILENAME` 命令行选项来告诉MxBuilding 将错误写入文件。

错误是作为具有一个属性的 JSON 对象输出： `个问题`。 此属性的值是一个数组对象，每个对象都描述你项目中的一个错误、警告或废弃。 例如：

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

| 财产     | 描述                                             |
| ------ | ---------------------------------------------- |
| `名称`   | 问题的唯一标识符，或 `null` 当Mendix Metamodel中尚未定义一致性检查。 |
| `严重程度` | 描述问题类型： `警告`, `错误` 或 `废弃`。                     |
| `留言`   | 对问题的描述。 这与Mendix Modeler的“错误”基座中的消息相同。         |
| `位置`   | 包含描述Mendix 项目中出现问题的位置的零或更多对象（见下表）。             |

与问题相关的地点具有以下属性：

| 财产          | 描述              |
| ----------- | --------------- |
| `elementId` | 发生问题的模型元素的唯一ID。 |
| `单位ID`      | 发生问题的文件中的唯一标识。  |
| `元素`        | 对问题发生的模型元素的描述。  |
| `文档`        | 说明问题发生的文档。      |
| `模块`        | 问题发生的模块描述。      |
