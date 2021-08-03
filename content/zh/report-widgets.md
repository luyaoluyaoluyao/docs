---
title: "报告小部件"
parent: "页面"
---

通过报告，您可以通过数据库数据创建报告。 报告被用来创建总合信息（例如，每个客户的总销售额）。

数据网格与报告网格之间的差别是，报告网格中显示的数据不存储在数据库中。 每次创建报告时，从数据库中检索数据。 报告小部件的数据由 [数据集](data-sets) 提供。

A report can be presented on a [Page](page) in a tabular form using a [Report Grid](report-grid) widget or in a graphical form using a [Report Chart](report-chart) widget. 如果对应于报告的 [数据集](data-sets) 包含参数， 这些可以由用户通过 [报告参数](report-parameter) 和 [报告日期 参数](report-date-parameter) 小部件指定. 请注意，所有报告参数都是可选的，所以不必指定所有参数。
