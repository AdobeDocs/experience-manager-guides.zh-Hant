---
title: 簡單的自訂
description: 簡單自訂範例
role: User, Admin
exl-id: 7f19f0b0-2a1b-4a8b-b28c-3918a1bc9096
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# 簡單自訂範例

現在，讓我們來瞭解如何在AEM Guides應用程式中整合這些自訂專案。

假設我們想要在應用程式的現有檢視中新增此按鈕。
為此，我們需要3項基本功能：

1. 我們要新增元件的檢視JSON的`id`。
2. `target`，也就是我們想要新增元件的JSON位置。 已使用`key`和`value`定義`target`。 機碼 — 值組可以是任何用來定義元件的屬性，可有助於識別元件的唯一識別。
我們也可以使用索引來參照目標。
我們有3個viewStates： `APPEND`、`PREPEND`、`REPLACE`。
3. 新建立之元件的JSON和對應方法。

假設我們想要新增按鈕到稽核中使用的註釋工具箱，該按鈕會在AEM中開啟檔案。

```typescript
export default {
  id: 'annotation_toolbox', 
  view: {
    items: [
      {
        component: 'button',
        icon: 'linkOut',
        title: 'Open topic in Assets view',
        'on-click': 'openTopicInAEM',
        target: {
          key: 'value',
          value: 'addcomment',
          viewState: VIEW_STATE.APPEND

        },
      },
    ],
  },
  controller: {
    openTopicInAEM: function (args) {
        const topicIndex = tcx.model.getValue(tcx.model.KEYS.REVIEW_CURR_TOPIC)
        const {allTopics = {}} = tcx.model.getValue(tcx.model.KEYS.REVIEW_DATA) || {}
        tcx.appGet('util').openInAEM(allTopics[topicIndex])
    },
  },
}
```

在上述範例中，我們有：

1. 我們想要插入元件的JSON的`id`，即`annotation_toolbox`
2. 目標是`addcomment`按鈕。 我們使用viewState `append`在`addcomment`按鈕之後新增按鈕。
3. 我們定義控制器中按鈕的點按事件。

「annotation_toolbox」的JSON `.src/jsons/review_app/annotation_toolbox.json`

在自訂之前，註解工具箱看起來像這樣：

![註解工具箱](imgs/annotation_toolbox.png "註解工具箱")

自訂後，註解工具箱看起來像這樣：

![customized-annotation-toolbox](imgs/customised_annotation_toolbox.png "Customized註解工具箱")

## 新增CSS

為了保持一致性，我們提供已設定樣式的元件。 插入的JSON將套用其固有樣式
管理css的主要方式是透過擴充功能中的extraClass索引鍵。

```js
{    
    "view":{
        items:[
            {
                compoenent:"button",
                extraClass:"underline bg-red",
            }
        ]
    }
}
```

您可以將CSS檔案新增至clientlibs，以使用CSS類別放置自訂樣式。 在建置期間，我們也會為順風中的公用程式類別建立[順風](https://tailwindcss.com/docs/utility-first)輸出。 相同專案的設定可在擴充功能的`tailwind.config.js`的`./tailwind.config.js`找到
