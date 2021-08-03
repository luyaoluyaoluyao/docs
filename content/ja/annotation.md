---
title: "注釈"
parent: "application-logic"
menu_order: 60
tags:
  - "studio pro"
  - "アノテーション:"
  - アノテーションフロー
aliases:
  - /refguide8/annotation-flow.html
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/annotation.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

アノテーションは、フローにコメントを配置するために使用できる要素です。

以下の例では、 **Show message** アクティビティを使用して、クライアントにポップアップメッセージが表示されている未払い注文についてエンドユーザーに警告します。 後で、ユーザーに送信される電子メールメッセージでこの警告を拡張したいです。 注釈をリマインダーとして使用し、現在のアクティビティの上に置くことができます。

![](attachments/anotation/anotation.png)

## 2つの一般的なプロパティ

### 2.1 図表番号

詳細については、 [共通プロパティ](microflow-element-common-properties) を参照してください。

## 注釈フロー3 {#annotation-flow}

注釈フローは、注釈をフローオブジェクトにリンクするために使用できる接続です。

例えば、これは注釈と **マイクロフローコール** アクティビティをリンクする注釈フローです。

![](attachments/anotation/anotation-flow.png)