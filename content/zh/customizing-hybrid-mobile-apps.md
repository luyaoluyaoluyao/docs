---
title: "自定义混合移动应用程序"
parent: "混合移动设备"
tags:
  - "studio pro"
---

## 1 导言

Mendix 移动应用程序和生成混合移动应用程序包含他们自己的 `index.html` 文件。 此索引文件不能被编辑以添加 CSS 文件。 然而，您可以通过一个名为 *components.json* 的文件间接更改索引文件。 在这里，您可以添加 CSS 和 JavaScript 文件。 这些是 *components.json* 的初始内容：

## 2 标准组件.json

```js
很抱歉，
    "files":
        "css": ["styles/web/css/main.css"],
        "js": ["mxclientsystem/mxui/mxui.js"]
    },
    "cachebust": "{{cachebust}}"
}

```

如果你想要包含更多的资源，你可以在主题根目录中添加你自己的 *components.json* 文件。 复制上面的版本并添加您自己的文件。 这是一个动态将 JavaScript 文件添加到 `index.html` 的示例：

## 3 个自定义组件.json

```js
很抱歉，
    "files":
        "css": ["styles/web/css/main.css"],
        "js": [
        "mxclientsystem/mxui/mxui.js",
        "myOwnCode.js"
    ]
    },
    "cachebust": "{{cachebust}}"
}
```
