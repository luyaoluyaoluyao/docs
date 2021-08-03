---
title: "侧边栏切换按钮"
parent: "布局部件"
---


侧边栏切换是一个按键，当按下时会使一个 [滚动容器](scroll-container) 区域出现或消失。 这就可以创建侧边栏， 例如，移动电话上的菜单默认隐藏，可以点击按钮显示。 查看使用侧边栏切换的示例布局。

![](attachments/pages/sidebar-toggle-button.png)

## 按钮属性

{{% snippet file="refguide7/Caption+Property.md" %}}

{{% snippet file="refguide7/Image+Property.md" %}}

{{% snippet file="refguid7/Render+Mode+Property.md" %}}

{{% snippet file="refguide7/Button+Style+Property.md" %}}

## 共同属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

{{% snippet file="refguide7/Tab+index+Property.md" %}}

## 常规属性

### 地区

点击此按钮来选择要折叠/扩展的区域。

| 地区 | 效果            |
| -- | ------------- |
| 左侧 | 将切换布局容器的左侧区域。 |
| 右侧 | 将切换布局容器的右侧区域。 |

{{% alert type="info" %}}

侧边栏切换是右至左(RTL)，这意味着用RTL语言，如果您选择 'Left'，侧边栏将从右侧滑入。}

{{% /报警 %}}

_默认值：_ 左侧

### 模式

确定切换区域。

| 模式     | 效果                                         |
| ------ | ------------------------------------------ |
| 保留推送内容 | 侧边栏将其余内容移至屏幕外(仅在 Mendix 5.17 及以上版本中可用的模式)。 |
| 滑动内容   | 侧边栏在内容上移动。                                 |
| 收缩内容   | 内容缩减以便为侧边栏腾出空间。                            |

### 最初打开

仅在模式为“收缩内容”时适用。

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Extened.md" %}}
