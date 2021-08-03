---
title: "チャート詳細チートシート"
parent: "chart-widgets"
menu_order: 20
tags:
  - "グラフ"
  - "高度な設定"
  - "デスクトップ モデラー"
  - "レイアウトコントロール"
  - "データのプロパティ"
  - "系列のプロパティ"
---

## 1つの紹介

このリファレンスでは、チャートウィジェットの詳細な構成設定について説明します。

標準チャートは、ウィジェットの設定を通じて最も一般的な設定を提供します。 追加設定は詳細設定から行うことができます。

JSONスニペットを備えたこのチートシートは、事前設定のサンプルを提供します。

完全なリファレンスは [https://plot.ly/javascript/](https://plot.ly/javascript/) にあります。

詳細設定で十分でない場合は、アプリストアの [チャート](https://marketplace.mendix.com/link/component/106437/Mendix/Any-Chart) ウィジェットを参照してください。

## 2 レイアウト (すべてのグラフ) {#layout-all}

レイアウトは、チャートの一般的な外観を制御します。 チャートはレイアウトにJSONプロパティを追加することでカスタマイズされます。

以下は基本的な構成です。

``` json
{
  "font": {
    // font properties
  },
  "title": "CHART TITLE",
  "titlefont": {
    // title font properties
  },
  "hovermode": "closest",
  "showlegend": true,
  "legend": {
    // legend properties
  },
  "hoverlabel": {
    // hover label properties
  },
  "margin": {
    // margin properties
  }
}
```

上記のレイアウトスニペットを使用するには、 *// {some text} プロパティ* とラベルされたすべての行を要素固有の実際のプロパティに置き換えます。

### 2.1 レジェンド

カスタムスタイルを適用するために、以下の凡例プロパティがレイアウト構成に追加されます。

``` json
{
  "legend": {
    "showlegend": true,
    "legend": {
      "bgcolor": "#fff",
      "bordercolor": "#444",
      "borderwidth": 0,
      "font":{
        "family": "Open Sans, verdana, arial, sans-serif",
        "size": 12,
        "color": "black"
      },
      "orientation": "v",
      "traceorder": "normal",
      "tracegroupgap": 10,
      "x": -0.1,
      "xanchor": "right"
    }
  }
}
```

次のようにプロパティを変更することで、凡例の位置を変更できます。

**右:**

``` json
{
  "showlegend": true,
}
```

**左:**

xを長い系列名またはY軸ティックに合わせて調整します。

``` json
{
  "showlegend": true,
  "legend": {
    "xanchor": "right",
    "x": -0.1
  }
}
```

**上:**

``` json
{
  "showlegend": true,
  "legend": {
    "orientation": "h",
    "y": 1.1
  }
}
```

**下部:**

長いX軸ティックの場合、yを-0.2に調整します。

``` json
{
  "showlegend": true,
  "legend": {
    "オリエンテーション": "h",
    "y": "auto"
  }
}
```

**内部:**

``` json
{
  "showlegend": true,
  "legend": {
    "x": 0
  }
}
```

**なし:**

``` json
{
  "showlegend": false
}
```

![凡例の構成](attachments/pages/charts/advanced-layout-legend.gif)

詳細なオプションはこちら: [凡例の設定](https://plot.ly/javascript/reference/#layout-legend).

### 2.2 軸

軸のプロパティは、x 軸と y 軸のグラフに適用されます。 次のように設定できます:

``` json
{
  "xaxis": {
    "gridcolor": "#eaeaea",
    "title": "X-axis",
    "color": "#0000FF",
    "showgrid": false,
    "fixedrange": true,
    "showline": true,
    "side": "bottom"
  },
  "yaxis": {
    "rangemode": "tozero",
    "zeroline": true,
    "zerolinecolor": "#eaeaea",
    "gridcolor": "#eaeaea",
    "color": "#0000FF",
    "title": "Y-axis",
    "showgrid": true,
    "showline": true,
    "fixedrange": true
  }
}
```

![軸の構成](attachments/pages/charts/axes.gif)

その他のオプションはこちらでご覧いただけます: [軸設定](https://plot.ly/javascript/reference/#layout-xaxis).

### 2.3 複数の Y 軸

これらのプロパティは、複数の Y 軸を持つグラフに適用されます。 次のように設定できます:

``` json
{
  "yaxis": {
    "title": "Y-axis 1",
    "zeroline": true,
    "color": "#4682B4",
    "showgrid": true,
    "showline": true
  },
  "yaxis2": {
    "title": "Y-axis 2",
    "color": "#FF8C00",
    "showgrid": true,
    "showline": true,
    "zeroline": true,
    "overlaying": "y",
    "side": "right"
  }
}
```

上記のレイアウト プロパティは、対応する [データ プロパティ](#multiple-y-axes-data-properties) で使用する必要があります。

![複数のY軸の構成](attachments/pages/charts/multiple-y.gif)

より多くのオプションがここにあります: [複数のY軸設定](https://plot.ly/javascript/multiple-axes/).

### 2.4 複数の X 軸

これらのプロパティは、1 つ以上の X 軸のグラフに適用されます。 次のように設定できます:

``` json
{
  "xaxis": {
    "title": "X-axis 1",
    "color": "#4682B4",
    "showgrid": true,
    "showline": true,
    "zeroline": true
  },
  "xaxis2": {
    "title": "X-axis 2",
    "titlefont": {
      "color": "#FF8C00"
    },
    "tickfont": {
      "color": "#FF8C00"
    },
    "zeroline": true,
    "color": "#FF8C00",
    "showgrid": true,
    "showline": true,
    "overlaying": "x",
    "side": "top"
  }
}
```

上記のレイアウト プロパティは、対応する [データ プロパティ](#multiple-x-axes-data-properties) で使用する必要があります。

![複数の X 軸の構成](attachments/pages/charts/multiple-x.gif)

より多くのオプションがここにあります: [複数のX軸構成](https://plot.ly/javascript/multiple-axes/).

### 2.5 Math LaTeX 数式

タイトル、軸、系列は複雑な数式を含むことができます。

![数式：](attachments/pages/charts/math-formula.png)

```
$\sqrt{(n_\text{c}(t|{T_\text{early}}))}$
```

テーマのindex.htmlに以下を追加します。

``` javascript
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_SVG"></script>
```

LatTex構文の詳細はこちらをご覧ください: https://en.wikibooks.org/wiki/LaTeX/Mathematics.

### 2.6 タイトル

タイトルはチャートの上に表示されます。 次のように設定できます:

``` json
{
  "title": "CHART TITLE",
  "titlef": {
    "family": "Droid Sans, Droid Serif, sans-serif",
    "size": 20,
    "color": "black"
  }
}
```

![タイトルの構成](attachments/pages/charts/title.gif)

他のオプションはこちらでご覧いただけます: [タイトル設定](https://plot.ly/javascript/reference/#layout-title).

### 2.7 色

グラフの背景色を設定します。

``` json
{
  "paper_bgcolor": "#FFF"
}
```

### 2.8 証拠金

グラフの周りにスペースを作成します。

``` json
{
  "margin": {
    "l": 70,
    "r": 60,
    "b": 60,
    "t": 60,
    "pad": 10,
    "autoexpand": true
  }
}
```

![ マージン構成 ](attachments/pages/charts/margin.gif)

オプションの詳細はこちら: [マージン設定](https://plot.ly/javascript/reference/#layout-margin).

### 2.9 ツールチップ

グラフデータポイントの上にマウスポインタを移動すると、小さなポップアップボックスが表示されます。

``` json
{
  "hovermode": "text",
  "hovertext": "text",
  "hoverinfo": "all",
  "textposition": "inside",
  "hoverlabel": {
    "bgcolor": "#888",
    "bordercolor": "#888",
    "font": {
      "color": "white"
    }
  }
}
```

![ツールチップの設定](attachments/pages/charts/tooltip.gif).

オプションの詳細はこちら: [ツールチップ設定](https://plot.ly/javascript/reference/#layout-hovermode).

### 2.10 フォント

すべてのチャート要素に適用されるルートレベルにグローバルフォントを設定します。 または、特定の要素のフォントを設定します。

``` json
{
  "font": {
    "family": "Open Sans,verdana, arial, sans-serif",
    "size": 12,
    "color": "black"
  },
  "legend": {
    "font": {}
  },
  "titlefont": {},
  "hoverlabel": {
    "font": {}
  },
  "xaxis": {
    "titlefont": {},
    "tickfont": {}
  },
  "yaxis": {
    "titlefont": {},
    "tickfont": {}
  }
}
```

### 2.11 範囲モード

指定した軸の表示範囲を設定します。

**普通:**

プロットされた値に基づいて範囲を設定します。

```json
{
  "yaxis": {
    "rangemode": "normal"
  }
}
```
![範囲モード](attachments/pages/charts/normal.gif)

**否定的ではない:**

正の値のみを表示し、範囲はプロットされた正の値に基づいています。

```json
{
  "yaxis": {
    "rangemode": "nonnegative"
  }
}
```

![範囲モード](attachments/pages/charts/nonnegative.gif)

**tozero:**

これはチャートのデフォルトの範囲モードです。 軸の正と負の両方の範囲は、ゼロマークから始まります。

```json
{
  "yaxis": {
    "rangemode": "tozero"
  }
}
```

![範囲モード](attachments/pages/charts/tozero.gif)

{{% alert type="info" %}}
When **fill** for the series is set to something other than *none*, the Y-axis range is forced to start from zero (*tozero*). 例:

**レイアウト**

```json
{
  "yaxis": {
    "rangemode": "normal"
  }
}
```

**データ**

```json
{
  "fill": "tonexty"
}
```
{{% /alert %}}

![範囲モード](attachments/pages/charts/rangemode-note.gif)

その他のオプションはこちらでご覧いただけます: [レンジモード設定](https://plot.ly/javascript/reference/#layout-yaxis-rangemode).

## 3 データ/シリーズプロパティ {#data-series}

これらのプロパティは、特定の種類のグラフにのみ適用されます。 チャートごとに、データプロパティが異なります。 彼らは、チャートがあるはずのように見えるようにします。

### 3.1 行

モードと行の設定は、シリーズの **Advanced** 設定で追加できます。

![Line styles](attachments/pages/charts/line-styles.png)

``` json
[
  {
    "mode": "markers"
  },
  {
    "mode": "lines+markers"
  },
  {
    "mode": "lines"
  },
  {
    "mode": "lines",
    "line": {
      "dash": "dashdot"
    }
  },
  {
    "mode": "lines",
    "line": {
      "dash": "dot"
    }
  },
  {
    "mode": "lines",
    "line": {
      "dash": "longdash"
    }
  },
  {
    "mode": "lines",
    "line": {
      "width": 5
    }
  }
]
```

### 3.2 複合グラフの種類

系列の種類を変更できます。 たとえば、棒グラフの系列を行列にすることができます。

![グラフのデータのプロパティ](attachments/pages/charts/combine-list-bar.gif)

### 3.3 円グラフ

円形のグラフをスライスに分割して数字の割合を示します。

``` json
{
  "hole": 0.9
}
```

![円グラフデータのプロパティ](attachments/pages/charts/pie-chart.png)

その他のオプションはこちらでご覧いただけます: [円グラフデータプロパティ](https://plot.ly/javascript/reference/#pie).

### 3.4 塗りつぶし

線の下の色で塗りつぶされた線グラフを表示します。

``` json
{
  "line": {
    "color": "#17202A",
    "shape": "linear",
    "dash": "dot"
  },
  "type": "scatter",
  "fill": "tonexty",
  "fillcolor": "#B2BABB"
}
```

![エリアチャートデータのプロパティ](attachments/pages/charts/area-chart.png)

その他のオプションはこちらでご覧いただけます: [エリアチャートデータプロパティ](https://plot.ly/javascript/reference/#area).

### 3.5 時系列数

以下の例は、時間ごとにチャートをフィルタするためのフィルタボタンを設定する方法を示しています。

![折れ線グラフのデータ プロパティ](attachments/pages/charts/time-series-filters.png).

``` json
{
  "xaxis": {
    "rangeslider": {
      "visible": true
    },
    "rangeselector": {
      "buttons": [
        {
          "step": "all",
          "label": "reset"
        },
        {
          "step": "year",
          "stepmode": "backward",
          "count": 1,
          "label": "1 YEAR"
        },
        {
          "step": "year",
          "stepmode": "backward",
          "count": 5,
          "label": "5 YEARS"
        },
        {
          "step": "year",
          "stepmode": "backward",
          "count": 10,
          "label": "10 YEARS"
        },
        {
          "step": "year",
          "stepmode": "todate",
          "count": 1,
          "label": "YTD"
        }
      ]
    }
  }
}
```

詳細はこちらをご覧ください: [範囲選択](https://plot.ly/javascript/reference/#layout-xaxis-rangeselector).

### 3.6 複数の Y 軸データプロパティ {#multiple-y-axes-data-properties}

データセットの範囲に応じて、異なるスケールを持つ 2 つの異なるY軸を表示します。

``` json
[
  {
    "name": "yaxis2 data",
    "yaxis": "y2",
    "type": "scatter"
  },
  {
    "name": "yaxis data",
    "type": "scatter"
  }
]
```

![複数の Y 軸のプロパティ](attachments/pages/charts/data-multiple-y.png)

### 3.7 複数の X 軸データプロパティ {#multiple-x-axes-data-properties}

異なるX軸を異なるスケールで表示します。

``` json
[
  {
    "name": "xaxis data",
    "xaxis": "x",
    "type": "scatter"
  },
  {
    "name": "xaxis2 data",
    "xaxis": "x2",
    "type": "scatter"
  }
]
```

![複数の X 軸のプロパティ](attachments/pages/charts/data-multiple-x.png).

## 4 構成オプション (すべてのグラフ) {#config-options}

以下の設定オプションはすべてのチャートで使用できます。

```json
{
  "displayModeBar": true,
  "displaylogo": false,
  "modeBarButtonsToRemove": [ "sendDataToCloud", "lasso2d", "select2d", "hoverClosestCartesian", "hoverCompareCartesian", "toggleSpikelines" ],
  "locale": "nl",
  "locales": {
    "nl": {
      "dictionary": {
        "Download plot as a png": "Opslaan als PNG"  
      }
    }
  }
 }
```
