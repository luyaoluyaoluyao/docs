---
title: "Sort Bar"
parent: "data-grid"
aliases:
  - /refguide7/Sort+Bar.html
---

The sort bar contains sort items. Each sort item specifies what attribute to sort on and in what direction (ascending or descending). First, the contents of the grid will be sorted on the first item. If two rows are the same with respect to this sort item, the second item will be used, and so on. For example, if you have sort items for name and age and two people have the same name they will be sorted on their age.

If you do not specify any sort items, the objects will appear in the order in which they were created.

{{% alert type="info" %}}
There are special cases for ordering behavior. For more details, see [Order By Behavior](ordering-behavior).
{{% /alert %}}
