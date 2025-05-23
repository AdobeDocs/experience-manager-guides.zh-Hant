---
title: 在左側面板中設定自訂面板
description: 瞭解如何在左側面板中設定自訂面板
exl-id: 6cfa64aa-46f3-4235-a4a7-f21e658f0a5a
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# 在左側面板中設定自訂面板 {#id224JI200Y6F}

執行以下步驟，在網頁編輯器的左側面板中新增自訂面板：

1. 建立&#x200B;*clientlib*&#x200B;資料夾，並將您的JavaScript和CSS檔案新增至此資料夾。
1. 透過將&#x200B;*apps.fmdita.xml\_editor.page\_overrides*&#x200B;的值指派給&#x200B;*clientlib*&#x200B;資料夾來更新categories屬性。

設定自訂面板的程式碼範例：

```JavaScript
tcx.ready(function () { //Ready will call the callback after editor code is set for events and global variable excess
 
 
    // APP_ADD_AUTHOR_LEFT_TAB event will add a new left tab in the left panel, user can show hide it using editor settings
    tcx.eventHandler.next(tcx.eventHandler.KEYS.APP_ADD_AUTHOR_LEFT_TAB, {
            id: 'my_panel',
            class: 'my-panel-tab',
            icon: 'file', //Any valid Adobe Spectrum icon name https://spectrum.adobe.com/page/icons/
            label: 'My Tab',
            prevTabID: 'repository_panel' //Existing tab ids are 'collection_panel', 'repository_panel', 'map_panel', 'outline_panel', 'conref_panel', 'glossary_panel', 'condition_panel', 'subject_scheme_panel', 'snippet_panel', 'template_panel', 'search_panel'
    })
 
    // APP_PANEL_DID_MOUNT event will be called after user has selected the panel and panel is rendered in the DOM
    tcx.eventHandler.subscribe({
        key: tcx.eventHandler.KEYS.APP_PANEL_DID_MOUNT,
        next: function(opts) {
            // TODO create panel ui inside $el
            let $el = opts.$el //$el is Tab panel content html node
            let id = opts.id //id is tab panel id (my_panel)
            console.log("mounted", opts)
        }
    })
 
  // APP_PANEL_WILL_UNMOUNT will be called before destorying the new left panel
  tcx.eventHandler.subscribe({
        key: tcx.eventHandler.KEYS.APP_PANEL_WILL_UNMOUNT,
        next: function(opts) {
            //TODO do some cleanup
            let id = opts.id //id is tab panel id (my_panel)
            console.log("unmounted", opts)
        }
    })
 
});
```

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
