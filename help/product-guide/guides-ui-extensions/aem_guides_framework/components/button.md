---
title: 按鈕
description: 按鈕
role: User, Admin
exl-id: 40e3f254-f94e-4f43-8ff5-2e6e1eb1cb6f
TQID: https://experienceleague.adobe.com/pmhyi9TN4gFF0opdy2SsTEUr4l1uLZMwhIwmUPMJSA0
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 62
ht-degree: 4%

---

# 按鈕

若要顯示按鈕，我們使用元件button。
JUI中的按鈕元件代表html `<button/>`。

```js title="buttonJSON.js"
const buttonJSON = {
  "component": "button",//tells the component name
  "label": "Yes, login",//tells the text for the button
  "variant": "cta",//tells the variants for the button which  provides default styles
  "on-click": "done",//tells what function to run after user clicks the button
};
```

這將會產生標籤為`Yes, login`的按鈕。 其他屬性包括但不限於variant、label、on-click。
> **_NOTE:_** `on-<events>`是叫用控制器中命令的語法。

轉譯的按鈕看起來像這樣：

![按鈕](imgs/yes_login_button.png "按鈕")
