---
title: 演算Widget
description: 在JUI Widget中轉譯的運作方式
source-git-commit: f9a72e44fe1a3d90180ff728189a24ea9c7b1b1a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# 演算Widget

我們可以使用下列元件來參照小工具 `id`

轉譯Widget的方式 `widget_languages` 在應用程式的任意位置，我們可以使用簡單語法：

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

此處 `@files` 是包含欄位的檔案物件清單

```typescript
- fileName: string
- contributors: Array<String>
```
