---
title: 演算Widget
description: 在JUI Widget中轉譯的運作方式
role: User, Admin
exl-id: 381cc7b9-c957-40be-9db4-8347eefe2fa7
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# 演算Widget

我們可以使用其`id`來參照小工具

若要在應用程式中的任何位置轉譯Widget `widget_languages`，我們可以使用簡單語法：

```json
{
    "component": "widget",
    "id": "widget_languages"
}
```

Widget也可用來轉譯複雜專案，例如我想轉譯每個檔案的貢獻者清單。
在此，Widget可建構為：

```js title="fileContributorsWidget.js"
const widgetJSON =  {
    component: "div", 
    id: "file_contributors", 
    items: [ // adding components to the widget
        {
            component: "div",
            items: [
                {
                    component: "icon",
                    icon: "file"
                },
                {
                    component: "label",
                    label: "@fileName"
                }
            ]
        },
        {
            component: "list",
            data: "@contributors",
            itemConfig: {
                component: "label"
            }
        }
    ]
},
```

現在，為了呈現每個檔案的貢獻者清單，我們將清單編寫為：

```js title="fileContributorsList.js"
const listJSON = {
    component: "list"
    data: "@files"
    itemConfig: {
        component: "widget",
        id: "file_contributors"
    }
}
```

這裡`@files`是包含欄位的檔案物件清單

```typescript
- fileName: string
- contributors: Array<String>
```
