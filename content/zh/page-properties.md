---
title: "页面属性"
parent: "页面"
menu_order: 10
tags:
  - "studio pro"
  - "页面"
  - "属性"
---

## 1 导言

此文档描述页面属性。 关于哪些页面的详细信息以及哪些小部件可以放置在它们上，参见 [页面](pages)。

## 2 属性

下面的图像是页面属性的示例：

{{% image_container width="250" %}}![页面属性](attachments/page/page-properties.png)
{{% /image_container %}}

页面属性由以下部分组成：

* [常用的](#common)
* [设计师](#designer)
* [A. 概况](#general)
* [Navigation](#navigation)
* [弹出窗口](#pop-up)
* [用法](#usage)

### 2.1 共同部分 {#common}

{{% snippet file="refguide/common-section-link.md" %}}

### 2.2 设计师科 {#designer}

{{% snippet file="refguide/designer-properties.md" %}}

### 2.3 一般部分 {#general}

#### 2.3.1 平台

**平台** 属性的值是：

* Web *(默认)* — 即将显示在浏览器或混合移动应用程序中的页面
* 原生——将在本地移动应用中显示的页面

#### 2.3.2 布局类型 {#layout-type}

**布局类型**, 决定页面的目的和它的开启方式。

| 布局类型       | 描述                                                          |
| ---------- | ----------------------------------------------------------- |
| **响应性**    | 在所有类型设备上都能正常工作的页面。                                          |
| **绘图板特定的** | 将显示在平板电脑上的页面，因为响应选项没有在平板电脑上提供一个好的用户界面。                      |
| **专用电话**   | 在手机上显示页面，因为响应选项没有在手机上提供一个好的用户界面。                            |
| **弹出模式**   | 显示为 [模式弹出窗口](https://www.wikiwand.com/en/Modal_window) 的页面。 |
| **弹出窗口**   | 显示为 *的页面* 弹出窗口。                                             |

#### 2.3.3 布局

此页面基于的 [布局](layout)。

#### 2.3.4 标题 {#title}

使用 [页面标题小部件](page-title) 显示的页面标题。 如果页面显示在弹出窗口中，标题会出现在弹出窗口的标题栏中。

标题可以覆盖。 例如， [创建按钮](control-bar) 和 [编辑按钮](control-bar) 数据网格可以引用同一页面， 但是他们分别将标题覆盖到 **新的** 和 **编辑**中。

#### 2.3.6 URL

页面的 URL 可以直接导航到页面(例如，从外部链接或书签)。 当您访问页面时，它将显示在浏览器的地址栏中。 当导航到没有配置URL的页面时，会显示最后访问过的URL。 请注意，页面的完整URL将是您应用程序的基础URL，然后是 `/p` ，然后是页面的已配置的 URL (例如) `http://示例。 endixcloud.com/p/home_page`)。

具有顶级数据视图(参数化页面)的页面也可以有URL。 此页面的 URL 属性应该包含结尾处的 `{Id}` 路径段。 在浏览器中， `{Id}` 部分将被实体的实际标识符所取代。

在简单的电子商务应用程序中，URL可以配置如下：

* */orders/* — 一个带有 `订单数据网格的页面的 URL` (在浏览器中) URL将看起来像 `http://示例。 endixcloud.com/p/p/orders/`)

* */order/{Id}* - 包含特定数据的页面的 URL `订单` (在浏览器中) URL将看起来像 `http://示例。 endixcloud.com/p/order/3212449487634321`, 其中 `3212449487634321` 是 `命令` 的唯一标识符

### 2.4 导航部分 {#navigation}

#### 2.4.1 可见性

此属性定义了页面可见的模块角色。 这对 [菜单部件](menu-widgets) 和仅允许时可见的按钮有影响 (例如) 用于编辑的 [动作按钮](button-widgets)

欲了解更多信息，请参阅 [Module Security](module-security)。

### 2.5 弹出部分 {#pop-up}

**弹出式** 部分仅用于弹出式页面。 关于弹出页面的更多信息，请参阅 [布局类型](#layout-type) 部分。

#### 2.5.1 宽度 (像素)

此属性以像素为单位指定弹出页面宽度。 当设置为 0时，宽度将自动确定。

默认： *0*

#### 2.5.2 高度 (像素)

此属性指定弹出页面高度以像素为单位。 当设置为 0时，高度将自动确定。

默认： *0*

#### 2.5.3 Resizable

此属性指定最终用户是否可以调整弹出窗口大小.

默认： *是*

#### 2.5.4 近距离行动

配置关闭弹出页面按钮的行为。 弹出窗口关闭按钮的默认行为是回滚任何更改并关闭弹出窗口。

如果您想要自定义弹出式关闭按钮的行为，您可以指向页面上的按钮。 当弹出式关闭按钮被点击时，它会像点击所选按钮一样。 如果选中的按钮不可用，弹出式关闭按钮将恢复为默认行为。

默认： *默认 (cancel)*

### 2.6 使用部分 {#usage}

#### 2.6.1 标记为已使用

您可以通过按 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>F</kbd> 在Studio Pro 中搜索未使用的项目。 仅使用 Java 代码的页面将被列为未使用的页面，因为Studio Pro 无法在 Java 源代码中看到。

By setting the property **Mark as used** to *Yes*, you specify that the document is used implicitly and Studio Pro will no longer list it when searching for unused items.

*默认值*: 否