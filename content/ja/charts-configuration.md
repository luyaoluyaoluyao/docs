---
title: "グラフの構成"
parent: "chart-widgets"
menu_order: 10
tags:
  - "グラフ"
  - "ウィジェット"
  - "Studio Pro"
  - "グラフの構成"
  - "設定"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/charts-configuration.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

このガイドでは、チャート ウィジェットの設定オプションについて説明します。 グラフウィジェットは、Atlas UIに基づいたMendixアプリテンプレートに含まれています。 [Mendix Marketplace](https://marketplace.mendix.com/link/component/105695/) からダウンロードすることで、他のMendix アプリに含めることができます。 詳細については、 [マーケットプレイスガイド](/appstore/widgets/charts) の *チャート* を参照してください。

このガイドでは、次のウィジェットについて説明します。

* 面積グラフ
* 棒グラフ
* バブルチャート
* 縦棒グラフ
* ヒートマップ
* 折れ線グラフ
* 円グラフ
* Time series
  * 一部のアプリには2つの *時系列* ウィジェットがあることに注意してください。 このドキュメントはこのアイコンを持つものを参照しています： ![正しい時系列ウィジェットの画像](attachments/charts/time-series-icon.png)

*任意のチャート* ウィジェットの構成は、別のドキュメントにあります: [任意のチャート ウィジェット](charts-any-configuration).

## 2つの一般的な構成

すべてのチャートの一般的な構成については、ここで説明します。 チャート固有の構成については、 [チャートタイプ別の構成](#configuration-by-chart-type)を参照してください。

### 2.1 グラフのプロパティ

![一般的なグラフのプロパティダイアログ](attachments/charts/line-chart-chart-properties.png)

#### 2.1.1 シリーズ

系列を追加し、そのプロパティを設定すると、各系列はデータセットを表します。 たとえば、折れ線グラフ上の線です。

* *円グラフ* と *ヒートマップ* は、単一のデータセットを含む単一のシリーズのみをサポートします

  この場合、 **データ ソース** と **データ ポイント** はウィジェットに別々のタブとして表示されます。

  ![データソースとデータポイントのタブを表示する円グラフダイアログ](attachments/charts/widget-data-source.png)

  フィールドは [Data source](#data-source) と [Data points](#data-points)のセクションで説明されているものと同じです。

* 複数のデータ系列をサポートするチャート (たとえば、複数の線を持つ折れ線グラフなど) は、複数のデータ系列をサポートしています。

  In this case, new series can be added by clicking the **Series > New** button in the **Chart properties** tab.

  {{% alert type="info" %}}バージョン1.4のチャートから、可変数のデータ系列のチャートを作成できます。 これを行う方法については、 [動的な系列チャートを作成する方法](/howto8/front-end/charts-dynamic-series).{{% /alert %}} を参照してください。

1. データソース<a name="data-source"></a>

    各シリーズのデータは、異なるデータソースから取得できます。 追加のデータ系列は **チャート プロパティ** タブに追加できます。

    ![系列データソースタブの編集](attachments/charts/series-item-data-source.png)

    * **Static/Dynamic**: 決まったデータ系列があるかどうかを選択します(行)。 例えば、データ系列の数が変数であるか、アプリによって決定されます。

    * **エンティティ**: データ値が取得されるエンティティ。

    * **Data source**: 系列のデータソースタイプ: *Database*, *Microflow* または *REST エンドポイント*

    * **REST URL**: REST エンドポイントへの相対または完全な URL 。 REST エンドポイントの設定の詳細については、 [REST Charts](/howto8/front-end/charts-basic-rest) を参照してください。

    * **XPath constraint**: (データソースが Databaseの場合に使用される) エンティティからのデータに関する制約。

    * **Microflow**: データ値を持つリストオブジェクトを返すマイクロフロー

2. データ ポイント<a name="data-points"></a>

    プロットされる値に使用されるデータソース内の属性。

    ![系列データポイントタブを編集](attachments/charts/series-item-data-points.png)

    * **X軸データ 属性**: データソースの場合、参照上のデータベース属性は最大1階層でサポートされている。 データ ソースのマイクロフローでは、参照はサポートされていません

    * **Y軸データ 属性**: データソースの場合、参照上のデータベース属性は最大1レベルの深さでサポートされています。 データソースのマイクロフロー参照はサポートされていません

    * **X軸のソート属性**: データソースについて、参照上のデータベース属性は最大1階層でサポートされている。 データソースのマイクロフロー参照はサポートされていません

    * **ソート順序**: "X軸のソート属性" によって提供されるデータのソート順序

    * **aggregation type**: この系列に 1 x 値の 2 つの値がある場合(例えば、1 つの系列に 2 つのデータポイントがある場合): (2, )、および (2,4)) - ほとんどのオプションは自明で、例は次のとおりです。
      * 合計: 2 つの値の合計 – (2,7) をプロットします。
      * 平均: 2つの値の平均をプロットします (2,3.5)
      * なし：最初のデータポイントだけをプロットする (2,3)

3. 外観

    シリーズの外観。 これはチャートの種類ごとにカスタマイズされています。以下を参照してください: [チャートタイプごとの3つの構成](#configuration-by-chart-type)。

    ![系列の外観タブを編集](attachments/charts/series-item-appearance.png)

4. 静的なシリーズ

    静的な系列である場合、シリーズの外観のための追加の構成。 これはチャートの種類ごとにカスタマイズされています。以下を参照してください: [チャートタイプごとの3つの構成](#configuration-by-chart-type)。

    ![データ系列の静的系列タブ](attachments/charts/series-item-static.png)

5. 動的なシリーズ

    動的な系列である場合の設定。

    ![データ系列動的系列タブ](attachments/charts/series-item-dynamic.png)

    * **系列エンティティ**: 系列を定義するエンティティ - このエンティティタイプのオブジェクトのリストが系列を構築するために使用されます。 それぞれの物体に対して1つの系列があります

      各エンティティは、プロットされる値に関連付けられています。詳細については、 [動的直列チャートの作成方法](/howto8/front-end/charts-dynamic-series) を参照してください。

    * **シリーズ名属性**: 凡例が表示された場合、シリーズ名として表示されるシリーズエンティティの属性

    * **カラー属性**: このシリーズを表示するときに使用されるHTMLカラーを定義する系列エンティティの属性 – *異なる値を許可している場合、複数の色属性が存在する可能性があります (例えば、エリアチャートには別の線と塗りつぶしの色が含まれている場合)

    * **Series sort attribute**: allows you to sort the series by an attribute of the series entity – *this is not supported for **non-persistable** entities, such as those used when defining a REST datasource*

    * **シリーズソート順序**: *昇順* または *降順*

6. イベント

    ユーザーがチャートとやり取りする場合にサポートされるイベント。

    ![系列イベントタブを編集](attachments/charts/series-item-events.png)

    {{% alert type="info" %}}ページのコンテキスト、microflow。 または、イベントやツールチップに選択されたナノフローは、グラフ上の点が描画されたプロットオブジェクトになります。 This means you can display or use the x and y values, _and_ any other values stored in that object.<br /><br />For example you could use the tooltip to display the precise y value of a point, plus information on when the data was collected{{% /alert %}}

    * **クリック**: データポイントのクリック処理方法を選択します。
      * 何もしない
      * ページを表示
      * マイクロフローを呼び出す
      * ナノフローを呼び出します。

        対応する設定を構成します。

      * **クリックページ**: クリック時に開くページ。 必須 **クリック時 > ページを表示する** オプションが選択されています

      * **Open page as**: Full page, Popup or Blocking popup

      * **クリックマイクロフロー**: クリック時に実行されるマイクロフロー

      * **クリック時 nanoflow**: クリック時に実行される nanoflow

    *     **ツールチップ形式**: グラフのプロットポイントにユーザーがカーソルを合わせたときに表示するページ

7. 高度な設定 <a name="advanced"></a>

    ![シリーズの詳細タブを編集](attachments/charts/series-item-advanced.png)

    * **Options**: The Plotly *series options* in JSON format; these options will only be used when the *widget* tab **Advanced > Mode** is set to *Advanced* or *Developer*: see [Advanced](#advanced-mode), below.

#### 2.1.2 外観

**外観** の設定は、ページ上のグラフのサイズを設定するために使用されます。

![一般的なグラフの外観タブ](attachments/charts/widget-appearance.png)

* **Width unit**: **Width** プロパティ - *Percentage* または *Pixels* に使用される単位のタイプ。

* **Width**: **Width unit** の設定に基づいて、グラフの幅をピクセルまたはパーセンテージで示す。

* **高さ単位**: **高さ** プロパティで使用される単位の種類

  * **幅の割合**: アスペクト比を設定
  * **Pixel**: 絶対的な高さ
  * **親の割合**: ウィジェットが配置されているコンテナに関連する高さを設定します

  {{% alert type="warning" %}} **親コンテナの割合** 親コンテナの高さは **絶対** でなければなりません。そうでなければ何も表示されません。{{% /alert %}}

* **高さ**: **高さ単位** の設定に基づく高さまたはパーセンテージ。

#### 2.1.3 REST

REST リクエストにパラメータを追加します( [Data source](#data-source) を参照)。 contextId、および系列名はデフォルトで指定されます。

![汎用チャート RESTタブ](attachments/charts/widget-rest.png)

#### 2.1.4 Advanced {#advanced-mode}

チャートは、JSONを使用してチャートを設定する一般的なフレームワークのplotly.jsに基づいています。 上級モードおよび開発モードでは、追加の JSON を指定できます:plotly.js の多くの機能のロックを解除します。 ライブプレビューでこれを行うこともできます。

plotly.js とオプションの詳細については、次のリンクを参照してください: https://plot.ly/javascript/ 。

![一般的なグラフの詳細タブ](attachments/charts/widget-advanced.png)

* **モード**: 以下の3つのモードでこれらのグラフを使用できます:

  * **Basic**: さまざまなウィジェットオプションでグラフをすばやくセットアップする
  * **Advanced**: 追加の JSON 設定を指定する
  * **開発者**: 実行時にチャートに **エディター** ボタンを追加します。これはエディターを切り替えて異なる高度な設定オプションでプレイするように切り替えます

    ![](attachments/charts/toggle-editor.png)

* **レイアウトオプション**: Plottly レイアウトオプションを含む JSON
  * [サンプル](charts-advanced-cheat-sheet#layout-all)
  * [完全な参照](https://plot.ly/javascript/reference/#layout)

* **設定オプション**: Plotty 設定オプションを含む JSON
  * [サンプル](charts-advanced-cheat-sheet#config-options)
  * [ドキュメント](https://plot.ly/javascript/configuration-options/)
  * [完全な参照](https://github.com/plotly/plotly.js/blob/master/src/plot_api/plot_config.js)

#### 2.1.5 Common

これらは多くのウィジェットに共通するプロパティです。 詳細については、 [ページエディターの](common-widget-properties#common-properties) プロパティ共通を参照してください。

## グラフの種類による3つの構成 {#configuration-by-chart-type}

上記のプロパティはグラフタイプで共通です。 このセクションでは、説明されているプロパティはチャート タイプに固有です。

### 3.1 列グラフ

**シリーズの新規または編集**

1. **静的系列** タブ

    * **シリーズ名**: グラフ上の任意の凡例に表示されます

    * **Column color**: 列のHTML色 (例: 緑, #00FF00, rgb(0,255,0), rgba(0,255,0, 0.5)

### 3.2 折れ線

**シリーズの新規または編集**

1. **外観** タブ

    * **ラインモード**: *ライン* (データポイントがあるマーカーを表示せず) または *マーカー付きライン*

    * **ライン スタイル**: *直線* または *曲線線 (スプライン)*

2. **静的系列** タブ

    * **シリーズ名**: グラフ上の任意の凡例に表示されます

    * **ラインカラー**: 例えば、緑色、#00FF00、rgb(0,255,0), rgba(0,255,0, 0.5)

### 3.3 円グラフ

**グラフのプロパティ**

* **グラフの種類**: 使用する円グラフの種類 *円* または *ドーナツ*

* **凡例を表示**: 円グラフに凡例を表示する

* **色**: 緑色、#00FF00、rgb(0,255,0), rgba(0,255,0, 0.5)

* **Refresh interval (ms)**: 0に設定した場合、チャートをミリ秒単位でリフレッシュする

### 3.4 エリアチャート

**シリーズの新規または編集**

1. **データソース** タブ

    * **シリーズ名**: グラフ上の任意の凡例に表示されます

2. **外観** タブ

    * **外枠**: いいえ、マーカー付きでははい

    * **境界スタイル**: 直線, 曲線

3. **静的系列** タブ

    * **境界色**: 境界線のHTML色 (例, 緑, #00FF00, rgb(0,255,0), rgba(0,255,0, 0.5)

    * **領域の色**: 境界内の領域のHTML色、例えば、緑、#00FF00、rgb(0,255,0)、rgba(0,255,0, 0.5)。 既定値は透明度を持つ境界線の色です

### 3.5 棒グラフ

**シリーズの新規または編集**

1. **静的系列** タブ

    * **シリーズ名**: グラフ上の任意の凡例に表示されます

    * **バーの色**: 例えば、緑色、#00FF00、rgb(0,255,0), rgba(0,255,0, 0.5)

### 3.6 時系列チャート

**シリーズの新規または編集**

1. **外観** タブ

    * **外枠**: いいえ、マーカー付きでははい

    * **境界スタイル**: 直線, 曲線

    * **領域の塗りつぶし**: データポイントとX軸の間の塗りつぶし: はい、いいえ

2. **静的系列** タブ

    * **シリーズ名**: グラフ上の任意の凡例に表示されます

    * **ラインカラー**: 例えば、緑色、#00FF00、rgb(0,255,0), rgba(0,255,0, 0.5)

    * **領域の色**: 境界内の領域のHTML色、例えば、緑、#00FF00、rgb(0,255,0)、rgba(0,255,0, 0.5)。 デフォルトは透明度のある線の色です

### 3.7 ヒートマップ

**拡大縮小**

* **色**: 関連する色とともに、各色を適用する割合。 少なくとも2つの値を指定する必要があります。指定しない場合は、デフォルトの色が使用されます

* **スケールの表示**: グラフにスケールを表示: はい , いいえ

* **値を表示する**: グラフにデータ値を表示する: はい , いいえ

* **フォント値の色**: ヒートマップ上に表示される値のHTML色 (緑, #00FF00, rgb(0,255,0), rgba(0,255,0, 0.5)

* **X軸ラベル**: X軸に表示するラベル

* **Y軸ラベル**: Y軸に表示するラベル

* **滑らかな色**: データポイント間の徐々な色勾配: はい, いいえ

### 3.8 バブルチャート

**シリーズの新規または編集**

1. **静的系列** タブ

    * **シリーズ名**: グラフ上の任意の凡例に表示されます

    * **セリエ色**[sic]: バブルの緑色,#00FF00,rgb(2,255,0)

## 4チャートテーマ

高度な JSON 設定は、Mendix プロジェクトのルートディレクトリのテーマフォルダを介してグローバルコンテキストに追加することもできます。

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

{{% alert type="info" %}}

ここで設定する設定は、アプリケーション内のチャートのすべてのインスタンスに適用されるため、注意して使用してください。  
ウィジェット自体に設定された高度な設定のみが優先されます。

{{% /alert %}}
