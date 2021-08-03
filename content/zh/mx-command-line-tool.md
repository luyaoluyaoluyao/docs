---
title: "mx 命令行工具"
category: "常规信息"
menu_order: 50
description: "描述mx 命令行工具的选项"
tags:
  - "毫克"
  - "项目"
  - "命令行"
  - "工具"
  - "毫克"
  - "studio pro"
  - "窗口"
  - "linux"
---

## 1 导言

**mx 工具** 是一个 Windows 和 Linux 命令行工具，可用来在您的 Mendix 应用程序中做有用的事情。

## 2 个位置

Mendix Studio Pro 带有mx 命令行工具。 可执行文件 `mx.exe` 可以在同一个包含 `studio.exe` 的文件夹中找到(例如， *C:\Program Files\Mendix\8.1.0.58215\model\mx.exe*)。

## 3 mx 工具选项

mx 工具启用了下面描述的选项。

### 3.1 mx 转换命令

`mx 转换` 命令将应用程序转换为 Studio Pro 特定版本。 例如，如果您使用 mx command-line 工具为 Mendix 版本 8.0 。 8215, 然后 `mx 转换` 将会将应用程序转换为那个版本。

输入的文件可以是单个文件、目录或多个文件。

{{% alert type="info" %}}
mx 工具只能升级您的应用，但您不能用它来降级版本。
{{% /报警 %}}

#### 3.1.1 使用

使用 `mx 转换` 的命令模式：

`mx convert [OPTIONS] INPUT... 输出输出`

下面的表格描述了 `选项`

| 选项            | 快捷方式  | 结果                                                               |
| ------------- | ----- | ---------------------------------------------------------------- |
| `--help`      | `-小时` | 显示帮助文本并退出。                                                       |
| `--inplace`   | `-p`  | 转换当前应用目录。 使用此选项来转换包含 Mendix 应用程序的文件夹。 否则， `mx 转换` 将转换 *.mpk* 文件。 |
| `--skip 错误检查` | `- 秒` | 不检查错误。 使用此选项在转换过程中禁用应用错误检查。 当省略时，该工具将报告应用程序中的错误、警告和弃置次数，并进行转换。   |

对于 `INPUT...`, 请输入一个或多个 *.mpk* 文件或一个需要转换的目录。

对于 `OUTPUT`, 输入转换结果的输出位置。 输入以下内容：

* 当 `INPUT时...` 是一个单一的文件， `OUTPUT` 可以是一个单一的文件或目录； 否则, `OUTPUT` 必须是一个目录。
* 使用 `--place` 选项时， `INPUT...` 文件夹也将用作 `OUTPUT` 文件夹， 所以您不需要指定一个单独的 `OUTPUT` 文件夹

#### 3.1.2 实例

以下表格介绍了命令的示例：

| 示例                                                                                                                                                                                         | 结果                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------- |
| `mx 转换 --in place C:\MxProjects\App-main`                                                                                                                                                | 将文件夹 `C:\MxProjects\App-main` 的应用转换为 mx 工具捆绑的特定Studio Pro 版本。 |
| ``mx 转换 C:\Mendix\App1.mpk C:\Mendix\App2.mpk C:\Mendix\ConvertedProjects\` | 转换 *App1.mpk* 和 *App2. pk* 应用程序包位于*C:\Mendix\* 文件夹中，并将结果放入``C:\Mendix\ConvertedProjects\`文件夹。 |                                                                 |
| ``mx 转换 --skip-error-check C:\Mendix\Packages\ C:\Mendix\ConvertedPackages\` | 将``C:\Mendix\Packages\`文件夹中的所有应用程序包转换为 `C:\Mendix\ConvertedPackages\` 文件夹而不检查错误。            |                                                                 |

#### 3.1.3 返回码

下表说明了返回代码：

| 退出代码 | 描述        |
| ---- | --------- |
| 0    | 转换成功。     |
| 1    | 发生内部错误。   |
| 2    | 命令行选项有问题。 |
| 3    | 转换失败。     |

### 3.2 mx create-project 命令

`mx create-project` 命令在Studio Pro中创建了一个新的应用程序。 应用程序版本取决于工具被捆绑的版本。 例如，如果您正在使用 Studio Pro 8.1.0 版本的 mx 工具。 8215,  `mx creating project` 将在那个版本中创建一个新的应用。

#### 3.2.1 使用

使用以下命令模式： `mx create-project [OPTIONS] [TEMPLATE-MPK-FILE]`

下面的表格描述了 `选项`

| 选项               | 默认值  | 结果                                                                                                                                                   |
| ---------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `应用程序名称`         | 应用   | 将指定的应用名称分配给应用程序。                                                                                                                                     |
| `输出目录`           | 当前目录 | 要创建项目的目录。                                                                                                                                            |
| `语言代码`           | 可选的  | 应用程序的默认语言。                                                                                                                                           |
| `sprintr-app-id` | 可选的  | Associates the app [feedback features](/developerportal/collaborate/feedback) with the provided [Developer Portal app](/developerportal/apps-list/). |

`TEMPLATE-MPK-FILE` 是Mendix 应用包的可选路径(*.mpk*) 文件。 如果省略此参数，应用程序将使用默认的空项目模板创建。

#### 3.2.2 实例

以下表格介绍了命令的示例：

| 示例                                                                                | 结果                                                            |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| `mx 创建项目`                                                                         | 使用所有默认参数在当前文件夹中创建应用程序。                                        |
| `mx create-project --app-name "MyFirstApp" --output-dir "C:/Projects/MyFirstApp"` | 在 *C:/Projects/MyFirstApp* 使用所有默认参数创建一个名为 `MyFirstApp` 的应用程序。 |
| `mx create-project "C:/Templates/ExpenseReportTemplate.mpk"`                      | 从位于 *C:/Templates/ExpenseReportTemplate.mpk* 的模板创建一个默认参数。     |

#### 3.2.3 退货代码

下表说明了返回代码：

| 退出代码 | 描述        |
| ---- | --------- |
| 0    | 应用程序创建成功。 |
| 1    | 发生内部错误。   |
| 2    | 命令行选项有问题。 |

### 3.3 未记录的选项

mx 工具包含未在本文档中描述的选项。 这些是供Mendix 内部使用的，没有得到官方支持。 这可能会在将来发生变化，但这些选项只能由您自己承担风险。
