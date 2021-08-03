---
title: "制止规则"
parent: "errors-pane"
menu_order: 10
description: "在Studio Pro描述用于警告的抑制规则。"
tags:
  - "Studio Pro"
  - "一致性错误"
  - "检查"
  - "警告"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/suppression-rules.pdf)。
{{% /报警 %}}

## 1 导言 {#intro}

当您在一个项目上工作时，Studio Pro 进行一致性检查，这可能会导致警告。 警告确定了一些不是关键问题的问题，但指出了可能是一个问题的问题。 这些警告在 **错误** 面板中显示。

![错误窗格中的警告](attachments/suppression-rules/errors-pane-with-warnings.png)

虽然警告可能是有价值的，但有些情况下您可能想要禁用它们，如：

* 你在你的项目中做出了有意识的选择，导致警告，你知道这不会导致问题。
* 您正在使用包含警告的市场模块，不想更改市场模块。
* 警告的数量太大， **警告** 标签页已不可用。 您想要暂时禁用其中的一些内容。

使用 **抑制规则** 是可以禁用警告的。 You can [suppress warnings](#suppress-warning) from the **Errors** pane and [manage them](#managing-rules) via the **Suppression rules** option. 也可以使用 [抑制所有应用市场模块](#suppress-appstore-warnings) 的警告。

## 2 抑制规则逻辑。 {#suppression-rules-logic}

抑制规则适用于一个用户和一个项目的一个实例。 您抑制的警告不是在用户或项目之间共享的。 对于在同一个项目上工作的团队成员来说，警告不会被压制。

抑制规则在本地存储在一个名为 *project-settings.user.json* 的文件中。 将您的更改提交给团队服务器时，Studio Pro 将忽略此文件。

![在 Windows Explorer 中显示的设置文件](attachments/suppression-rules/windows-explorer-showing-settings-files.png)

然而，可以手工进出口制止规则。 关于如何导出和导入警告的更多信息，请参阅 [导出您的抑制规则](#export) and [导入您的抑制规则](#import) 章节。

## 3 在错误面板中压制警告 {#suppress-warning}

从 **错误** 面板，您可以压制文档、模块或整个项目的警告： ![抑制警告](attachments/suppression-rules/suppressing-warning.png)

### 3.1 制止对具体文件提出警告

只对特定文件制止警告，请做以下操作：

1. 右键单击您想要取消的警告。

2. 选择 **禁止此警告** > **文档 {Document name}**。


此警告仅在特定文档中被压制。 如果在另一个文档中出现相同的警告(例如在另一页)，它仍然会显示该文档。

### 3.2 制止特定模块的警告

为了阻止某个特定模块的警告，请执行以下操作：

1. 右键单击您想要取消的警告。

2. 选择 **禁止此警告** > **模块 {Module name}**。


整个模块的警告被压制。 如果在另一个模块中出现同样的警告，它仍将被显示为该模块。

### 3.3 禁止整个项目的警告

为整个项目制止警告，做以下工作：

1. 右键单击您想要取消的警告。

2. 选择 **禁止此警告** > **整个项目**。


警告被整个项目压制，并在 **错误** 面板中更新警告列表。

关于如何编辑或删除抑制规则的更多信息，请参阅 [管理抑制规则](#managing-rules) 部分。

## 4 管理制止规则 {#managing-rules}

您可以添加、编辑、删除、导出或导入抑制规则。 您也可以抑制来自市场的警告。

{{% alert type="info" %}}
修改抑制规则后，点击 **确定** 关闭 **管理抑制规则** 对话框并应用更改。
{{% /报警 %}}

### 4.1 取缔AMarketplace 警告 {#suppress-appstore-warnings}

为了抑制市场警告，请做以下工作：

1.  点击 **抑制规则** 按钮在 **错误** 窗格中。

    ![查看抑制警告规则](attachments/suppression-rules/errors-pane-suppress-warnings-button.png)

2. 在 **管理抑制规则** 对话框中，检查 **禁用市场模块** 选项。

    ![抑制市场警告](attachments/suppression-rules/rules-dialog-app-store-setting.png)

3. 点击 **确定** 应用新设置。

来自市场模块的警告已被制止。

### 4.2 增加一条规则

对于更高级的情况，您可能想要手动添加一个新的规则。 这使您能够在决定要抑制哪些警告时完全控制规则使用的设置。

要手动添加新规则，请按下面的步骤：

1. 点击 **抑制规则** 按钮在 **错误** 窗格中。

2. 在 **管理抑制规则** 对话框中，选择 **新的** 按钮：

    ![规则窗口 - 新按钮](attachments/suppression-rules/rules-dialog-new-button.png)

3. 在 **添加抑制规则** 对话框中， 设置添加规则的必要选项(关于设置的更多信息，请参阅 [规则设置](#rule-settings) 部分)。

    ![规则窗口 - 添加抑制项](attachments/suppression-rules/new-warning-window.png)

4. 点击 **确定** 来确认您的选择。

5. 在 **管理抑制规则** 对话框中点击 **确定** 以保存您的更改。

已创建抑制规则。


### 4.3 编辑规则

要编辑现有的规则，请按照下面的步骤：

1. 点击 **抑制规则** 按钮在 **错误** 窗格中。

2.  在 **管理抑制规则** 对话框中，选择 **编辑** 按钮：

    ![规则窗口 - 编辑按钮](attachments/suppression-rules/rules-dialog-edit-button.png)

3.  在 **编辑抑制规则** 对话框中，编辑更改规则的选项 (对于设置的更多信息)。 查看 [制止规则设置](#rule-settings) 部分。

    ![规则设置窗口](attachments/suppression-rules/rule-settings-window.png)

4. 点击 **确定** 来确认您的选择。

5. 在 **管理抑制规则** 对话框中点击 **确定** 以保存您的更改。

抑制规则已编辑。


### 4.4 删除规则

若要删除现有规则，请采取以下步骤：

1. 点击 **抑制规则** 按钮在 **错误** 窗格中。

2.   在 **管理抑制规则** 对话框中，点击 **删除** 按钮：

    ![规则窗口 - 删除按钮](attachments/suppression-rules/rules-dialog-delete-button.png)

抑制规则已删除。


### 4.5 进口制止规则 {#import}

为了进口制止规则，请采取以下行动：

1. 点击 **抑制规则** 按钮在 **错误** 窗格中。

2.  在 **管理抑制规则** 对话框中，选择 **导入** 按钮：

    ![导入规则按钮](attachments/suppression-rules/import-rules.png)

3. 浏览到您想要导入的文件夹(您正在导入的文件扩展名必须是 *.suppressions.json*)。

4. 点击 **打开** 来选择该文件。

5.  在确认弹出窗口中，点击 **确定** 来关闭它：

    ![导入规则确认](attachments/suppression-rules/confirmation-dialog-after-rules-imported.png)

6. 在 **管理抑制规则** 对话框中点击 **确定**。

警告列表已更新。


### 4.6 导出您的抑制规则 {#export}

要导出您的抑制规则，请执行以下操作：

1. 点击 **抑制规则** 按钮在 **错误** 窗格中。

2.  在 **管理抑制规则** 对话框中，选择 **导出** 按钮：

    ![导出规则按钮](attachments/suppression-rules/export-rules.png)

3. 浏览到要导出规则的文件夹 (默认文件名是 `<your app name>.suppressions.json`)。

4. 点击 **保存** 按钮以保存导出的规则。

5.  在确认弹出窗口中，点击 **确定** 来关闭它：

    ![导出规则确认](attachments/suppression-rules/confirmation-dialog-after-rules-exported.png)

6. 在 **管理抑制规则** 对话框中点击 **确定**。

您的抑制规则已导出。 Another user can [import](#import) that file to use the same suppression rules.


## 5 抑制规则设置 {#rule-settings}

下表描述了可用设置：
仅在 **错误代码** 选项在上面的</strong> 选择器的 **禁止中被选择时才显示。 您可以输入一个特定的错误代码，例如 **CW1234**, 来制止这个特定的警告。</td> </tr> </tbody> </table> 



## 6 阅读更多 {#read-more}

* [Errors Pane](errors-pane)
* [一致性错误](一致性错误)
