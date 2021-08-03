---
title: "工作流属性"
category: "工作流"
menu_order: 10
tags:
  - "工作流"
  - "工作流"
  - "Workflow 属性"
  - "工作室"
---

## 1 导言

此文档描述了工作流属性。 关于什么是工作流以及你可以在那里使用哪种元素的详细信息，请参阅 [工作流](workflows)。

## 2 工作流属性

Workflow 属性由以下部分组成：

* [A. 概况](#general)
* [数据](#data)
* [显示信息](#display-info)
* [权限](#permissions)
* [截止日期](#due-date)
* [管理页面](#admin-page)

### 2.1 一般部分 {#general}

**常规** 部分包含有关工作流程标题和名称的信息。

![一般部分](attachments/workflow-properties/general.jpg)

**常规** 章节属性在下表中描述：

| 财产 | 描述                                          |
| -- | ------------------------------------------- |
| 标题 | 定义您在工作区顶部看到的工作流标题。                          |
| 名称 | 必须唯一工作流的内部名称。 当在应用程序中使用 Workflow 时，您将使用此名称。 |

### 2.2 数据科 {#data}

**Data** 部分包含了关于工作流使用什么数据环境的信息。

![数据部分](attachments/workflow-properties/data.jpg)

**Workflow entity** 是一个被用作工作流环境的实体。 这个实体是工作流程的输入，并且可以保存执行工作流程过程中添加的数据。 例如，在核准开支的过程中，它持有批准金额和目的。

此实体应为工作流实体类型。 For more information, see the [Entities and Their Types](domain-models#entity-types) section in the *Domain Model*.

### 2.3 显示信息部分 {#display-info}

**显示信息** 部分定义了工作流名称及其在运行 (已发布) 应用程序中显示的描述。

![显示信息部分](attachments/workflow-properties/display-information.jpg)

下面的表格描述了 **显示信息** 部分属性：

| 财产    | 描述                                                                                                                            |
| ----- | ----------------------------------------------------------------------------------------------------------------------------- |
| 工作流名称 | **工作流名称** 显示在运行中的应用中。 **工作流名称** 可以包含表达式结果，这些结果将显示给最终用户。 例如， 您可以从 **员工在线** 数据添加 **完整名称** 属性值以显示新员工的名称。 表达式应该返回一个字符串值。          |
| 工作流描述 | **工作流描述** 是对正在运行的应用程序中显示的工作流的描述。 **工作流名称** 可以包含表达式结果，这些结果将显示给最终用户。 例如， 您可以从 **员工在线上添加 **第一天** 属性值** 数据来显示新员工的开始日期并指派他们到一个培训组。 |

### 2.4 权限部分 {#permissions}

**允许的角色** 定义了可以触发工作流程的 [用户角色](settings-security#roles-and-permissions)。

![权限部分](attachments/workflow-properties/permissions.jpg)

{{% alert type="info" %}}
此部分仅在开启安全时才显示。 欲了解更多信息，请参阅 [Security](settings-security)。
{{% /报警 %}}

### 2.4 截止日期部分 {#due-date}

**到期日** 部分允许您为工作流设定一个截止日期并跟踪它。 然而，这并不是自动提醒，而是在跟踪工作流程时你提到的最后期限。 例如，您可以使用此截止日期来显示在仪表盘中逾期的工作流。

![截止日期部分](attachments/workflow-properties/due-date.jpg)

**到期日** 部分属性在下表中描述：

您可以设置工作流的截止日期，并在</strong> 选项中包含 **到期时间 它表示工作流到期的小时数、天数或周数。 该属性的可能值如下：<br /><ul><li>小时数</li><li>日 (秒)</li><li>周数</li> </ul></td> </tr> 

</tbody> </table> 



### 2.5 管理页面部分 {#admin-page}

**覆盖管理页面** 是一个可用来显示所有正在运行的工作流到工作流管理员的可选页面。 这将覆盖用于在应用程序中显示任何正在运行的工作流的通用页面，例如： 当您有一个 **显示工作流页面** 设置为 [点击动作](page-editor-widgets-events-section#show-workflow-page) 或为 [微流活动](microflows#microflow-workflow-activities) 设置为此事件/活动所选择的页面。 

![工作流页面部分](attachments/workflow-properties/workflow-page.jpg)



## 3 阅读更多

* [工作流](workflows)