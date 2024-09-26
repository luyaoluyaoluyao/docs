---
title: "データの操作"
menu_order: 30
description: "Mendix Studio でデータを扱う方法を説明します。"
tags:
  - "スタジオ"
  - "データ"
  - "データを使って"
  - "データを操作する"
---

## 1つの紹介

Mendix Studioでは、さまざまな方法でデータを扱います。 たとえば、独自のデータを作成し、ページやマイクロフローで使用します。 スプレッドシートからデータをアップロードするアプリを起動したり、組織内の他のアプリのデータを使用したりできます。

Studio でデータを使用すると、以下に分類できます。

* **ご自身のデータの操作** – 作成したデータの操作。
  * **ドメインモデルでのデータの作成と管理** – ドメインモデルは、データを扱うビジュアルエディターです。 ドメインモデルは、アプリケーションドメイン内の情報を抽象的な方法で記述するデータモデルです。 それはあなたのアプリケーションのアーキテクチャの中心です。 ドメインモデルの詳細と操作方法については、 [Domain Model](domain-models) を参照してください。
  * **ご自身のデータ** から始めて、Studio では独自のデータから始めてアプリを構築することもできます。 そのためには、スプレッドシート **アプリの** テンプレートを使用して、Microsoft Excelスプレッドシートをインポートする必要があります。 スプレッドシートからのデータは、エンティティ、属性、関連付けに自動的に変換されます。 スプレッドシート **からの**アプリの詳細については、 [自分のデータで開始](start-with-data) を参照してください。
* **外部データの操作** – 組織がデータハブのライセンスを持っている場合 組織内の他のアプリからの外部データをアプリに接続し、このデータをローカルで使用できます。 詳細については、 [Studio のデータ ハブ](data-hub-in-studio) を参照してください。
* **データの表示と制御** - ページを介してデータを表示し、マイクロフローとページを介して取得および表示するデータを制御することができます。 [microflow](microflows)を使用すると、オブジェクトのオブジェクト/リストを取得できます。 On [pages](page-editor), you can show data using data containers ([data view](page-editor-data-view-list-view#data-view-properties), [list view](page-editor-data-view-list-view#list-view-properties), or [data grid](page-editor-data-grid)) and other widgets on pages. 最後に、 [データ フィルター](data-filters) を使用して、ページとマイクロフローに表示されるデータを制御できます。

## このカテゴリ内の2つのメインドキュメント

* [ドメインモデル](domain-models)
* [あなた自身のデータから開始](start-with-data)
* [Studio のデータハブ](data-hub-in-studio)
* [データフィルタ](data-filters)