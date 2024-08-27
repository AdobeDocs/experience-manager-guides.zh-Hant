---
title: 文字區域
description: 文字區域
role: User, Admin
exl-id: 4c576acc-fa6a-4c41-9b92-443ba51dc8ee
source-git-commit: 08d379acc98dac425f1c84b0ac2226b0e34f6d8b
workflow-type: tm+mt
source-wordcount: '64'
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
