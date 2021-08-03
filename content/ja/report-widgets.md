---
title: "ウィジェットのレポート"
parent: "ページ"
---

レポートを使用すると、データベースデータにレポートを作成できます。 レポートは、集計された情報を作成するために使用されます (例えば、顧客あたりの総売上高)。

データ グリッドとレポート グリッドの違いは、レポート グリッドに表示されているデータがデータベースに保存されていないことです。 レポートが作成されるたびに、データはデータベースから取得されます。 レポートウィジェットのデータは、 [Datasets](data-sets) によって提供される。

レポートは [ページ](page) に [レポート グリッド](report-grid) ウィジェットを使用するか、 [レポート チャート](report-chart) ウィジェットを使用してグラフィカルなフォームで表形式で表示できます。 If the [Data Set](data-sets) corresponding to the report contains parameters, these can be specified by the user via the [Report Parameter](report-parameter) and [Report Date Parameter](report-date-parameter) widgets. すべてのレポートパラメータは任意であるため、すべてのパラメータを指定する義務はありません。
