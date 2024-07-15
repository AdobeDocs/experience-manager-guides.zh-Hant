---
title: 清單
description: 清單
role: User, Admin
exl-id: 333b5e24-efba-4a51-8f68-83b5d1d7daec
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 5%

---

# 清單

若要顯示清單，我們使用元件清單。

```js title="list.js"
const listJSON =  {
    "component": "list", //tells the component name
    "data": "@languages", // an array of list items
},
```

在這裡，語言是一組簡單的字串。 `languages = ["English", "Hindi", "French"]`
如果我們想要呈現物件清單，可以使用專案設定來指定結構。

```js title="list.js"
const listJSON =  {
    "component": "list", //tells the component name
    "data": "@projects", // an array of list items
    "itemConfig": { // used to define the structure of the list items.
    "component": "widget",
    "id": "checkbox_label"
    }
},
```

itemConfig通常是`widget`。 若要深入瞭解Widget，請前往[Widget](../Widgets/basic-widget.md)

轉譯後的清單看起來像這樣：

![清單](./imgs/list.png "清單")
