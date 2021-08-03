---
title: "Annotation"
parent: "microflows-and-nanoflows"
menu_order: 60
tags:
  - "studio pro"
  - "annotation"
  - annotation flow
aliases:
  - /refguide/annotation-flow.html
---

## 1 Introduction

An annotation is an element that can be used to put comments to a flow.

In the example below, you use a **Show message** activity to warn end-users about unpaid orders with a pop-up message in the client. Later you want to extend this warning with an e-mail message send to the user. You can use an annotation as a reminder and put it above the current activity.

![](attachments/anotation/anotation.png)

## 2 Common Properties

### 2.1 Caption

For details, see [Common Properties](microflow-element-common-properties).

## 3 Annotation Flow {#annotation-flow}

An annotation flow is a connection that can be used to link an annotation to a flow object(s).

For example, this is an annotation flow linking an annotation and a **Microflow call** activity:

![](attachments/anotation/anotation-flow.png)