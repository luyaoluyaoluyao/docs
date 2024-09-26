---
title: "レポートパラメータ"
parent: "レポートウィジェット"
menu_order: 20
tags:
  - "studio pro"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/report-parameter.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

**レポート パラメータ** を使用すると、エンドユーザーは、 [レポート グリッド](data-sets) のデータを提供する [データ セット](report-grid) のパラメータを選択できます。 このパラメータは、同じレポートが異なるデータセットを表示できるように、さまざまな方法で結果をフィルタリングするために使用されます。

例えば、 レポートは顧客の注文データを表示し、レポートパラメータを使用して顧客のデータを表示することができます。

レポートパラメータは、データセットパラメータ名 (およびパラメータがオブジェクトの場合に表示される属性) と共に、角括弧と青色の間で表示される構造モードで表示されます。

![ストラクチャーモードでのレポートパラメータ](attachments/report-widgets/report-parameter.png)

{{% alert type="info" %}}
**レポート パラメータ** は、 **日付と時刻** 型のデータセットパラメータには使用できません。 日付と時刻のパラメータは、 [日付パラメータ](report-date-parameter) ウィジェットでフィルタリングする必要があります。

ページにレポート パラメータ ウィジェットを追加する場合は、 [レポート ボタン](report-button) ウィジェットも追加する必要があります。 これにより、エンドユーザーはパラメータを指定した後、レポートを再生成することができます。
{{% /alert %}}

## 2 レポートパラメータのプロパティ

レポートパラメータのプロパティの例を以下の画像に示します。

{{% image_container width="300" %}}![ストラクチャーモードでのレポートパラメータ](attachments/report-widgets/report-parameter-properties.png)
{{% /image_container %}}

レポート パラメータ プロパティは、次のセクションで構成されます。

* [一般的な](#common)
* [デザインプロパティ](#design-properties)
* [全般](#general)

### 2.1 共通セクション{#common}

{{% snippet file="refguide8/comon-section-link.md" %}}

### 2.2 デザインプロパティセクション{#design-properties}

{{% snippet file="refguide8/design-section-link.md" %}}

### 2.3 一般セクション{#general}

#### 2.3.1 パラメータ

**パラメータ** は、このウィジェットで制限されるデータセットパラメータに設定されます。 対応するデータセットは、ページのレポート ウィジェットのいずれかで使用する必要があります。

#### 2.3.2 表示属性

**表示される属性** は、データセットパラメータがオブジェクトの場合にのみ使用できます。 表示される属性は、ドロップダウン選択で対応するエンティティの属性を指定します。
