---
title: 標籤
description: 標籤
role: User, Admin
exl-id: aceefb08-3198-4c3a-90ec-ac1cdde28582
TQID: https://experienceleague.adobe.com/fYBih0o2nCF66z8OgoFJ0Xqt2oN8aY7ZomqfgljZIyA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 45
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
