---
title: "ハイブリッドアプリのカスタマイズ"
category: "モバイル開発"
---

Mendixモバイルアプリと生成されたハイブリッドモバイルアプリには、独自の `index.html` ファイルが含まれています。 このインデックス ファイルは、例えば CSS ファイルを追加するために編集することはできません。 ただし、 `components.json` と呼ばれるファイルから間接的にインデックスファイルを変更することができます。 そこで、CSSとJavaScriptファイルを追加できます。 これらは `components.json` の最初の内容です:

**標準 'components.json'**

```js
{
    "files": {
        "css": [
            "lib/bootstrap/css/bootstrap.min.css",
            "mxclientsystem/mxui/ui/mxui.css",
            "css/theme.css"
        ],
        "js": [ "mxclientsystem/mxui/mxui.js" ]
    }
}

```

より多くのリソースを含めたい場合は、テーマのルートに独自の `components.json` ファイルを追加できます。 上記のバージョンをコピーし、独自のファイルを追加します。 これは、 `index.html` に JavaScript ファイルを動的に追加する例です。

**カスタム 'components.json'**
```js
{
    "files": {
        "css": [
            "lib/bootstrap/css/bootstrap.min.css",
            "mxclientsystem/mxui/ui/mxui.css",
            "css/theme.css"
        ],
        "js": [ 
            "mxclientsystem/mxui/mxui.js",
            "myOwnCode.js"
        ]
    }
}
```
