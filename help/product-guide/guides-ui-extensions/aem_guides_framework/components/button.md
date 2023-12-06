---
sidebar_position: 1
source-git-commit: 5e0584f1bf0216b8b00f00b9fe46fa682c244e08
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 1%

---


# 按鈕

若要顯示按鈕，我們使用元件button。
JUI中的按鈕元件代表html `<button/>`.

```js title="buttonJSON.js"
const buttonJSON = {
  "component": "button",//tells the component name
  "label": "Yes, login",//tells the text for the button
  "variant": "cta",//tells the variants for the button which  provides default styles
  "on-click": "done",//tells what function to run after user clicks the button
};
```

這將會產生一個按鈕，其標籤為 `Yes, login`. 其他屬性包括但不限於variant、label、on-click。
> **_注意：_**  此 `on-<events>` 是叫用控制器中命令的語法。

轉譯的按鈕看起來像這樣：

![按鈕](imgs/yes_login_button.png "按鈕")
