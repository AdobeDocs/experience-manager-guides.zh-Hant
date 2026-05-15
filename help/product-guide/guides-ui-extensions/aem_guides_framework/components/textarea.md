---
title: 文字區域
description: 文字區域
role: User, Admin
exl-id: 4c576acc-fa6a-4c41-9b92-443ba51dc8ee
TQID: https://experienceleague.adobe.com/ws7FgyxoutcYEts9wIJ3iQyjIwUfLrCgolSamc8ybDY
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 65
ht-degree: 3%

---

# 文字欄位和文字區域

若要以文字作為輸入，我們使用元件、文字欄位和文字區域。
JUI中的文字區域元件代表html `<textarea/>`。

```js title="textArea.js"
const textAreaJSON =  {
    "component": "textarea", //tells the component name
    "id": "input_name", // can be used to give a unique identifier to a component
    "data": "@name", // the variable storing the inputted text
    "on-keyup": {
        "name": "submitName",
        "eventArgs": {
            "keys": [
            "ENTER"
            ]
        }
    },
},
```

這裡，`on-keyup`是叫用控制器中命令的語法。
這會產生textArea，按ENTER鍵會呼叫事件`submitName`

演算後的文字區域看起來像這樣：

![文字區域](./imgs/text_area.png "文字區域")
