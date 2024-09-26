---
title: "イベントを終了"
parent: "イベント"
menu_order: 2
tags:
  - "studio pro"
  - "イベントを終了する"
  - "イベント"
---

{{% alert type="info" %}}
<img src="attachments/chinese-translation/china.png" style="display: inline-block; margin: 0" /> 簡体字中国語の翻訳については、 [<unk> <unk> <unk>](https://cdn.mendix.tencent-cloud.com/documentation/refguide8/end-event.pdf) をクリックしてください。
{{% /alert %}}

## 1つの紹介

end イベントはフローが停止する場所を定義します。

endイベントは、オブジェクト、列挙、リストなどの値を返すことができます。 詳細については、 [Return Value](#return-value) セクションを参照してください。

以下の例では、 *顧客* エンティティの *買い手* 変数は、終了イベントによって返されます。

![](attachments/events/end-event.png)

エンドイベントの数は、マイクロフローまたはナノレベルの結果の数によって決まります。 つまり、たとえば、 [decision](decision) が使用されている場合など、複数の end イベントが存在する可能性があります。

![](attachments/events/end-events.png)

## 2つのビヘイビアプロパティ

### 2.1 戻り値 {#return-value}

戻り値は、現在のフローと呼ばれるフローに返される値です。 複数の終了イベントがあり、それらが戻り値を持っている場合、すべて同じ型の値を返す必要があります。 例えば、endイベントの1つが *Entity*型のオブジェクトを返す場合、他のイベントは同じ型を返す必要があります。

{{% image_container width="300" %}}
![](attachments/events/return-value.png)
{{% /image_container %}}

何も返すか、リスト、列挙値、ブール値などを選択できます。

![](attachments/events/end-event-type.png)

戻り値は [式](expressions) として入力できます。

{{% alert type="info" %}}

別のマイクロフローからマイクロフローを呼び出す場合、 *を呼び出すことで、* を呼び出すことで返されるものを制御できないことに注意してください。 これは *と呼ばれる* マイクロフローによって制御されます。

{{% /alert %}}

## 3 続きを読む

* [イベントを開始](start-event)

* [マイクロフロー通話](microflow-call)
