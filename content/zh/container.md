---
title: "容器"
parent: "容器部件"
---

容器部件可以用来样式或同时隐藏一组部件。 在浏览器中，默认情况下它是一个简单的 `div` 元素。 还可以将一个容器变成HTML5的一个化验元件(例如) `部分`, `main`, `article`, `nav`).

{{% alert type="info" %}}

![](attachments/16713858/16843976.png) 空容器。

{{% /报警 %}}

## 共同属性

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## 常规属性

### 渲染模式

渲染模式决定哪些HTML5标签将用于在网页浏览器中显示容器。

| 值                    | HTML 标签  |
| -------------------- | -------- |
| Div                  | `div`    |
| 1 P-5, 1 P-4, 1 P-3, | `部分`     |
| 第 1 条                | `文章`     |
| 标题                   | `标题`     |
| 页脚                   | `页脚`     |
| 主要的                  | `主要的`    |
| Nav                  | `nav`    |
| 旁边                   | `留言`     |
| Hgroup               | `hgroup` |
| 地址                   | `地址`     |

_Default value:_ Div

## 可见性属性

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguid7/Visibility+Property+With+Module+Roles+Simple.md" %}}
