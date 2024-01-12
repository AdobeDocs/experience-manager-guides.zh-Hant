---
title: 文字區域
description: 文字區域
role: User, Admin
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 3%

---

# 文字欄位和文字區域

若要以文字作為輸入，我們使用元件、文字欄位和文字區域。
JUI中的文字區域元件代表html `<textarea/>`.

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

此處， `on-keyup` 是叫用控制器中命令的語法。
這會產生textArea，按下ENTER即可呼叫事件 `submitName`

演算後的文字區域看起來像這樣：

![text-area](./imgs/text_area.png "文字區域")
