---
title: "任意のグラフのBuilding Blocks"
parent: "chart-widgets"
description: "任意のチャートウィジェットの一部として提供されている任意のチャート構築ブロックの参照"
menu_order: 40
tags:
  - "任意のグラフ"
  - "グラフ"
  - "Building Blocks"
  - "ウィジェット"
  - "Studio Pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/charts-any-building-blocks.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

任意のチャートは、ここのMendixマーケットプレイスで利用可能なウィジェットです: [任意のチャート](/appstore/modules/any-chart) モジュール。 任意のチャートモジュールを使用すると、Plolyで可能なすべてのチャートタイプを構築できます。 sはマーケットプレイスのウィジェットの説明に記載されているバージョンまでです。 Plotly.js の詳細はこちら: https://plot.ly/javascript/reference/ .

任意のチャート構成ブロックは、既に定義されているチャートの基本的なプロパティを持つ、事前に構成されたページ構成ブロックです。 他のウィジェットやBuilding Blockと同じ方法でMendixページに配置できます。 グラフを作成するために必要な **データ** と **レイアウト** オブジェクトのサンプルが含まれています。 これらのオブジェクトは、Source 属性が選択されていない場合や、Studio プレビューでサンプルデータをレンダリングする場合に、実行時にデモ目的で使用されます。

## プロパティー

format@@0の構成ブロックには、ウィジェットに不可欠な基本構成が含まれます。 チャートの外観をカスタマイズするには、いくつかの変更を行う必要があります。 以下のプロパティは、アプリに任意のチャート構築ブロックを配置する際に最小限に設定する必要があります。

ウィジェットをダブルクリックして、任意のチャートウィジェットのプロパティを開きます。

### データ
プロットされるデータは、通常はdataと呼ばれる配列で記述されます。その要素は、さまざまな種類のトレースオブジェクトです(例えば、 文書化されている [完全なリファレンス](https://plot.ly/javascript/reference) にある scatter、bar など。

#### Static
https://plot.ly/javascript/reference/ に基づくデータJSON配列。

#### ソース属性
属性データがマージされ、 **静的** データが上書きされます。

#### サンプルデータ
データをプレビューします。 **ソース 属性** が選択されていない場合、Studio 内または実行時に **静的データ** とマージされます。

#### モード
開発モードでは、アプリを実行するときに、チャートにボタンが追加されます。このボタンは、詳細設定オプションのライブエディタを切り替えるために使用されます。

### レイアウトオプション
プロットのレイアウト – タイトルや注釈などの非データ関連の視覚的属性 – は、通常はlayoutと呼ばれるオブジェクトに記述されています。 [完全な参照](https://plot.ly/javascript/reference/#layout) で文書化されています。

#### Static
https://plot.ly/javascript/reference/ ベースの JSON オブジェクト。

#### ソース属性
属性レイアウトは静的レイアウトオプションをマージおよび上書きします。

#### サンプルレイアウト
プレビュー用のレイアウトオプション。 'Source attribute'が選択されていない場合、Studio内または実行時に'Static'とマージされます。

{{% alert type="info" %}}
任意のチャート構成の詳細については、 [任意のチャートウィジェット](charts-any-configuration) を参照してください。
{{% /alert %}}
