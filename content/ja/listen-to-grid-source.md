---
title: "ウィジェットのソースを聞く"
parent: "データソース"
tags:
  - "studio pro"
  - "ウィジェットを再生"
  - "データソース"
menu_order: 70
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/listen-to-grid-source.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

listen-to-widgetデータ ソースは、データ グリッドで選択されているオブジェクトの詳細情報をデータ ビューに表示することができるデータ ビューの特定のソースです。 テンプレートグリッド、または同じページのリストビュー。 これは、大量のデータを表示するときに特に便利で、オブジェクトごとに利用可能な情報が制限されます。 新しいページを開かなくても個々のオブジェクトの詳細を見ることができます。

{{% image_container width="400" %}}![ウィジェットの例を聞く](attachments/data-widgets/listen-to-widget-example.jpg)
{{% /image_container %}}

上の画像のデータビューは、データ グリッドにリッスンします。 この例では、選択されている製品の名前がデータビューに表示されます。

リストビュー、テンプレートグリッド、およびデータグリッドはリストウィジェットであり、聞くことができます。 リストウィジェットでオブジェクトが選択されていない場合、データビューは空のままで反応しません。

## 2つのプロパティ

### 2.1 リストウィジェット

データビューに表示されるオブジェクトを制御するリストウィジェットを指定します。
