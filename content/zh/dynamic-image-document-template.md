---
title: "动态图像 (文档模板)"
parent: "文档模板"
tags:
  - "studio pro"
aliases:
  - /refguide/Dynamic+Image+(document+template).html
  - /refguide/dynamic-image-(document-template).html
---

## 1 导言

动态图像可以用于显示 System.Image。 如果图像不可用(例如：图像从未保存)，它将显示预设的默认图像。 它可以放置在数据视图或模板类别内。

{{% alert type="info" %}}

![](attachments/document-templates/918132.png) 一个表格单元内的动态图像，显示预设的默认图像。

{{% /报警 %}}

## 2 外观属性

### 2.1 默认图像

默认图像是文档中无法找到动态图像时出现的图像(当系统专业化实体时)。 mage 实体不包含实际图像。)

### 2.2 使用缩略图

您可以在这里选择是使用文档中的缩略图还是使用完整图像。

### 2.3 Width

宽度定义文档中图像的宽度。 这是以像素为单位设置的，使用文档模板中的 PPI ，这将被重新计算为实际打印大小。 可以设置宽度或高度；为了防止图像的扭曲，无法同时设置两者。

### 2.4 高度

高度定义文档中图像的高度 这是以像素为单位设置的，使用文档模板中的 PPI ，这将被重新计算为实际打印大小。 可以设置宽度或高度；为了防止图像的扭曲，无法同时设置两者。

## 3 个公共属性

{{% snippet file="refguide/name-property.md" %}}
