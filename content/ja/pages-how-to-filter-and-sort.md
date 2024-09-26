---
title: "リスト内のアイテムのフィルタと並べ替え"
category: "ページ"
description: "Mendix Studio でリスト内の項目をフィルタリングおよびソートする方法を説明します。"
menu_order: 50
tags:
  - "スタジオ"
  - "ページ"
  - "リスト"
  - "どうやって?"
  - "フィルター"
  - "並べ替え"
---

## 1つの紹介

この方法では、Mendix Studio でリストビューまたはデータ グリッドの項目をフィルタリングおよびソートする方法を説明します。

**以下の方法を教えてくれます。**

* リスト内の項目のフィルタを設定します
* リスト内のアイテムをソート

以下のユースケースについて説明します。

安全規制の遵守を確認した企業を示す検査レポートの一覧が表示されたページを構築しています。 この検査に失敗した会社のみを表示したいです。 また、今日のみレポートを表示します。 また、項目は最新のものから始まる日付と時刻でソートする必要があります。

検査レポートの一覧がページに表示されます。 リストビューにリストがある場合は、次のようにページが表示されます。

{{% image_container width="600" %}}
![](attachments/pages-how-to-filter-and-sort/list-view-example.png)
{{% /image_container %}}

または、リストがデータグリッド内にある場合、ページを次のように見ることができます。

{{% image_container width="600" %}}
![](attachments/pages-how-to-filter-and-sort/page-example-data-grid.png)
{{% /image_container %}}

Domain model is configured the following way in this use-case:

{{% image_container width="250" %}}
![](attachments/pages-how-to-filter-and-sort/domain-model.png)
{{% /image_container %}}

## 2 つの前提条件

この方法を開始する前に、以下の必要条件を完了していることを確認してください:

* ページの用語や基本的な機能をどのように実行するかに慣れます。 詳細については、 [ページ](/studio/page-editor) を参照してください。
* データフィルタの条件に慣れてください。 詳細については、 [データフィルター](/studio/data-filters) を参照してください。
* ドメインモデルの用語に慣れ、基本的な機能を実行する方法を学びます。 詳細については、 [ドメインモデル](/studio/domain-models) を参照してください。

## 3フィルタリング情報

まず、リストにフィルタを追加する必要があります。  検査チェックに失敗した企業だけをお見せしたいと思います。 **Passed** 属性 (上記のドメインモデル画像を参照) は、検査レポートで *No* としてマークされている必要があります。

また、2020年2月に作成または変更されたレポートを表示したいと思います。 つまり、 **DateAndTime** 属性は2020年2月1日から2020年2月29日までの範囲に収まるはずです。

フィルタを設定するには、次の手順を実行します。

1. リスト ビューまたはデータ グリッドを選択し、プロパティを開きます。

2. **データ ソース** セクションで、 **フィルター** をクリックします。

    {{% image_container width="250" %}}![](attachments/pages-how-to-filter-and-sort/properties-filter.png){{% /image_container %}}

3. **フィルター** の追加ダイアログボックスで、以下を行ってフィルターの条件を追加します:

    1. ドロップダウンメニューから **Passed** 属性を選択します。

        {{% image_container width="550" %}}![](attachments/pages-how-to-filter-and-sort/add-filter-select-attribute.png){{% /image_container %}}

    2. 条件の最初の部分を選択すると、他の部分を選択して完了できます。 *false* を選択:

        {{% image_container width="550" %}}![](attachments/pages-how-to-filter-and-sort/add-filter-condition.png){{% /image_container %}}

    3. 今日の検査レポートをフィルタリングする フィルタに別の条件を追加する必要があります: **新しい条件の追加** をクリックし、ドロップダウン メニューで **DateAndTime** 属性を選択します。

    4. 条件の 2 番目の部分を追加: 日付は今日の日付である必要があります。 ドロップダウンメニューで *Today* を選択します:

        {{% image_container width="550" %}}![](attachments/pages-how-to-filter-and-sort/filter-date-and-time.png){{% /image_container %}}

    5. **追加** をクリックします。

よくできました！ You have created the filter that has two conditions and reads the following way: *Select records of InspectionReport where Passed is false and date and time is Today.* This means this filter will show you only the reports that fall under both conditions: which failed the inspection check and which were created or modified in the current day.

## 4つのソート項目

リスト内の項目を最新のものから始まる日付と時刻でソートするには、以下の手順に従ってください:

1. リスト ビューまたはデータ グリッドを選択し、そのプロパティを開きます。

2. **並べ替え順序** プロパティで、 **並べ替えルール** を追加をクリックします。

3. **並べ替えルール** ダイアログボックスで、 **DateAndTime** 属性を選択し、 **Order** を *Descending* に設定します。

    {{% image_container width="450" %}}![](attachments/pages-how-to-filter-and-sort/add-sorting-rule.png){{% /image_container %}}

4. **追加** をクリックします。

おめでとうございます フィルターと並べ替え順序をリストに追加しました。 アプリをプレビューしてページをテストできるようになりました。 ページをプレビューする方法の詳細については、 [プレビュー中 & アプリを公開する](/studio/publishing-app) を参照してください。