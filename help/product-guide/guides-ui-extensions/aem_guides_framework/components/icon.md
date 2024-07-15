---
title: 圖示
description: 圖示
role: User, Admin
exl-id: 5ba41c77-7329-49fc-bce5-02682261ea8e
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 6%

---

# 圖示

若要顯示圖示，請使用元件「圖示」。
JUI中的文字區域元件代表html `<icon/>`。

[Adobe頻譜圖示](https://spectrum.adobe.com/page/icons/)中可用的圖示與我們的應用程式相容。

```js title="icon.js"
const iconJSON =  {
    "component": "icon", //tells the component name
    "icon": "info", // name of the icon to be used
    "size": "S", // size of the icon
    "title": "Information" // tooltip corresponding to the icon.
},
```

圖示也可以新增到按鈕中。

演算後的圖示看起來像這樣：

![圖示](./imgs/info_icon.png "圖示")
