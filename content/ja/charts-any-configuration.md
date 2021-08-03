---
title: "任意のグラフのウィジェット"
parent: "chart-widgets"
description: "プロットに正しい値を渡すための[Any Chart (任意のチャート)]ウィジェットの構成の参照。 これにより、さまざまなグラフを描くことができます"
menu_order: 30
tags:
  - "任意のグラフ"
  - "オプション"
  - "設定"
  - "グラフ"
  - "studio pro"
---

## 1つの紹介

**任意のチャート**を使用すると、Plolyでサポートされている任意のチャート タイプを作成できます。 sはマーケットプレイスのウィジェットの説明に記載されているバージョンまでです。 ですから、標準チャートウィジェットとして利用できないチャートを作成したい場合は、 例えば、3Dグラフ、任意のグラフはあなたの友人です。

このチャートタイプの構成は複雑です。 ヘルプについては、Mendix Marketplace の **任意のチャート** モジュールで配信されている [Building blocks](/appstore/modules/any-chart) を参照してください。 別の方法として、 [任意のチャート](/howto/front-end/charts-any-usage) または [任意のチャート シート](charts-any-cheat-sheet) を使用して、クイックスタートを行います。

チャートは JSON **Data** 配列と **Layout** オブジェクトで構成されます。 構成は、 **Source 属性** および **Sample data** プロパティを使用して静的に設定できます。

動的またはデータベースから取得できるレイアウトJSON。 は静的設定にマージされ、共通のプロパティが上書きされます。

サンプルデータはデモ用です。 format@@0属性が選択されていない場合や、Studio Proのプレビューでチャートをレンダリングする場合は、実行時に表示されます。

## 任意のグラフウィジェットの場所2

任意のチャートウィジェットは、 **データ ビュー** のコンテキストに配置する必要があります。 データ ビューには、 **ソース 属性** (無制限長文字列) を持つエンティティオブジェクトが含まれています。このオブジェクトには、プロットするデータの JSON 表現が含まれています。 基本チャートウィジェットとは異なり、[Any Chart (任意のチャート)] ウィジェットはドメインモデルのデータに対して直接動作しません。 プロットしたいデータを任意のチャートのJSON形式に変換する必要があります。 これを行う方法については、 [任意のチャートの使い方](/howto/front-end/charts-any-usage) を参照してください。

## 3つのデータ

プロットされるデータは配列で記述されます。 この配列の要素は、選択したグラフの種類にプロットする点です (散布図または棒図)。 例えば) [完全な参照](https://plot.ly/javascript/reference) に記載されているように。

### 3.1 Static

JSON配列（https://plot.ly/javascript/reference/に基づき、チャートの説明の *静的* 部分を含む）。 これらは、グラフのデフォルトの説明です。たとえば、プロットしたいグラフの種類などです。

### 3.2 ソース属性

これは、 **任意のチャート** ウィジェットが配置されているデータビューのコンテキストを形成するエンティティの属性である無制限の文字列属性です。

In the image below, the **Source attribute** is the *data* attribute of the *ChartContext* entity which is the data view context in which the Any Chart widget is placed.

![](attachments/charts/any-chart-page-placement.png)

**Source 属性** には、 **Static** データをマージして上書きする JSON 構造が含まれています。 通常、これにはプロットするデータが含まれていますが、グラフの種類など他の静的要素を上書きすることもできます。 棒グラフの線の色、または棒グラフの棒の方向。

### 3.3 サンプルデータ

グラフをプレビューするためのデータ。 **ソース 属性** が選択されていない場合、Studio Pro の **静的データ** または実行時にマージされます。

### 3.4 モード

**開発** モードでは、アプリの実行時にチャートにボタンが追加されます。 このボタンは、詳細設定オプションをテストするためのライブエディタを切り替えるために使用されます。

**Production** モードでは、ユーザーがチャートを設計したとおりに表示するためにこのボタンが削除されます。

## 4つのレイアウトオプション

プロットのレイアウト – タイトル、注釈などの非データ関連の視覚的属性。 – [完全な参照](https://plot.ly/javascript/reference/#layout) に記載されている JSON オブジェクトで説明されています。

### 4.1 Static

https://plot.ly/javascript/reference/ に基づいてチャートのデフォルトのレイアウトを記述する JSON オブジェクト。

### 4.2 ソース属性

これは、 **チャート** ウィジェットが配置されているデータビューのコンテキストを形成するエンティティの unlimited length string 属性です。 これには、 **Static** レイアウトとマージして上書きする JSON 構造が含まれています。 これにより、アプリ内からレイアウト情報を動的に変更できます。

### 4.3 サンプルレイアウト

プレビュー用のレイアウトオプション。 *ソース 属性* が選択されていない場合は、Studio Pro の *静的なレイアウト* とマージされます。

## 5つの設定オプション

スクロール/ズーム/ホバー動作など、プロットのプロット高レベルの設定オプションを含むJSON。 これらの高レベルの設定オプションについては、こちらをご覧ください: https://plot.ly/javascript/configuration-options.

**config** と **layout** の違いは、レイアウトがプロットの内容に関連することです。 一方、設定はプロットが表示されているコンテキストに関連しています。 **チャート** ウィジェットでは、アプリ内で設定オプションを動的に変更することはできません。

## 6つの外観

外観設定は、チャートの寸法を設定するために使用されます。

### 6.1 幅単位

**幅** プロパティに使用される単位のタイプ: *パーセント* または *ピクセル*。

### 6.2 Width

**幅 単位** 設定に基づいて、グラフの幅をピクセルまたはパーセンテージで指定します。

### 6.3 高さ単位

**Percentage of width** allows you to change the aspect ratio, **Pixels** is an absolute measure, and **Percentage of parent** allows you to set the height in relation to the parent container.

{{% alert type="warning" %}}
警告：親コンテナの **パーセント** を使用する場合、親コンテナの高さは絶対でなければなりません。そうでなければ何も表示されません。
{{% /alert %}}

### 高さ6.4

**高さ単位**の設定に基づいて、ピクセル単位またはパーセンテージでの高さ。

## 7つのイベント

**任意のチャート** ウィジェットは、チャート上にプロットされた点に関連する2種類のイベントをサポートしています。

* **ホバー**: *Tooltip* 要求として解決する
* **click**: *On click* event

{{% alert type="info" %}}
イベントは、グラフ上にカーソルを合わせるか、グラフ上にプロットされた点をクリックすることでトリガーされます。 チャートの他の部分でのクリックはイベントをトリガーしません。
{{% /alert %}}

{{% alert type="info" %}}
ホバーイベントがトリガーされないようにすると、クリックイベントがトリガーされなくなります。 これには、レイアウトパラメータ `ホバーモード` を `false` に設定し、データパラメータ `ホバー情報` を `スキップ` に設定することが含まれます。
{{% /alert %}}

イベントが発生すると、plotly はここで説明されている JSON オブジェクトを返します: https://plot.ly/javascript/plotlyjs-events/#event-data この JSON データは、 **任意のデータ** に渡されるエンティティオブジェクトの文字列属性に格納されます。 JSON には、点の x 座標や y 座標などのグラフから生データが含まれています。 イベントによって引き起こされるマイクロフローで解釈される必要があります

### 7.1 イベントエンティティ

plotlyからのイベントデータの受信に使用されるエンティティ。 イベントデータを保持する文字列属性を含める必要があります。

### 7.2 イベントデータ属性

chart イベントの JSON データが格納される文字列属性。

### 7.3 クリック時のマイクロフロー

チャート上のデータポイントがクリックされたときに実行されるマイクロフロー。 これは **イベント エンティティ** をコンテキストとして持ちます。

### 7.4 クリック時 Nanoflow

チャート上のデータポイントがクリックされたときに実行されるナノフロー。 これはコンテキストとして **イベントエンティティ** を持ちます

### 7.5 ツールチップフォームエンティティ

When a **Tooltip microflow** is triggered by a plotly hover event, it needs to return an entity object which forms the context of the **Tooltip form**.

ツールチップマイクロフローによって返されるエンティティは、ここで識別されます。 **Tooltip microflow** のコンテキストである **イベントエンティティ** である必要はありません。 開発者は、Tooltipフォームによって表示されるデータと、ホバーイベントによって提供される **イベントエンティティ** の情報に基づいて、エンティティの属性と関連付けを決定し、追加することができます。

### 7.6 Tooltip Microflow

ここで同定されたマイクロフローは、プロットから受信したオンホバーイベントによって呼び出されます。 JSON イベントデータを含む **Event data 属性** を使用して、タイプ **Event data 属性** のイベントオブジェクトを受け取ります。 データは解釈され、 **Tooltipフォームエンティティ** 型のオブジェクトが返されます。 これは **Tooltip form** のコンテキストを形成します。

### 7.7 ツールチップフォーム

ユーザーがグラフのプロットポイントにカーソルを合わせたときに表示するフォーム。 コンテキスト **ツールチップエンティティ** があります。 グラフ上にプロットされた点の上にマウスがある間、フォームが表示されます。 プロットされた点の上にマウスがない場合、自動的に閉じます。

## 8 チャートテーマ

高度な JSON 設定は、Mendix アプリの root ディレクトリのテーマフォルダーを介してグローバルコンテキストに追加することもできます。

To the theme folder, add a *.json* file named *com.mendix.charts*. JSON は以下の形式である必要があります:

``` json
{
  "layout": {
    // Add shared layout options here (for all charts)
  },
  "configuration": {
    // Add shared configuration options here (for all charts)
  },
  "charts": {
    "LineChart": {
      "layout": {
        // Add line chart only layout options here
      },
      "data": {
        // Add line chart only data options here
      },
      "configuration": {
          // Add line chart only configuration options here
      }
    },
    "AreaChart": {
      // Same arrangement as the line chart
    },
    "BubbleChart": {
      // Same arrangement as the line chart
    },
    "TimeSeries": {
      // Same arrangement as the line chart
    },
    "ColumnChart": {
      // Same arrangement as the line chart
    },
    "BarChart": {
      // Same arrangement as the line chart
    },
    "PieChart": {
      // Same arrangement as the line chart
    },
    "HeatMap": {
      // Same arrangement as the line chart
    }
  }
}
```

チャートのテーマを設定する方法についてのガイダンス: [チャートのテーマを使用する方法](/howto/front-end/charts-theme).

{{% alert type="info" %}}

ここで設定する設定は、アプリケーション内のすべてのチャートに適用されるため、注意して使用してください。 ウィジェット自体で設定された高度な設定のみが優先されます。

{{% /alert %}}
