---
title: "模块安全"
parent: "安全"
menu_order: 20
tags:
  - "studio pro"
  - "模块安全"
  - "安全"
  - "模块"
aliases:
  - /refguide8/module-role.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 对于简体中文翻译，请点击 [中文为 xix x](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/module-security.pdf)。
{{% /报警 %}}

## 1 导言

{{% alert type="info" %}}
欲了解更多安全信息，请参阅 [Security](security)。
{{% /报警 %}}

在模块中，您可以定义模块角色并指定页面、微流、实体和数据集的安全设置。

## 2 个模块角色 {#module-role}

模块角色定义了一组您可以分配给用户的访问权限。 关于模块角色的更多信息， [用户角色](user-roles)及其关系，见 [Security](security)。

模块角色具有以下属性：

* **名称** - 模块角色的名称； 最终用户看不到模块角色的名称。如果他们创建或查看用户账户，他们只看到用户角色的名称
*  **文档** - 模块角色的文档仅供Studio Pro 用户使用。 它不显示给最终用户

    ![](attachments/module-security/module-roles-tab.png)

## 2 页访问

**页面访问** 定义了每个角色可见的页面。 **页面访问** 标签被显示为一个矩阵，显示页面和模块角色。

![页面访问选项卡](attachments/module-security/page-access-tab.png)

对于每个组合，您都可以指明该页面是否为模块角色可见。 您也可以在页面中编辑此信息，使用</strong> 属性的 **可见性。</p>

指定角色不可见的页面不会在导航结构中显示。 并且 **默认情况下，打开页面** 按钮导致该页面不会呈现。

页面访问设置不限制用户通过其他方式导航到页面。 例如，通过一个深度链接或通过一个被强制可见的按钮(用于更多信息) 查看 [常见小部件属性](common-widget-properties)。 如果您想要确保特定角色不能访问您的部分数据或逻辑， 超过这一点必须通过 **实体访问** 和 **微流程访问** 表示.

## 3 个微流程访问

**Microflow Access** 定义了哪些微流可以由具有特定模块角色的用户执行。 菜单栏是最优化的，以便它只显示用户可以访问的页面和微流。

**微流程访问** 标签被显示为一个矩阵，显示微流程和模块角色。

![](attachments/module-security/microflow-access-tab.png)

对于每个组合，您可以指出模块角色是否可以访问微流。 您也可以使用 **允许的角色** 在一个 [微流](microflow) 中编辑此信息。

{{% alert type="info" %}}
请注意，这些角色仅在从客户端执行微流程时才会被检查。 微流程总是允许调用另一个微流程，当时不会检查这些角色。
{{% /报警 %}}

## 4 个实体访问 {#entity-access}

**实体访问** 定义每个模块角色是否授权具有此角色的用户 **创建** **读取**, **写入** 和/或 **删除** 实体对象。 您也可以写 XPath 约束来限制访问规则所适用的对象集。

**实体访问** 标签被显示为一个矩阵，显示适用于实体的访问规则：

![](attachments/module-security/entity-access-tab.png)

每个访问规则都适用于一组模块角色。 欲了解更多信息，请参阅 [访问规则](access-rules)。

## 5 OData Access

**OData Access** 定义了每个模块的角色，是否授权具有此角色的用户访问在模块中曝光的每个OData服务。

**OData Access** 标签作为矩阵显示已发布的 OData 服务和模块角色：

![](attachments/module-security/odata-access-tab.png)

对于每个组合，您可以指出模块角色是否可以访问已发布的 OData服务。 您也可以在 [发布的 OData 服务](published-odata-services) 中使用 **允许的角色** 属性在 **设置** 选项卡中编辑此信息。

## 6 REST 访问

**REST Access** 定义每个模块角色是否授权具有此角色的用户访问在模块中曝光的每个REST 服务的REST 资源。

**REST Access** 标签作为矩阵显示已发布的REST 服务和模块角色：

![](attachments/module-security/rest-access-tab.png)

对于每个REST 服务，您可以指出模块角色是否可以访问已发布的REST 服务。

**REST Access** 标签只有在服务安全设置需要认证时才可见。 欲了解更多信息，请参阅 [已发布的REST服务](published-rest-services)。

## 7 个数据集访问

**数据集访问** 显示了模块角色对每个 [数据集](data-sets) 的访问权限。

| 值    | 描述                               |
| ---- | -------------------------------- |
| 完全访问 | 数据集参数不适用约束，允许所有可能的范围参数。          |
| 访问限制 | 至少一个约束适用于数据集的参数，或者至少一个范围参数是不允许的。 |
| 无访问  | 具有此模块角色的用户无法访问数据集。               |

{{% alert type="info" %}}
数据集的参数定义定义了限制因素。 是否应用在 **数据集访问** 中定义。 范围是在数据集参数中定义的。 是否允许这些范围内的值在 **数据集访问** 中定义。
{{% /报警 %}}

## 8 阅读更多

* [安全](安全)
* [用户角色](user-roles)
