---
title: 標籤
description: 標籤
role: User, Admin
exl-id: aceefb08-3198-4c3a-90ec-ac1cdde28582
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 6%

---

# 標籤

若要顯示任何文字或字串，我們會使用元件label。
JUI中的標籤元件代表html `<label/>`。

以下是新增靜態標籤的範例

```js title="staticLabel.js"
const staticLabelJSON =  {
    "component": "label", //tells the component name
    "label": "This is an example label", // the string to be displayed
}
```

JSON下方會顯示動態字串：

```js title="dynamicLabel.js"
const labelJSON =  {
    "component": "label", //tells the component name
    "label": "@name", // the variable storing the text to be displayed
},
```

轉譯的標籤看起來像這樣：

![標籤](./imgs/label.png "標籤")
