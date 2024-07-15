---
title: 按鈕
description: 按鈕
role: User, Admin
exl-id: 40e3f254-f94e-4f43-8ff5-2e6e1eb1cb6f
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 5%

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
> **_注意：_** `on-<events>`是叫用控制器中命令的語法。

轉譯的按鈕看起來像這樣：

![按鈕](imgs/yes_login_button.png "按鈕")
