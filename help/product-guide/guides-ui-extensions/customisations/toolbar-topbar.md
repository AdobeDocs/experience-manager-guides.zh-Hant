---
title: 頂端列和工具列
description: 自訂標題列和工具列
source-git-commit: 5962414dfc065543b946cac1468a5f62013073cf
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---


# 自訂標題列和工具列

若要自訂 `topbar` 和 `toolbar`，我們會使用id： `topbar` 或 `toolbar`，並遵循相同的檢視、控制器結構。

以下是工具列自訂的簡單範例。 在此，我們已移除 `Insert Numbered List` 按鈕，並取代 `Insert Paragraph` 按鈕搭配我們自己的元件，並使用自訂的點按處理常式。

```js title = toolbar_customisation.js
const toolbarExtend = {
    id: "toolbar",
    view: {
        items: [
            {
                component: "div",
                target: {
                    key:"title",value: "Insert Numbered List",                    
                    viewState: VIEW_STATE.REPLACE
                }
            },
            {
                {
                    "component": "button",
                    "icon": "textParagraph",
                    "variant": "action",
                    "quiet": true,
                    "title": "Insert Paragraph",
                    "on-click": "INSERT_P"
                },

                target: {
                    key:"title",value: "Insert Paragraph",                    
                    viewState: VIEW_STATE.REPLACE
                }
            },
        ]
    },
    controller: {

        INSERT_P(){
            this.next("AUTHOR_INSERT_ELEMENT",  "p" )
        }
    }
}
```
