---
title: "Container"
parent: "container-widgets"
---

A container widget can be used to style or simultaneously hide a group of widgets. In the browser, it is rendered as a simple `div` element by default. It is also possible to render a container as one of HTML5 sementic elements (for example, `section`, `main`, `article`, `nav`).

{{% alert type="info" %}}

![](attachments/16713858/16843976.png) An empty container.

{{% /alert %}}

## Common properties

{{% snippet file="refguide7/Name+Property.md" %}}

{{% snippet file="refguide7/Class+Property.md" %}}

{{% snippet file="refguide7/Style+Property.md" %}}

## General properties

### Render mode

The render mode determines which HTML5 tag will be used to show the container in the web browser.

| Value   | HTML Tag  |
| ------- | --------- |
| Div     | `div`     |
| Section | `section` |
| Article | `article` |
| Header  | `header`  |
| Footer  | `footer`  |
| Main    | `main`    |
| Nav     | `nav`     |
| Aside   | `aside`   |
| Hgroup  | `hgroup`  |
| Address | `address` |

_Default value:_ Div

## Visibility properties

{{% snippet file="refguide7/Visibility+Property.md" %}}

{{% snippet file="refguide7/Visibility+Property+With+Module+Roles+Simple.md" %}}
