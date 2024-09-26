---
title: "グラフのウィジェット"
parent: "ページ"
menu_order: 70
tags:
  - "グラフ"
  - "任意のグラフ"
  - "Studio Pro"
  - "ページ"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/chart-widgets.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

format@@0ウィジェットを使用すると、幅広いグラフでアプリのページにデータ系列を視覚的に表示できます。

[基本チャート](#basic-charts) は、Atlas UIに基づいたMendixアプリテンプレートに含まれています。 Mendix Marketplace からダウンロードすることで、他のMendix アプリに含めることができます (詳細については、 [チャート](/appstore/widgets/charts) を参照してください)。 基本チャートは、plotly.jsのバージョン1.47.4に基づいています。

[任意のチャート](#any-chart) は、 [plotly.js](https://plot.ly/) の機能をより柔軟に使用することができます。 [任意のチャート](/appstore/modules/any-chart) ウィジェットをアプリに含めることができます。 plotly.js がサポートしているバージョンについては、ウィジェットのドキュメントを参照してください。

## 2つの基本チャート {#basic-charts}

Mendix Chartsを使用すると、すばやく美しいチャートを作成できます。 次のグラフが含まれています:

* **エリア** チャート – X-axis {{% image_container width="200" %}}![Sample Area Chart](attachments/charts/sample-area-chart.png){{% /image_container %}}
* **Bar** chart – 水平棒, grouped or stacked {{% image_container width="200" %}}![Sample Bar Chart](attachments/charts/sample-bar-chart.png){{% /image_container %}}
* **Bubble** chart – グラフにサイズ寸法を追加 {{% image_container width="200" %}}![Sample Bubble Chart](attachments/charts/sample-bubble-chart.png){{% /image_container %}}
* **列** チャート – 垂直バー, grouped or stacked {{% image_container width="200" %}}![Sample Column Chart](attachments/charts/sample-column-chart.png){{% /image_container %}}
* **Heat map** – 2D matrix {{% image_container width="200" %}}![Sample Heat Map](attachments/charts/sample-heat-map.png){{% /image_container %}}
* **折れ線** グラフ – マーカーの有無にかかわらず直線または曲線。{{% image_container width="200" %}}![Sample Line Chart](attachments/charts/sample-line-chart.png){{% /image_container %}}
* **Pie** chart – a 円またはドーナツチャート {{% image_container width="200" %}}![Sample Pie Chart](attachments/charts/sample-pie-chart.png){{% /image_container %}}
* **Time series** – 時間の順序でデータを表示する {{% image_container width="200" %}}![Sample Time Series](attachments/charts/sample-time-series.png){{% /image_container %}}

ウィジェットにはいくつかの設定が含まれており、Studio Proで外観や雰囲気をカスタマイズしたり、クリックイベントやカスタムツールチップのサポートを提供することができます。 Mendix チャートの設定方法については、 [チャート構成](charts-configuration) を参照してください。

標準的なチャート設定があなたの目的に十分でない場合。 基本チャートの詳細設定については、 [チャート詳細チートシート](charts-advanced-cheat-sheet) を参照してください。

Plotly.jsのバージョン1.47.4までの機能のみが、チャートの設定時に使用できます。

**動的な系列チャート**

ベーシックチャートのバージョン1.4から、可変数のデータ系列でチャートを作成できます。 これを行う方法については、 [動的系列チャートの作成方法](/howto8/front-end/charts-dynamic-series) を参照してください。

## 3 任意のチャート {#any-chart}

*任意のチャート* を使用すると、Plolyで可能なすべてのチャートタイプを構築できます。 sは、ウィジェットでサポートされているバージョンまでです(詳細については、マーケットプレイスのウィジェットの説明を参照してください)。 基本チャートでは利用できないチャートを作成したい場合は、 *任意のチャート* が友達です。

{{% image_container width="400" %}}![Sample Contour Chart made with Any Chart](attachments/charts/contour.png){{% /image_container %}}

プロットチャートはJSONに基づいた構成が必要なので、 *任意のチャート* はJSONを入力パラメータとして持っています。 JSON 構造ドキュメントを使用してマイクロフロー内でこの JSON を動的に作成し、これを *チャート* 構成で使用できます。 動的な JSON と組み合わせた静的な JSON 構成を定義することもできます。

このモジュールには、インスピレーションと出発点として、いくつかの [構成要素](charts-any-building-blocks) が含まれています。 新しいグラフを作成したい場合は、plotly.js Webサイトを確認することをお勧めします。

See [Any Chart Widgets](charts-any-configuration) to learn how to configure *Any charts* widgets.

[任意のチャート シート](charts-any-cheat-sheet) には、最も一般的なチャート タイプと、任意のチャートでそれらを作成するために必要な JSON がリストされています。

## 4 基本機能の実行

{{% snippet file="refguide8/performing-basic-functions-widgets.md" %}}

## このセクション内の5つのドキュメント

以下のドキュメントでは、チャートの使い方を詳しく説明しています。

* [グラフの構成](charts-configuration)
* [チャート詳細チートシート](charts-advanced-cheat-sheet)
* [任意のグラフのウィジェット](charts-any-configuration)
* [任意のグラフのBuilding Blocks](charts-any-building-blocks)
* [任意のチャートチートシート](charts-any-cheat-sheet)
