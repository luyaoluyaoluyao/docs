---
title: "タブコンテナ"
parent: "container-widgets"
menu_order: 40
tags:
  - "studio pro"
  - "タブコンテナ"
  - "tab page"
  - "コンテナウィジェット"
  - "ウィジェット"
aliases:
  - /refguide8/tab-page.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/tab-container.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

タブコンテナは、タブに分類された情報を表示するために使用されます。 これは、表示しなければならない情報の量が画面上のスペースの量よりも大きい場合に非常に便利です。

![タブコンテナ](attachments/container-widgets/tab-container.png)

## 2つのプロパティ

タブコンテナプロパティの例を以下の画像に示します。

{{% image_container width="250" %}}![format@@0 タブ](attachments/container-widgets/tab-container-properties.png)
{{% /image_container %}}

format@@0 タブ コンテナプロパティは以下のセクションで構成されます。

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [公開範囲](#visibility)

### 2.1 共通セクション {#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション {#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 表示セクション {#visibility}

{{% snippet file="refguide8/visibility-section-link.md" %}}

## 3 Tab Page {#tab-page}

タブコンテナには、ウィジェットを配置するタブページが1つまたは複数あります。 たとえば、タブページには注文のグリッドを含めることができます。

### 3.1 format@@0 タブ

#### 3.1.1 Default Tab Page

**デフォルトのタブページ** では、ページが開かれたときに表示されるタブを定義します。 デフォルトのタブが設定されていない場合、最初のタブページが表示されます。

デフォルト: *False*

#### 3.1.2 表示時に更新 {#refresh}

**ショー時に更新する** は、タブページが表示されたときにタブページの内容を更新するかどうかを示します。 タブページの情報に影響がないことがわかっている場合は、このプロパティを *いいえ* に設定してください。

デフォルト: *True*

{{% alert type="info" %}}
このプロパティは、ネイティブのモバイルページではサポートされていません。
{{% /alert %}}

## 4 続きを読む

* [ページ](page)
* [コンテナウィジェット](container-widgets)
* [ページエディターで共通のプロパティ](common-widget-properties)
